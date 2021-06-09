---
title: Installare Visual Studio Build Tools in un contenitore
titleSuffix: ''
description: Informazioni su come installare Visual Studio Build Tools in un contenitore di Windows per supportare flussi di lavoro di integrazione continua e recapito continuo (CI/CD).
ms.date: 03/25/2020
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: dcf28f818760320b215cbff0d3a2eb5ad6d9f623
ms.sourcegitcommit: 55b99dbce29d19e493feae9b8d2fdac73718e4de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873068"
---
# <a name="install-build-tools-into-a-container"></a>Installare Build Tools in un contenitore

È possibile installare Visual Studio Build Tools in un contenitore di Windows per supportare flussi di lavoro di integrazione continua e recapito continuo (CI/CD). Questo articolo illustra le modifiche di configurazione di Docker necessarie, nonché i [carichi di lavoro e i componenti](workload-component-id-vs-build-tools.md) che è possibile installare in un contenitore.

I [contenitori](https://www.docker.com/what-container) sono un ottimo modo per inserire un sistema di compilazione coerente in un pacchetto utilizzabile non solo in un ambiente server CI/CD, ma anche per gli ambienti di sviluppo. Ad esempio, è possibile montare il codice sorgente in un contenitore per la compilazione in un ambiente personalizzato, pur continuando a usare Visual Studio o altri strumenti per scrivere il codice. Se il flusso di lavoro CI/CD usa la stessa immagine del contenitore, è possibile essere certi che la compilazione del codice avvenga in modo coerente. È possibile usare i contenitori anche per la coerenza del runtime, un'esigenza comune per i microservizi che usano più contenitori con un sistema di orchestrazione, ma ciò esula dagli scopi di questo articolo.

Se Visual Studio Build Tools non include ciò che serve per la compilazione del codice sorgente, le stesse procedure sono valide anche per altri prodotti Visual Studio. Si noti, tuttavia, che i contenitori di Windows non supportano un'interfaccia utente interattiva pertanto tutti i comandi devono essere automatizzati.

## <a name="before-you-begin"></a>Prima di iniziare

Di seguito si presuppone una certa conoscenza di [Docker](https://www.docker.com/what-docker). Se non si ha già familiarità con l'esecuzione di Docker in Windows, vedere le informazioni su [come installare e configurare il motore Docker in Windows](/virtualization/windowscontainers/manage-docker/configure-docker-daemon).

L'immagine di base riportata di seguito è un esempio e potrebbe non funzionare nel sistema specifico. Vedere [Compatibilità delle versioni del contenitore Windows](/virtualization/windowscontainers/deploy-containers/version-compatibility) per determinare quale immagine di base è consigliabile usare per l'ambiente specifico.

## <a name="create-and-build-the-dockerfile"></a>Creare e compilare il Dockerfile

Salvare il Dockerfile di esempio seguente in un nuovo file su disco. Se il file è denominato semplicemente "Dockerfile", viene riconosciuto per impostazione predefinita.

> [!WARNING]
> Questo Dockerfile di esempio esclude solo le versioni precedenti di Windows SDK che non possono essere installate in contenitori. Con le versioni precedenti il comando di compilazione ha esito negativo.

1. Aprire un prompt dei comandi.

1. Creare una nuova directory (operazione consigliata):

   ```shell
   mkdir C:\BuildTools
   ```

1. Passare alla nuova directory:

   ```shell
   cd C:\BuildTools
   ```

1. Salvare il contenuto seguente in C:\BuildTools\Dockerfile.
 
   ::: moniker range="vs-2017"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.2.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
   RUN start /wait C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --add Microsoft.VisualStudio.Workload.AzureBuildTools `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Define the entry point for the Docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > Per un elenco dei carichi di lavoro e dei componenti, vedere la [directory Visual Studio Build Tools dei componenti.](workload-component-id-vs-build-tools.md)
   >

   > [!WARNING]
   > Se si basa l'immagine direttamente su microsoft/windowsservercore o mcr.microsoft.com/windows/servercore (vedere [Microsoft syndicates container catalog](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/) (Microsoft pubblica il catalogo dei contenitori)), .NET Framework potrebbe non essere installato correttamente e non viene segnalato alcun errore di installazione. Il codice gestito potrebbe non essere eseguito dopo il completamento dell'installazione. Basare invece l'immagine su [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) o versione successiva. Si noti anche che le immagini contrassegnate con la versione 4.7.2 o versioni successive potrebbero usare PowerShell come `SHELL` predefinita, impedendo l'esecuzione delle istruzioni `RUN` e `ENTRYPOINT`.
   >
   > Non è possibile installare Visual Studio 2017 versione 15.8 o versioni precedenti (qualsiasi prodotto) in mcr.microsoft.com/windows/servercore:1809 o versioni successive. Non viene visualizzato un errore.
   >
   > Vedere [Compatibilità delle versioni dei contenitori di Windows](/virtualization/windowscontainers/deploy-containers/version-compatibility) per scoprire quali versioni del sistema operativo contenitore sono supportate in quali versioni del sistema operativo host, e [Problemi noti dei contenitori](build-tools-container-issues.md) per i problemi noti.
   
   ::: moniker-end

   ::: moniker range="vs-2019"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.8.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/16/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --add Microsoft.VisualStudio.Workload.AzureBuildTools `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Define the entry point for the docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > Per un elenco dei carichi di lavoro e dei componenti, vedere la [directory Visual Studio Build Tools dei componenti.](workload-component-id-vs-build-tools.md)
   >

   > [!WARNING]
   > Se si basa l'immagine direttamente su microsoft/windowsservercore, .NET Framework potrebbe non essere installato correttamente e non viene segnalato nessun errore di installazione. Il codice gestito potrebbe non essere eseguito dopo il completamento dell'installazione. Basare invece l'immagine su [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) o versioni successive. Si noti anche che le immagini contrassegnate con la versione 4.8 o versioni successive potrebbero usare PowerShell come `SHELL` predefinita, impedendo l'esecuzione delle istruzioni `RUN` e `ENTRYPOINT`.
   >
   > Vedere [Compatibilità delle versioni dei contenitori di Windows](/virtualization/windowscontainers/deploy-containers/version-compatibility) per scoprire quali versioni del sistema operativo contenitore sono supportate in quali versioni del sistema operativo host, e [Problemi noti dei contenitori](build-tools-container-issues.md) per i problemi noti.

   ::: moniker-end
   
   > [!NOTE]
   > Il codice `3010` di errore viene usato per indicare l'esito positivo di un riavvio necessario. Per altre informazioni,MsiExec.exe messaggi di [errore.](/windows/win32/msi/error-codes)

1. Eseguire il comando seguente in tale directory.

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Questo comando compila il Dockerfile nella directory corrente con 2 GB di memoria. L'impostazione predefinita di 1 GB non è sufficiente quando sono installati determinati carichi di lavoro. Tuttavia il completamento della compilazione con solo 1 GB di memoria potrebbe riuscire, a seconda dei requisiti di compilazione.

   L'immagine finale viene contrassegnata con "buildtools2017:latest" in modo da poterla eseguire facilmente in un contenitore come "buildtools2017", dato che il tag "latest" è il valore predefinito se non si specifica alcun tag. Se si vuole usare una versione specifica di Visual Studio Build Tools 2017 in uno [scenario più avanzato](advanced-build-tools-container.md), è possibile contrassegnare il contenitore con un numero di build di Visual Studio specifico, oltre a usare il tag "latest", in modo che i contenitori possano usare una versione specifica in modo coerente.

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   Questo comando compila il Dockerfile nella directory corrente con 2 GB di memoria. L'impostazione predefinita di 1 GB non è sufficiente quando sono installati determinati carichi di lavoro. Tuttavia il completamento della compilazione con solo 1 GB di memoria potrebbe riuscire, a seconda dei requisiti di compilazione.

   L'immagine finale viene contrassegnata con "buildtools2019:latest" in modo da poterla eseguire facilmente in un contenitore come "buildtools2019", dato che il tag "latest" è il valore predefinito se non si specifica alcun tag. Se si vuole usare una versione specifica di Visual Studio Build Tools 2019 in uno [scenario più avanzato](advanced-build-tools-container.md), è possibile contrassegnare il contenitore con un numero di build di Visual Studio specifico e usare il tag "latest", in modo che i contenitori possano usare una versione specifica in modo coerente.

   ::: moniker-end

## <a name="using-the-built-image"></a>Uso dell'immagine compilata

Dopo avere creato un'immagine, è possibile eseguirla in un contenitore per eseguire compilazioni sia automatiche che interattive. L'esempio usa il prompt dei comandi per gli sviluppatori, in modo che la variabile PATH e altre variabili di ambiente siano già configurate.

1. Aprire un prompt dei comandi.

1. Eseguire il contenitore per avviare un ambiente di PowerShell con tutte le variabili di ambiente per gli sviluppatori impostate:

   ::: moniker range="vs-2017"

   ```shell
   docker run -it buildtools2017
   ```

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker run -it buildtools2019
   ```

   ::: moniker-end

Per usare questa immagine per il flusso di lavoro CI/CD è possibile pubblicarla nel proprio [Registro Azure Container](https://azure.microsoft.com/services/container-registry) o in un altro [registro Docker](https://docs.docker.com/registry/deploying) interno, in modo che i server possano semplicemente eseguirne il pull.

   > [!NOTE]
   > Se l'avvio del contenitore Docker non riesce, è probabile che si sia verificato un Visual Studio di installazione. È possibile aggiornare dockerfile per rimuovere il passaggio che chiama il Visual Studio batch. In questo modo è possibile avviare il contenitore Docker e leggere i log degli errori di installazione.
   >
   > Nel file Dockerfile rimuovere i `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` parametri e dal comando `&&` `ENTRYPOINT` . Il comando dovrebbe ora essere `ENTRYPOINT ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]` . Ricompilare quindi dockerfile ed eseguire il `run` comando per accedere ai file del contenitore. Per individuare i log degli errori di installazione, passare alla `$env:TEMP` directory e individuare il `dd_setup_<timestamp>_errors.log` file.
   >
   > Dopo aver identificato e risolto il problema di installazione, è possibile aggiungere nuovamente i parametri e al comando e `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` `&&` `ENTRYPOINT` ricompilare il Dockerfile.
   >
   > Per altre informazioni, vedere [Problemi noti dei contenitori](build-tools-container-issues.md).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Esempio avanzato per i contenitori](advanced-build-tools-container.md)
* [Problemi noti dei contenitori](build-tools-container-issues.md)
* [ID dei carichi di lavoro e dei componenti di Visual Studio Build Tools](workload-component-id-vs-build-tools.md)
