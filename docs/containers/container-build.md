---
title: Panoramica di compilazione e debug degli strumenti contenitore di Visual Studio
author: ghogen
description: Panoramica del processo di compilazione e debug degli strumenti contenitore
ms.author: ghogen
ms.date: 11/20/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 6b96f23bc7bcd7e6d970025b23f89f572d07daf1
ms.sourcegitcommit: e825d1223579b44ee2deb62baf4de0153f99242a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2019
ms.locfileid: "74473994"
---
# <a name="build-and-debug-containerized-apps-using-visual-studio-or-the-command-line"></a>Compilare ed eseguire il debug di app in contenitori con Visual Studio o la riga di comando

Che si stia compilando dall'IDE di Visual Studio o configurando una compilazione da riga di comando, è necessario sapere in che modo le compilazioni di Visual Studio usano Dockerfile per compilare i progetti.  Per motivi di prestazioni, Visual Studio segue un processo speciale per le app in contenitori. Conoscere il modo in cui Visual Studio compila i progetti è particolarmente importante quando si Personalizza il processo di compilazione modificando Dockerfile.

Quando Visual Studio compila un progetto che non usa contenitori Docker, richiama MSBuild nel computer locale e genera i file di output in una cartella (in genere `bin`) nella cartella della soluzione locale. Per un progetto in contenitori, tuttavia, il processo di compilazione prende in considerazione le istruzioni di Dockerfile per la creazione dell'app in contenitori. Il Dockerfile usato da Visual Studio è suddiviso in più fasi. Questo processo si basa sulla funzionalità di *compilazione multifase* di Docker.

## <a name="multistage-build"></a>Compilazione multifase

La funzionalità di compilazione multifase consente di rendere più efficiente il processo di creazione di contenitori, rendendo i contenitori più piccoli, consentendo loro di contenere solo i bit necessari per l'app in fase di esecuzione. La compilazione multifase viene usata per i progetti .NET Core e non per i progetti .NET Framework.

La compilazione multifase consente la creazione di immagini del contenitore in fasi che producono immagini intermedie. Si consideri ad esempio un tipico Dockerfile generato da Visual Studio: la prima fase è `base`:

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Le righe in Dockerfile iniziano con l'immagine di nano server da Microsoft Container Registry (mcr.microsoft.com) e creano un'immagine intermedia `base` che espone le porte 80 e 443 e imposta la directory di lavoro su `/app`.

La fase successiva è `build`, che viene visualizzata come segue:

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

È possibile osservare che la fase `build` inizia da un'immagine originale diversa dal registro di sistema (`sdk` anziché `aspnet`), anziché continuare dalla base.  L'immagine `sdk` dispone di tutti gli strumenti di compilazione e per questo motivo è molto più grande dell'immagine ASPNET, che contiene solo i componenti Runtime. Il motivo per l'uso di un'immagine separata diventa chiaro quando si esamina il resto del Dockerfile:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

La fase finale inizia di nuovo da `base`e include il `COPY --from=publish` per copiare l'output pubblicato nell'immagine finale. Questo processo rende possibile che l'immagine finale sia molto più piccola, perché non è necessario includere tutti gli strumenti di compilazione presenti nell'immagine `sdk`.

## <a name="faster-builds-for-the-debug-configuration"></a>Compilazioni più veloci per la configurazione di debug

Visual Studio offre diverse ottimizzazioni che consentono di migliorare le prestazioni del processo di compilazione per i progetti in contenitori. Il processo di compilazione per le app in contenitori non è così semplice come semplicemente seguendo i passaggi descritti in Dockerfile. La compilazione in un contenitore è molto più lenta rispetto alla compilazione nel computer locale.  Quindi, quando si compila la configurazione di **debug** , Visual Studio compila effettivamente i progetti nel computer locale e quindi condivide la cartella di output nel contenitore usando il montaggio del volume. Una compilazione con questa ottimizzazione abilitata è denominata compilazione in modalità *veloce* .

In modalità **rapida** , Visual Studio chiama `docker build` con un argomento che indica a Docker di compilare solo la fase di `base`.  Visual Studio gestisce il resto del processo senza considerare il contenuto di Dockerfile. Quindi, quando si modificano i Dockerfile, ad esempio per personalizzare l'ambiente del contenitore o installare dipendenze aggiuntive, è necessario inserire le modifiche nella prima fase.  Eventuali operazioni personalizzate inserite nelle fasi `build`, `publish`o `final` di Dockerfile non verranno eseguite.

Questa ottimizzazione delle prestazioni si verifica solo quando si compila la configurazione di **debug** . Nella configurazione della **versione** , la compilazione viene eseguita nel contenitore come specificato in Dockerfile.

Se si desidera disabilitare l'ottimizzazione delle prestazioni e compilare come specificato da Dockerfile, impostare la proprietà **ContainerDevelopmentMode** su **Regular** nel file di progetto come indicato di seguito:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Per ripristinare l'ottimizzazione delle prestazioni, rimuovere la proprietà dal file di progetto.

## <a name="building-from-the-command-line"></a>Compilazione dalla riga di comando

Per eseguire la compilazione dalla riga di comando, è possibile usare `docker build` o `MSBuild`.

### <a name="docker-build"></a>compilazione Docker

Per compilare una soluzione in contenitori dalla riga di comando, in genere è possibile usare il comando `docker build <context>` per ogni progetto nella soluzione. Specificare l'argomento del *contesto di compilazione* . Il *contesto di compilazione* per un Dockerfile è la cartella nel computer locale utilizzata come cartella di lavoro per generare l'immagine. Ad esempio, si tratta della cartella da cui vengono copiati i file quando si esegue la copia nel contenitore.  Nei progetti .NET Core utilizzare la cartella che contiene il file di soluzione (con estensione sln).  Espresso come percorso relativo, questo argomento è in genere ".." per un Dockerfile in una cartella di progetto e il file della soluzione nella cartella padre.  Per .NET Framework progetti, il contesto di compilazione è la cartella del progetto, non la cartella della soluzione.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Dockerfile creati da Visual Studio per i progetti .NET Framework (e per i progetti .NET Core creati con le versioni di Visual Studio precedenti a Visual Studio 2017 Update 4) non sono Dockerfile a più fasi.  I passaggi in questi Dockerfile non compilano il codice.  Al contrario, quando Visual Studio compila un .NET Framework Dockerfile, compila innanzitutto il progetto tramite MSBuild.  Quando ha esito positivo, Visual Studio compila il Dockerfile, che copia semplicemente l'output di compilazione da MSBuild nell'immagine Docker risultante.  Poiché i passaggi per compilare il codice non sono inclusi in Dockerfile, non è possibile compilare .NET Framework Dockerfile usando `docker build` dalla riga di comando. Per compilare questi progetti, è necessario utilizzare MSBuild.

Per compilare un'immagine per un singolo progetto di contenitore Docker, è possibile usare MSBuild con l'opzione di comando `/t:ContainerBuild`. Ad esempio:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Verrà visualizzato un output simile a quello visualizzato nella finestra **output** quando si compila la soluzione dall'IDE di Visual Studio. Usare sempre `/p:Configuration=Release`, poiché nei casi in cui Visual Studio usa l'ottimizzazione della compilazione multifase, i risultati quando si compila la configurazione di **debug** potrebbero non essere quelli previsti.

Se si utilizza un progetto di Docker Compose, utilizzare il comando per compilare immagini:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>Riscaldamento progetto

Si tratta di una sequenza di passaggi che si verificano quando il profilo Docker è selezionato per un progetto (ovvero quando viene caricato un progetto o viene aggiunto il supporto Docker) per migliorare le prestazioni dell'esecuzione successiva (**F5** o **CTRL**+**F5**). Questa operazione può essere configurata in **strumenti** > **Opzioni** > **strumenti contenitore**. Di seguito sono riportate le attività eseguite in background:

- Verificare che Docker desktop sia installato e in esecuzione.
- Assicurarsi che Docker desktop sia impostato sullo stesso sistema operativo del progetto.
- Estrarre le immagini nella prima fase di Dockerfile (la fase `base` nella maggior parte dei Dockerfile).  
- Compilare il Dockerfile e avviare il contenitore.

Il riscaldamento si verificherà solo in modalità **rapida** , quindi il contenitore in esecuzione avrà il volume della cartella dell'app montata e le eventuali modifiche apportate all'app non invalideranno il contenitore. Ciò migliora le prestazioni di debug in modo significativo e riduce il tempo di attesa per attività a esecuzione prolungata, ad esempio il pull di immagini di grandi dimensioni.

## <a name="volume-mapping"></a>Mapping del volume

Per il funzionamento del debug nei contenitori, Visual Studio usa il mapping del volume per eseguire il mapping delle cartelle debugger e NuGet dal computer host. Ecco i volumi montati nel contenitore:

|||
|-|-|
| **Debugger remoto** | Contiene i bit necessari per eseguire il debugger nel contenitore a seconda del tipo di progetto. Questa operazione è illustrata più di |Dettagli nella sezione [debug](#debugging) .
| **Cartella app** | Contiene la cartella del progetto in cui si trova Dockerfile.|
| **Cartella di origine** | Contiene il contesto di compilazione che viene passato ai comandi di Docker.|
| **Cartelle pacchetti NuGet** | Contiene i pacchetti NuGet e le cartelle di fallback letti dal file *obj\{Project}. csproj. NuGet. g. props* nel progetto. |

Per le app Web ASP.NET Core, potrebbero essere presenti due cartelle aggiuntive per il certificato SSL e i segreti utente, che vengono illustrati più dettagliatamente nella sezione successiva.

## <a name="ssl-enabled-aspnet-core-apps"></a>App ASP.NET Core abilitate per SSL

Gli strumenti contenitore in Visual Studio supportano il debug di un'app ASP.NET Core abilitata per SSL con un certificato di sviluppo, nello stesso modo in cui si prevede che funzioni senza contenitori. A tale proposito, Visual Studio aggiunge un paio di passaggi per esportare il certificato e renderlo disponibile per il contenitore. Ecco il flusso:

1. Verificare che il certificato di sviluppo locale sia presente e attendibile nel computer host tramite lo strumento `dev-certs`.
2. Esportare il certificato in%APPDATA%\ASP.NET\Https con una password sicura archiviata nell'archivio dei segreti utente per questa specifica app.
3. Montaggio del volume nelle directory seguenti:

   - *%APPDATA%\Microsoft\UserSecrets*
   - *%APPDATA%\ASP.NET\Https*

ASP.NET Core Cerca un certificato che corrisponda al nome dell'assembly nella cartella *https* , motivo per cui viene eseguito il mapping al contenitore in tale percorso. Il percorso e la password del certificato possono essere definiti in alternativa usando variabili di ambiente (ovvero `ASPNETCORE_Kestrel__Certificates__Default__Path` e `ASPNETCORE_Kestrel__Certificates__Default__Password`) o nel file JSON dei segreti utente, ad esempio:

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "c:\\app\\mycert.pfx",
        "Password": "strongpassword"
      }
    }
  }
}
```

Per altre informazioni sull'uso di SSL con ASP.NET Core app nei contenitori, vedere [hosting di ASP.NET Core immagini con Docker su HTTPS](https://docs.microsoft.com/aspnet/core/security/docker-https).

## <a name="debugging"></a>Debug

 Quando si avvia il debug (**F5**), viene riutilizzato un contenitore avviato in precedenza, se possibile. Se non si vuole riutilizzare il contenitore precedente, è possibile usare i comandi **ricompila** o **Pulisci** in Visual Studio per forzare l'uso di un contenitore aggiornato in Visual Studio.

Il processo di esecuzione del debugger dipende dal tipo di progetto e dal sistema operativo del contenitore:

|||
|-|-|
| **App .NET Core (contenitori Linux)**| Visual Studio Scarica `vsdbg` e ne esegue il mapping al contenitore, quindi viene chiamato con il programma e gli argomenti (ovvero `dotnet webapp.dll`), quindi il debugger si connette al processo. |
| **App .NET Core (contenitori di Windows)**| Visual Studio USA `onecoremsvsmon` e ne esegue il mapping al contenitore, lo esegue come punto di ingresso e quindi Visual Studio si connette a esso e viene collegato al programma. Questa operazione è simile a quella in cui normalmente si configura il debug remoto in un altro computer o macchina virtuale.|
| **App .NET Framework** | Visual Studio USA `msvsmon` e ne esegue il mapping al contenitore, lo esegue come parte del punto di ingresso in cui Visual Studio è in grado di connettersi e si connette al programma.|

Per informazioni su `vsdbg.exe`, vedere [il video relativo al debug Offroad di .NET Core in Linux e OSX da Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio).

## <a name="container-entry-point"></a>Punto di ingresso del contenitore

Visual Studio usa un punto di ingresso del contenitore personalizzato a seconda del tipo di progetto e del sistema operativo del contenitore. di seguito sono riportate le diverse combinazioni:

|||
|-|-|
| **Contenitori Linux** | Il punto di ingresso è `tail -f /dev/null`, ovvero un'attesa infinita per l'esecuzione del contenitore. Quando l'app viene avviata tramite il debugger, è il debugger responsabile dell'esecuzione dell'app, ovvero `dotnet webapp.dll`. Se viene avviato senza eseguire il debug, lo strumento esegue una `docker exec -i {containerId} dotnet webapp.dll` per eseguire l'app.|
| **Contenitori di Windows**| Il punto di ingresso è simile `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus` che esegue il debugger, quindi è in ascolto delle connessioni. Lo stesso vale per il debugger che esegue l'app e un comando `docker exec` quando viene avviato senza debug. Per .NET Framework app Web, il punto di ingresso è leggermente diverso da quello in cui `ServiceMonitor` viene aggiunto al comando.|
  
> [!NOTE]
> Il punto di ingresso del contenitore può essere modificato solo in progetti Docker-compose, non in progetti a contenitore singolo.

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come personalizzare ulteriormente le compilazioni impostando ulteriori proprietà di MSBuild nei file di progetto. Vedere [Proprietà MSBuild per progetti contenitore](container-msbuild-properties.md).

## <a name="see-also"></a>Vedere anche

[MSBuild](../msbuild/msbuild.md)
[Dockerfile nei contenitori Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
[Linux in Windows](/virtualization/windowscontainers/deploy-containers/linux-containers)
