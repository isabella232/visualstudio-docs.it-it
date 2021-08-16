---
title: Visual Studio Panoramica della compilazione e del debug di Strumenti contenitore
author: ghogen
description: Panoramica del processo di compilazione e debug di Container Tools
ms.author: ghogen
ms.date: 03/15/2021
ms.technology: vs-container-tools
ms.topic: conceptual
ms.openlocfilehash: 7e7b80aa144dfb1cbef88c27a3fe09478c91c268ca6b8f9dea6390148b3a2e0d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347935"
---
# <a name="how-visual-studio-builds-containerized-apps"></a>Modalità di compilazione delle app aggiunte a contenitori in Visual Studio

Sia che si usi l'IDE Visual Studio o la configurazione di una compilazione da riga di comando, è necessario sapere come Visual Studio usa Dockerfile per compilare i progetti.  Per motivi di prestazioni, Visual Studio un processo speciale per le app in contenitori. La comprensione Visual Studio compila i progetti è particolarmente importante quando si personalizza il processo di compilazione modificando dockerfile.

Quando Visual Studio compila un progetto che non usa contenitori Docker, richiama MSBuild nel computer locale e genera i file di output in una cartella (in genere ) nella cartella della soluzione `bin` locale. Per un progetto in contenitori, tuttavia, il processo di compilazione tiene conto delle istruzioni del Dockerfile per la compilazione dell'app in contenitori. Il Dockerfile che Visual Studio viene utilizzato è suddiviso in più fasi. Questo processo si basa sulla funzionalità di compilazione *multistage di* Docker.

## <a name="multistage-build"></a>Compilazione multistage

La funzionalità di compilazione multi-fase consente di rendere più efficiente il processo di creazione di contenitori e di ridurre le dimensioni dei contenitori consentendo loro di contenere solo i bit che l'app richiede in fase di esecuzione. La compilazione multistage viene usata per i progetti .NET Core, non .NET Framework progetti.

La compilazione multi-fase consente di creare immagini del contenitore in fasi che producono immagini intermedie. Si consideri ad esempio un tipico Dockerfile generato da Visual Studio: la prima fase `base` è:

```
FROM mcr.microsoft.com/dotnet/aspnet:3.1-buster-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Le righe nel Dockerfile iniziano con l'immagine Debian da Microsoft Container Registry (mcr.microsoft.com) e creano un'immagine intermedia che espone le porte `base` 80 e 443 e imposta la directory di lavoro su `/app` .

La fase successiva è `build` , che viene visualizzata come segue:

```
FROM mcr.microsoft.com/dotnet/sdk:3.1-buster-slim AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app/build
```

È possibile vedere che la fase inizia da un'immagine originale diversa dal Registro di sistema ( anziché ) anziché `build` `sdk` continuare dalla `aspnet` base.  L'immagine include tutti gli strumenti di compilazione e per questo motivo è molto più grande `sdk` dell'immagine aspnet, che contiene solo componenti di runtime. Il motivo dell'uso di un'immagine separata diventa chiaro quando si osserva il resto del Dockerfile:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

La fase finale inizia di nuovo da e include per `base` `COPY --from=publish` copiare l'output pubblicato nell'immagine finale. Questo processo rende possibile che l'immagine finale sia molto più piccola, poiché non è necessario includere tutti gli strumenti di compilazione presenti `sdk` nell'immagine.

## <a name="building-from-the-command-line"></a>Compilazione dalla riga di comando

Se si vuole compilare all'esterno Visual Studio, è possibile usare `docker build` o `MSBuild` per compilare dalla riga di comando.

### <a name="docker-build"></a>docker build

Per compilare una soluzione in contenitori dalla riga di comando, è in genere possibile usare il comando `docker build <context>` per ogni progetto nella soluzione. Specificare *l'argomento del contesto di* compilazione. Il *contesto di* compilazione per un Dockerfile è la cartella nel computer locale usata come cartella di lavoro per generare l'immagine. Ad esempio, è la cartella da cui si copiano i file quando si esegue la copia nel contenitore.  Nei progetti .NET Core usare la cartella che contiene il file di soluzione (con estensione sln).  Espresso come percorso relativo, questo argomento è in genere ".." per un Dockerfile in una cartella di progetto e il file di soluzione nella cartella padre.  Per .NET Framework, il contesto di compilazione è la cartella del progetto, non la cartella della soluzione.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

I dockerfile creati da Visual Studio per i progetti .NET Framework (e per i progetti .NET Core creati con versioni di Visual Studio precedenti Visual Studio 2017 Update 4) non sono dockerfile multistage.  I passaggi in questi Dockerfile non compilano il codice.  Al contrario, Visual Studio compila un .NET Framework Dockerfile, compila prima di tutto il progetto usando MSBuild.  Al termine, Visual Studio il Dockerfile, che copia semplicemente l'output di compilazione MSBuild'immagine Docker risultante.  Poiché i passaggi per compilare il codice non sono inclusi nel Dockerfile, non è possibile compilare .NET Framework Dockerfile usando `docker build` dalla riga di comando. È consigliabile usare MSBuild per compilare questi progetti.

Per compilare un'immagine per un singolo progetto di contenitore Docker, è possibile usare MSBuild con `/t:ContainerBuild` l'opzione di comando . Esempio:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

L'output sarà simile a quello visualizzato nella finestra **Output** quando si compila la soluzione dall'IDE Visual Studio. Usare sempre , poiché nei casi in cui Visual Studio l'ottimizzazione della compilazione multistage, i risultati durante la compilazione della configurazione di debug potrebbero `/p:Configuration=Release` non essere come previsto.  Vedere [Debug](#debugging)di .

Se si usa un progetto Docker Compose, usare questo comando per compilare le immagini:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>Project riscaldamento

*Project riscaldamento* si riferisce a una serie di passaggi che si verificano quando si seleziona il profilo Docker per un progetto (ovvero quando viene caricato un progetto o viene aggiunto il supporto Docker) per migliorare le prestazioni delle esecuzioni successive (**F5** o + **CTRL F5**). Questa opzione è configurabile in **Strumenti**  >  **Opzioni**  >  **Strumenti contenitore**. Ecco le attività eseguite in background:

- Verificare che Docker Desktop sia installato e in esecuzione.
- Assicurarsi che Docker Desktop sia impostato sullo stesso sistema operativo del progetto.
- Eseguire il pull delle immagini nella prima fase del Dockerfile `base` (la fase nella maggior parte dei Dockerfile).  
- Compilare dockerfile e avviare il contenitore.

Il riscaldamento verrà eseguito solo in **modalità rapida,** quindi il contenitore in esecuzione avrà la cartella dell'app montata sul volume. Ciò significa che qualsiasi modifica apportata all'app non invalida il contenitore. Ciò consente di migliorare significativamente le prestazioni di debug e di ridurre il tempo di attesa per attività a esecuzione lunga, ad esempio il pull di immagini di grandi dimensioni.

## <a name="volume-mapping"></a>Mapping dei volumi

Per il funzionamento del debug nei contenitori, Visual Studio il mapping dei volumi per eseguire il mapping del debugger e NuGet cartelle dal computer host. Il mapping dei volumi è descritto nella documentazione di Docker [qui](https://docs.docker.com/storage/volumes/). Ecco i volumi montati nel contenitore:

|Volume|Descrizione|
|-|-|
| **Debugger remoto** | Contiene i bit necessari per eseguire il debugger nel contenitore a seconda del tipo di progetto. Questa operazione è illustrata in modo più dettagliato nella [sezione](#debugging) Debug.|
| **Cartella dell'app** | Contiene la cartella del progetto in cui si trova dockerfile.|
| **Cartella di origine** | Contiene il contesto di compilazione passato ai comandi Docker.|
| **NuGet cartelle dei pacchetti** | Contiene i NuGet e le cartelle di fallback letti dal file *obj \{ project}.csproj.nuget.g.props* nel progetto. |

Per ASP.NET app Web di base, potrebbero essere presenti due cartelle aggiuntive per il certificato SSL e i segreti utente, come illustrato più dettagliatamente nella sezione successiva.

## <a name="ssl-enabled-aspnet-core-apps"></a>App ASP.NET Core SSL

Gli strumenti contenitore in Visual Studio supportano il debug di un'app core ASP.NET abilitata per SSL con un certificato di sviluppo, come ci si aspetterebbe che funzioni senza contenitori. A tale fine, Visual Studio altri passaggi per esportare il certificato e renderlo disponibile nel contenitore. Ecco il flusso che Visual Studio gestisce automaticamente durante il debug nel contenitore:

1. Garantisce che il certificato di sviluppo locale sia presente e attendibile nel computer host tramite lo `dev-certs` strumento .
2. Esporta il certificato in %APPDATA%\ASP.NET\Https con una password sicura archiviata nell'archivio segreti utente per questa particolare app.
3. Il volume monta le directory seguenti:

   - *%APPDATA%\Microsoft\UserSecrets*
   - *%APPDATA%\ASP.NET\Https*

ASP.NET Core un certificato corrispondente al nome dell'assembly nella cartella *Https* ed è per questo motivo che viene eseguito il mapping al contenitore in tale percorso. Il percorso del certificato e la password possono essere definiti in alternativa usando variabili di ambiente (ovvero e ) o nel file JSON dei segreti `ASPNETCORE_Kestrel__Certificates__Default__Path` `ASPNETCORE_Kestrel__Certificates__Default__Password` utente, ad esempio:

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

Se la configurazione supporta compilazioni sia in contenitori che non in contenitori, è consigliabile usare le variabili di ambiente, perché i percorsi sono specifici dell'ambiente contenitore.

Per altre informazioni sull'uso di SSL ASP.NET Core app nei contenitori, vedere Hosting di ASP.NET Core [immagini con Docker su HTTPS.](/aspnet/core/security/docker-https)

## <a name="debugging"></a>Debug

Quando si compila nella **configurazione di** debug, sono disponibili diverse ottimizzazioni Visual Studio che consentono di migliorare le prestazioni del processo di compilazione per i progetti in contenitori. Il processo di compilazione per le app in contenitori non è semplice come seguire semplicemente i passaggi descritti in Dockerfile. La compilazione in un contenitore è molto più lenta rispetto alla compilazione nel computer locale.  Pertanto, quando si  compila nella configurazione di debug, Visual Studio compila effettivamente i progetti nel computer locale e quindi condivide la cartella di output nel contenitore usando il montaggio del volume. Una compilazione con questa ottimizzazione abilitata è detta *compilazione in* modalità rapida.

In **modalità** veloce, Visual Studio con un argomento che indica `docker build` a Docker di compilare solo la `base` fase.  Visual Studio gestisce il resto del processo indipendentemente dal contenuto del Dockerfile. Pertanto, quando si modifica il Dockerfile, ad esempio per personalizzare l'ambiente del contenitore o installare dipendenze aggiuntive, è consigliabile inserire le modifiche nella prima fase.  Tutti i passaggi personalizzati inseriti nelle fasi , o del Dockerfile `build` `publish` non verranno `final` eseguiti.

Questa ottimizzazione delle prestazioni si verifica solo quando si esegue la compilazione nella **configurazione di** debug. Nella configurazione **release** la compilazione viene eseguita nel contenitore come specificato in Dockerfile.

Se si vuole disabilitare l'ottimizzazione delle prestazioni e la compilazione come specificato da Dockerfile, impostare la proprietà **ContainerDevelopmentMode** su **Regular** nel file di progetto come indicato di seguito:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Per ripristinare l'ottimizzazione delle prestazioni, rimuovere la proprietà dal file di progetto.

 Quando si avvia il debug (**F5**), viene riutilizzato un contenitore avviato in precedenza, se possibile. Se non si vuole riutilizzare il contenitore  precedente, è possibile usare i comandi Ricompila o Pulisci in Visual Studio per forzare Visual Studio usare un nuovo contenitore. 

Il processo di esecuzione del debugger dipende dal tipo di sistema operativo del progetto e del contenitore:

|Scenario|Processo del debugger|
|-|-|
| **App .NET Core (contenitori Linux)**| Visual Studio scaricarlo e mapparlo al contenitore, quindi viene chiamato con il programma e gli argomenti (ovvero ), quindi il debugger si `vsdbg` `dotnet webapp.dll` connette al processo. |
| **App .NET Core (Windows contenitori)**| Visual Studio usa ed esegue il mapping al contenitore, lo esegue come punto di ingresso e quindi Visual Studio si connette al contenitore e si collega `onecoremsvsmon` al programma. Questo è simile al modo in cui normalmente si configura il debug remoto in un altro computer o macchina virtuale.|
| **.NET Framework app** | Visual Studio usa ed esegue il mapping al contenitore, lo esegue come parte del punto di ingresso in cui Visual Studio può connettersi al contenitore e si collega `msvsmon` al programma.|

Per informazioni su `vsdbg.exe` , vedere Debug offroad di .NET Core in Linux e [OSX da Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio).

## <a name="container-entry-point"></a>Punto di ingresso del contenitore

Visual Studio usa un punto di ingresso del contenitore personalizzato a seconda del tipo di progetto e del sistema operativo del contenitore, ecco le diverse combinazioni:

|Tipo di contenitore|Punto di ingresso|
|-|-|
| **Contenitori Linux** | Il punto di ingresso è `tail -f /dev/null` , ovvero un'attesa infinita per mantenere in esecuzione il contenitore. Quando l'app viene avviata tramite il debugger, è il debugger responsabile dell'esecuzione dell'app , ovvero `dotnet webapp.dll` . Se avviati senza debug, gli strumenti eseguono un per `docker exec -i {containerId} dotnet webapp.dll` eseguire l'app.|
| **Contenitori Windows**| Il punto di ingresso è simile a `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus` quello che esegue il debugger, quindi è in ascolto delle connessioni. Lo stesso vale per il fatto che il debugger esegue l'app e un `docker exec` comando quando viene avviato senza debug. Per .NET Framework web, il punto di ingresso è leggermente diverso in cui `ServiceMonitor` viene aggiunto al comando.|

Il punto di ingresso del contenitore può essere modificato solo nei progetti docker-compose, non nei progetti a contenitore singolo.

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come personalizzare ulteriormente le compilazioni impostando proprietà aggiuntive MSBuild nei file di progetto. Vedere [MSBuild proprietà per i progetti contenitore.](container-msbuild-properties.md)

## <a name="see-also"></a>Vedi anche

[MSBuild](../msbuild/msbuild.md) 
 [Dockerfile in Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile) 
 [Contenitori Linux in Windows](/virtualization/windowscontainers/deploy-containers/linux-containers)
