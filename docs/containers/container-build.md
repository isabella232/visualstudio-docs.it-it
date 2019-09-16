---
title: Panoramica della compilazione degli strumenti contenitore di Visual Studio
author: ghogen
description: Panoramica del processo di compilazione degli strumenti contenitore
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 9f2da112bfeebe4e0bce976736eee5696d888105
ms.sourcegitcommit: c7b9ab1bc19d74b635c19b1937e92c590dafd736
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2019
ms.locfileid: "70312182"
---
# <a name="building-containerized-apps-using-visual-studio-or-the-command-line"></a>Creazione di app in contenitori con Visual Studio o la riga di comando

Che si stia compilando dall'IDE di Visual Studio o configurando una compilazione da riga di comando, è necessario sapere in che modo le compilazioni di Visual Studio usano Dockerfile per compilare i progetti.  Per motivi di prestazioni, Visual Studio segue un processo speciale per le app in contenitori. Conoscere il modo in cui Visual Studio compila i progetti è particolarmente importante quando si Personalizza il processo di compilazione modificando Dockerfile.

Quando Visual Studio compila un progetto che non usa contenitori Docker, richiama MSBuild nel computer locale e genera i file di output in una cartella, in genere `bin`, nella cartella della soluzione locale. Per un progetto in contenitori, tuttavia, il processo di compilazione prende in considerazione le istruzioni di Dockerfile per la creazione dell'app in contenitori. Il Dockerfile usato da Visual Studio è suddiviso in più fasi. Questo processo si basa sulla funzionalità di *compilazione multifase* di Docker.

## <a name="multistage-build"></a>Compilazione multifase

La funzionalità di compilazione multifase consente di rendere più efficiente il processo di creazione di contenitori, rendendo i contenitori più piccoli, consentendo loro di contenere solo i bit necessari per l'app in fase di esecuzione. La compilazione multifase viene usata per i progetti .NET Core e non per i progetti .NET Framework.

La compilazione multifase consente la creazione di immagini del contenitore in fasi che producono immagini intermedie. Ad esempio, si consideri un tipico Dockerfile generato da Visual Studio: la prima `base`fase è:

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Le righe in Dockerfile iniziano con l'immagine nanoserver di Microsoft container Registry (MCR.Microsoft.com) e creano un'immagine `base` intermedia che espone le porte 80 e 443 e imposta la directory di lavoro su. `/app`

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

È possibile osservare che la `build` fase inizia da un'immagine originale diversa dal registro di sistema`sdk` (anziché `aspnet`), anziché continuare dalla base.  L' `sdk` immagine include tutti gli strumenti di compilazione e per questo motivo è molto più grande dell'immagine ASPNET, che contiene solo i componenti Runtime. Il motivo per l'uso di un'immagine separata diventa chiaro quando si esamina il resto del Dockerfile:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

La fase finale inizia di nuovo `base`da e include la `COPY --from=publish` per copiare l'output pubblicato nell'immagine finale. Questo processo rende possibile che l'immagine finale sia molto più piccola, perché non è necessario includere tutti gli strumenti di compilazione presenti nell' `sdk` immagine.

## <a name="faster-builds-for-the-debug-configuration"></a>Compilazioni più veloci per la configurazione di debug

Visual Studio offre diverse ottimizzazioni che consentono di migliorare le prestazioni del processo di compilazione per i progetti in contenitori. Quando si avvia il debug (F5), un'immagine compilata in precedenza viene riutilizzata, se possibile. Se non si vuole riutilizzare il contenitore precedente, è possibile usare i comandi **ricompila** o **Pulisci** in Visual Studio per forzare l'uso di un contenitore aggiornato in Visual Studio.

Per migliorare le prestazioni, inoltre, il processo di compilazione per le app in contenitori non è così semplice come semplicemente seguendo i passaggi descritti in Dockerfile. La compilazione in un contenitore è molto più lenta rispetto alla compilazione nel computer locale.  Quindi, quando si compila la configurazione di **debug** , Visual Studio compila effettivamente i progetti nel computer locale e quindi condivide la cartella di output nel contenitore usando il montaggio del volume. Una compilazione con questa ottimizzazione abilitata è denominata compilazione in modalità *veloce* .

In modalità **rapida** , Visual Studio chiama `docker build` con un argomento che indica a Docker di compilare solo `base` la fase.  Visual Studio gestisce il resto del processo senza considerare il contenuto di Dockerfile. Quindi, quando si modificano i Dockerfile, ad esempio per personalizzare l'ambiente del contenitore o installare dipendenze aggiuntive, è necessario inserire le modifiche nella prima fase.  Eventuali passaggi personalizzati inseriti nelle fasi `build`, `publish`o `final` di Dockerfile non verranno eseguiti.

Questa ottimizzazione delle prestazioni si verifica solo quando si compila la configurazione di **debug** . Nella configurazione della **versione** , la compilazione viene eseguita nel contenitore come specificato in Dockerfile.

Se si desidera disabilitare l'ottimizzazione delle prestazioni e compilare come specificato da Dockerfile, impostare la proprietà **ContainerDevelopmentMode** su **Regular** nel file di progetto come indicato di seguito:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Per ripristinare l'ottimizzazione delle prestazioni, rimuovere la proprietà dal file di progetto.

## <a name="building-from-the-command-line"></a>Compilazione dalla riga di comando

È possibile utilizzare `docker build` o `MSBuild` per compilare dalla riga di comando.

### <a name="docker-build"></a>compilazione Docker

Per compilare una soluzione in contenitori dalla riga di comando, in genere è possibile usare il `docker build <context>` comando per ogni progetto nella soluzione. Specificare l'argomento del *contesto di compilazione* . Il *contesto di compilazione* per un Dockerfile è la cartella nel computer locale utilizzata come cartella di lavoro per generare l'immagine. Ad esempio, si tratta della cartella da cui vengono copiati i file quando si esegue la copia nel contenitore.  Nei progetti .NET Core utilizzare la cartella che contiene il file di soluzione (con estensione sln).  Espresso come percorso relativo, questo argomento è in genere ".." per un Dockerfile in una cartella di progetto e il file della soluzione nella cartella padre.  Per .NET Framework progetti, il contesto di compilazione è la cartella del progetto, non la cartella della soluzione.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Dockerfile creati da Visual Studio per i progetti .NET Framework (e per i progetti .NET Core creati con le versioni di Visual Studio precedenti a Visual Studio 2017 Update 4) non sono Dockerfile a più fasi.  I passaggi in questi Dockerfile non compilano il codice.  Al contrario, quando Visual Studio compila un .NET Framework Dockerfile, compila innanzitutto il progetto tramite MSBuild.  Quando ha esito positivo, Visual Studio compila il Dockerfile, che copia semplicemente l'output di compilazione da MSBuild nell'immagine Docker risultante.  Poiché i passaggi per compilare il codice non sono inclusi in Dockerfile, non è possibile compilare .NET Framework dockerfile `docker build` usando dalla riga di comando. Per compilare questi progetti, è necessario utilizzare MSBuild.

Per compilare un'immagine per un singolo progetto di contenitore Docker, è possibile usare `/t:ContainerBuild` MSBuild con l'opzione di comando. Ad esempio:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Verrà visualizzato un output simile a quello visualizzato nella finestra **output** quando si compila la soluzione dall'IDE di Visual Studio. Usare `/p:Configuration=Release`sempre, poiché nei casi in cui Visual Studio usa l'ottimizzazione della compilazione multifase, i risultati quando si compila la configurazione di **debug** potrebbero non essere quelli previsti.

Se si utilizza un progetto di Docker Compose, utilizzare il comando per compilare immagini:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come personalizzare ulteriormente le compilazioni impostando ulteriori proprietà di MSBuild nei file di progetto. Vedere [Proprietà MSBuild per progetti contenitore](container-msbuild-properties.md).

## <a name="see-also"></a>Vedere anche

[MSBuild](../msbuild/msbuild.md)
[Dockerfile nei](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
[contenitori Windows Linux in Windows](/virtualization/windowscontainers/deploy-containers/linux-containers)
