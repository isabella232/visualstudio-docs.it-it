---
title: Panoramica della compilazione e del debug di Visual Studio Container Tools
author: ghogen
description: Panoramica del processo di compilazione e debug degli strumenti contenitore
ms.author: ghogen
ms.date: 11/20/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: d91dd01879ac3bb62b981109463f6762046382ef
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027267"
---
# <a name="how-visual-studio-builds-containerized-apps"></a>Modalità di compilazione delle app aggiunte a contenitori in Visual Studio

Se si sta compilando dall'IDE di Visual Studio o l'impostazione di una compilazione da riga di comando, è necessario sapere come Visual Studio utilizza il Dockerfile per compilare i progetti.  Per motivi di prestazioni, Visual Studio segue un processo speciale per le app containerizzate. Comprendere come Visual Studio compila i progetti è particolarmente importante quando si personalizza il processo di compilazione modificando il Dockerfile.Understanding how Visual Studio builds your projects is especially important when you customize your build process by modifying the Dockerfile.

Quando Visual Studio compila un progetto che non utilizza contenitori Docker, richiama MSBuild nel computer locale `bin`e genera i file di output in una cartella (in genere ) nella cartella della soluzione locale. Per un progetto con contenitore, tuttavia, il processo di compilazione tiene conto delle istruzioni del Dockerfile per la compilazione dell'app con contenitore. Il Dockerfile utilizzato da Visual Studio è suddiviso in più fasi. Questo processo si basa sulla funzionalità di *compilazione multifase* di Docker.

## <a name="multistage-build"></a>Compilazione a più fasi

La funzionalità di compilazione a più fasi consente di rendere più efficiente il processo di creazione dei contenitori e di rimpicciolire i contenitori consentendo loro di contenere solo i bit necessari per l'app in fase di esecuzione. La compilazione a più fasi viene utilizzata per i progetti .NET Core, non per i progetti .NET Framework.

La build a più fasi consente di creare immagini contenitore in fasi che producono immagini intermedie. Si consideri ad esempio un tipico Dockerfile generato `base`da Visual Studio: la prima fase è:

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Le righe nel file Docker iniziano con l'immagine Debian dal Registro contenitori Microsoft (mcr.microsoft.com) e creano un'immagine `base` intermedia che espone le porte 80 e 443 e impostano la directory di lavoro su . `/app`

La fase `build`successiva è , che appare come segue:

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

Si può vedere `build` che lo stage inizia da`sdk` un'immagine originale diversa dal Registro di sistema ( anziché `aspnet`), anziché continuare dalla base.  L'immagine `sdk` ha tutti gli strumenti di compilazione, e per questo motivo è molto più grande dell'immagine aspnet, che contiene solo i componenti di runtime. Il motivo per l'utilizzo di un'immagine separata diventa chiaro quando si guarda il resto del Dockerfile:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

La fase finale `base`ricomincia da `COPY --from=publish` , e include l'oggetto per copiare l'output pubblicato nell'immagine finale. Questo processo rende possibile per l'immagine finale di essere molto più piccolo, dal momento che `sdk` non è necessario includere tutti gli strumenti di compilazione che erano nell'immagine.

## <a name="building-from-the-command-line"></a>Compilazione dalla riga di comando

Se si desidera eseguire la compilazione `docker build` all'esterno di Visual Studio, è possibile utilizzare o `MSBuild` per compilare dalla riga di comando.

### <a name="docker-build"></a>docker build

Per compilare una soluzione in contenitori dalla riga `docker build <context>` di comando, è in genere possibile usare il comando per ogni progetto nella soluzione. Specificare l'argomento del contesto di *compilazione.* Il contesto di *compilazione* per un Dockerfile è la cartella nel computer locale che viene utilizzata come cartella di lavoro per generare l'immagine. Ad esempio, è la cartella da cui si copiano i file quando si copiano nel contenitore.  Nei progetti .NET Core usare la cartella che contiene il file di soluzione (con estensione sln).  Espresso come percorso relativo, questo argomento è in genere ".." per un Dockerfile in una cartella di progetto e il file di soluzione nella cartella padre.  Per i progetti .NET Framework, il contesto di compilazione è la cartella del progetto, non la cartella della soluzione.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Dockerfiles creati da progetti di Visual Studio per .NET Framework (e per i progetti .NET Core creati con versioni di Visual Studio precedenti a Visual Studio 2017 Update 4) non sono Dockerfile a più fasi.  I passaggi in questi Dockerfiles non compilano il codice.  Al contrario, quando Visual Studio compila un Dockerfile di .NET Framework, compila innanzitutto il progetto utilizzando MSBuild.  Quando l'operazione riesce, Visual Studio compila quindi il Dockerfile, che copia semplicemente l'output di compilazione da MSBuild nell'immagine Docker risultante.  Poiché i passaggi per compilare il codice non sono inclusi nel Dockerfile, `docker build` non è possibile compilare I file Docker file di .NET Framework usando dalla riga di comando. È consigliabile usare MSBuild per compilare questi progetti.

Per compilare un'immagine per il progetto di `/t:ContainerBuild` contenitore docker singolo è possibile utilizzare MSBuild con l'opzione di comando. Ad esempio:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Verrà visualizzato un output simile a quello visualizzato nella finestra **di output** quando si compila la soluzione dall'IDE di Visual Studio.You'll see output similar to what you see in the Output window when you build your solution from the Visual Studio IDE. Utilizzare `/p:Configuration=Release`sempre , poiché nei casi in cui Visual Studio utilizza l'ottimizzazione della compilazione a più fasi, i risultati durante la compilazione della configurazione **di Debug** potrebbero non essere quelli previsti. Vedere [Debug](#debugging).

Se si utilizza un progetto Docker Compose, utilizzare questo comando per compilare immagini:If you are using a Docker Compose project, use this command to build images:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>Riscaldamento del progetto

*Il riscaldamento* del progetto si riferisce a una serie di passaggi che si verificano quando il profilo Docker viene selezionato per un progetto (ovvero quando viene caricato un progetto o viene aggiunto il supporto Docker) per migliorare le prestazioni delle esecuzioni successive (**F5** o **Ctrl**+**F5**). Questa operazione è configurabile in**Strumenti contenitore****opzioni** >  **strumenti** > . Di seguito sono riportate le attività eseguite in background:

- Verificare che Docker Desktop sia installato e in esecuzione.
- Assicurarsi che Docker Desktop sia impostato sullo stesso sistema operativo del progetto.
- Estrarre le immagini nella prima fase del `base` Dockerfile (lo stage nella maggior parte Dockerfiles).  
- Compilare il Dockerfile e avviare il contenitore.

Il riscaldamento avverrà solo in modalità **veloce,** quindi il contenitore in esecuzione avrà la cartella dell'app montata sul volume. Ciò significa che qualsiasi modifica all'app non invaliderà il contenitore. In questo modo si migliorano in modo significativo le prestazioni di debug e si riduce il tempo di attesa per le attività a esecuzione prolungata, ad esempio il pull di immagini di grandi dimensioni.

## <a name="volume-mapping"></a>Mapping del volume

Affinché il debug funzioni nei contenitori, Visual Studio usa il mapping del volume per eseguire il mapping delle cartelle debugger e NuGet dal computer host. Il mapping del volume è descritto nella documentazione della finestra mobile [qui](https://docs.docker.com/storage/volumes/). Di seguito sono riportati i volumi montati nel contenitore:

|||
|-|-|
| **Debugger remoto** | Contiene i bit necessari per eseguire il debugger nel contenitore a seconda del tipo di progetto. Questo è spiegato in più |dettagli nella sezione [Debug.](#debugging)
| **Cartella dell'app** | Contiene la cartella del progetto in cui si trova il file Docker.|
| **Cartella di origine** | Contiene il contesto di compilazione passato ai comandi Docker.|
| **Cartelle dei pacchetti NuGetNuGet packages folders** | Contiene i pacchetti NuGet e le cartelle di fallback che vengono letti dal file *obj\{project,csproj.nuget.g.props* nel progetto. |

Per ASP.NET app Web di base, potrebbero essere presenti due cartelle aggiuntive per il certificato SSL e i segreti utente, come illustrato in modo più dettagliato nella sezione successiva.

## <a name="ssl-enabled-aspnet-core-apps"></a>App ASP.NET Core abilitate per SSL

Gli strumenti contenitore in Visual Studio supportano il debug di un'app di base abilitata ASP.NET per SSL con un certificato di sviluppo, nello stesso modo in cui ci si aspetterebbe che funzioni senza contenitori. A tale fine, Visual Studio aggiunge un paio di passaggi per esportare il certificato e renderlo disponibile per il contenitore. Ecco il flusso che Visual Studio gestisce automaticamente durante il debug nel contenitore:Here is the flow that Visual Studio handles for you when debugging in the container:

1. Garantisce che il certificato di sviluppo locale sia `dev-certs` presente e attendibile nel computer host tramite lo strumento.
2. Esporta il certificato in %APPDATA% , ASP.NET , Https con una password sicura archiviata nell'archivio dei segreti utente per questa particolare app.
3. Il volume consente di montare le seguenti directory:

   - *%APPDATA% Microsoft UserSecrets*
   - *%APPDATA% ASP.NET Https*

ASP.NET Core di base cerca un certificato che corrisponda al nome dell'assembly nella cartella *Https,* motivo per cui è mappato al contenitore in tale percorso. Il percorso del certificato e la password possono essere `ASPNETCORE_Kestrel__Certificates__Default__Path` `ASPNETCORE_Kestrel__Certificates__Default__Password`definiti in alternativa utilizzando variabili di ambiente (ovvero e ) o nel file json dei segreti utente, ad esempio:

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

Se la configurazione supporta compilazioni con contenitori e non containerizzate, è consigliabile usare le variabili di ambiente, perché i percorsi sono specifici dell'ambiente del contenitore.

Per altre informazioni sull'uso di SSL con le app ASP.NET Core nei contenitori, vedere [Hosting di immagini ASP.NET Core con Docker su HTTPS).](/aspnet/core/security/docker-https)

## <a name="debugging"></a>Debug

Quando si compila nella configurazione di **debug,** esistono diverse ottimizzazioni che Visual Studio esegue questa funzionalità con le prestazioni del processo di compilazione per i progetti con contenitore. Il processo di compilazione per le app containerizzate non è così semplice come semplicemente seguendo i passaggi descritti nel dockerfile. La compilazione in un contenitore è molto più lenta rispetto alla creazione sulla macchina locale.  Pertanto, quando si compila nella configurazione **di Debug,** Visual Studio compila effettivamente i progetti nel computer locale e quindi condivide la cartella di output al contenitore utilizzando il montaggio del volume. Una compilazione con questa ottimizzazione abilitata viene chiamata compilazione in modalità *veloce.*

In modalità **rapida,** Visual Studio chiama `docker build` con un `base` argomento che indica a Docker di compilare solo lo stage.  Visual Studio gestisce il resto del processo senza considerare il contenuto del Dockerfile. Pertanto, quando si modifica il Dockerfile, ad esempio per personalizzare l'ambiente del contenitore o installare dipendenze aggiuntive, è necessario inserire le modifiche nella prima fase.  Eventuali passaggi personalizzati inseriti nelle `build`fasi `publish`, `final` , o del Dockerfile non verranno eseguiti.

Questa ottimizzazione delle prestazioni si verifica solo quando si compila nella configurazione **di Debug.This** performance optimization is only when you build in the Debug configuration. Nella configurazione **Release,** la compilazione viene eseguita nel contenitore come specificato nel Dockerfile.

Se si desidera disabilitare l'ottimizzazione delle prestazioni e compilare come specificato da Dockerfile, impostare la proprietà **ContainerDevelopmentMode** su **Regular** nel file di progetto come segue:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Per ripristinare l'ottimizzazione delle prestazioni, rimuovere la proprietà dal file di progetto.

 Quando si avvia il debug (**F5**), un contenitore avviato in precedenza viene riutilizzato, se possibile. Se non si vuole riutilizzare il contenitore precedente, è possibile usare i comandi **Ricostruisci** o **Pulisci** in Visual Studio per forzare Visual Studio a usare un nuovo contenitore.

Il processo di esecuzione del debugger dipende dal tipo di progetto e dal sistema operativo del contenitore:

|||
|-|-|
| **App .NET Core (contenitori Linux)**| Visual Studio `vsdbg` scarica e ne esegue il mapping al contenitore, quindi `dotnet webapp.dll`viene chiamato con il programma e gli argomenti (ovvero , ) e quindi il debugger si connette al processo. |
| **App .NET Core (contenitori di Windows)**| Visual Studio `onecoremsvsmon` usa e ne esegue il mapping al contenitore, lo esegue come punto di ingresso, quindi Visual Studio si connette a esso e si connette al programma. È simile a come si imposta normalmente il debug remoto in un altro computer o macchina virtuale.|
| **App .NET Framework** | Visual Studio `msvsmon` usa e ne esegue il mapping al contenitore, lo esegue come parte del punto di ingresso in cui Visual Studio può connettersi a esso e si connette al programma.|

Per informazioni `vsdbg.exe`su , vedere [Debug Offroad di .NET Core in Linux e OSX da Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio).

## <a name="container-entry-point"></a>Punto di ingresso contenitore

Visual Studio usa un punto di ingresso del contenitore personalizzato a seconda del tipo di progetto e del sistema operativo del contenitore, ecco le diverse combinazioni:Visual Studio uses a custom container entry point depending on the project type and the container operating system, here are the different combinations:

|||
|-|-|
| **Contenitori Linux** | Il punto `tail -f /dev/null`di ingresso è , ovvero un'attesa infinita per mantenere in esecuzione il contenitore. Quando l'app viene avviata tramite il debugger, è il debugger `dotnet webapp.dll`responsabile dell'esecuzione dell'app, ovvero ). Se avviato senza eseguire il `docker exec -i {containerId} dotnet webapp.dll` debug, gli strumenti vengono eseguiti per eseguire l'app.|
| **Contenitori windows**| Il punto di `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus` ingresso è simile a quello che esegue il debugger, pertanto è in ascolto di connessioni. Lo stesso vale per il debugger `docker exec` che il debugger esegue l'app e un comando quando viene avviato senza eseguire il debug. Per le app Web di .NET Framework, il punto di ingresso è leggermente diverso dove `ServiceMonitor` viene aggiunto al comando.|

Il punto di ingresso del contenitore può essere modificato solo nei progetti docker-compose, non nei progetti a contenitore singolo.

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come personalizzare ulteriormente le compilazioni impostando proprietà MSBuild aggiuntive nei file di progetto. Vedere [Proprietà MSBuild per](container-msbuild-properties.md)i progetti contenitore .

## <a name="see-also"></a>Vedere anche

[MSBuild](../msbuild/msbuild.md)
[Dockerfile di](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
MSBuild su[contenitori](/virtualization/windowscontainers/deploy-containers/linux-containers) Windows Linux in Windows
