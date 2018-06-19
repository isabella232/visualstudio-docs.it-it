---
title: Esempio avanzato per i contenitori
description: ''
ms.custom: ''
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c941928495dc39dc6b6ecbe9600f39dad969fec2
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
ms.locfileid: "31621145"
---
# <a name="advanced-example-for-containers"></a>Esempio avanzato per i contenitori

Il Dockerfile di esempio in [Installare Build Tools in un contenitore](build-tools-container.md) usa sempre l'immagine [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) basata sull'immagine microsoft/windowsservercore più recente e il programma di installazione più recente di Visual Studio Build Tools 2017. Se si pubblica questa immagine in un [registro Docker](https://azure.microsoft.com/services/container-registry) a disposizione per il pull, l'immagine potrebbe essere appropriata per molti scenari. Nella pratica, tuttavia, è più comune essere specifici in merito all'immagine di base usata, i file binari scaricati e le versioni degli strumenti installate.

Il Dockerfile di esempio seguente usa un tag di versione specifico dell'immagine microsoft/dotnet-framework. L'uso di un tag specifico per un'immagine di base è comune e rende più facile ricordare che per la creazione o la ricreazione delle immagini viene sempre usata la stessa base.

> [!NOTE]
> Non è possibile installare Visual Studio in microsoft/windowsservercore:10.0.14393.1593, o in qualsiasi immagine basata su di esso, che presenta problemi noti di avvio del programma di installazione in un contenitore. Per altre informazioni, vedere i [problemi noti](build-tools-container-issues.md).

Nell'esempio seguente viene scaricata l'ultima versione di Build Tools 2017. Se si vuole usare una versione precedente di Build Tools che è possibile installare in un contenitore in un secondo momento, è necessario innanzitutto [creare](create-an-offline-installation-of-visual-studio.md) e [mantenere](update-a-network-installation-of-visual-studio.md) un layout.

## <a name="install-script"></a>Installazione dello script

Per raccogliere i log, quando si verifica un errore di installazione, nella directory di lavoro creare uno script batch denominato "Install.cmd" con il seguente contenuto:

```shell
@if not defined _echo echo off
setlocal enabledelayedexpansion

call %*
if "%ERRORLEVEL%"=="3010" (
    exit /b 0
) else (
    if not "%ERRORLEVEL%"=="0" (
        set ERR=%ERRORLEVEL%
        call C:\TEMP\collect.exe -zip:C:\vslogs.zip

        exit /b !ERR!
    )
)
```

## <a name="dockerfile"></a>Dockerfile

Nella directory di lavoro creare il "Dockerfile" con il seguente contenuto:

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:1a66e2b5f3a5b8b98ac703a8bfd4902ae60d307ed9842978df40dbc04ac86b1b
ARG FROM_IMAGE=microsoft/dotnet-framework:4.7.1-20180410-windowsservercore-1709
FROM ${FROM_IMAGE}

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/15/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Download and install Build Tools excluding workloads and components with known issues.
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --all `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

Eseguire il comando seguente per creare l'immagine nella cartella di lavoro corrente:

```shell
docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
```

Passare facoltativamente uno o entrambi gli argomenti `FROM_IMAGE` o `CHANNEL_URL` usando lo switch della riga di comando `--build-arg` per specificare un'immagine di base diversa o la posizione di un layout interno per mantenere un'immagine fissa.

## <a name="diagnosing-install-failures"></a>Diagnosi degli errori di installazione

Questo esempio scarica strumenti specifici e verifica che gli hash corrispondano. Scarica inoltre la versione più recente di Visual Studio e l'utilità di raccolta log di .NET in modo che, se si verifica un errore di installazione, sia possibile copiare i log nel computer host per analizzare l'errore.

```shell
> docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
Sending build context to Docker daemon
...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

Al termine dell'esecuzione dell'ultima riga aprire "%TEMP%\vslogs.zip" nel computer o registrare un problema nel sito Web della [community di sviluppatori](https://developercommunity.visualstudio.com).

## <a name="get-support"></a>Supporto

Non sempre tutto funziona correttamente. Se l'installazione di Visual Studio non riesce, vedere la pagina [Risoluzione dei problemi di installazione e aggiornamento di Visual Studio 2017](troubleshooting-installation-issues.md). Se nessuna delle procedure di risoluzione dei problemi risulta utile, contattare Microsoft tramite chat in tempo reale per richiedere assistenza per l'installazione (solo in lingua inglese). Per informazioni dettagliate, vedere la [pagina del supporto di Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ecco alcune altre opzioni di supporto:

* È possibile segnalare i problemi del prodotto a Microsoft tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) che viene visualizzato sia nel programma di installazione di Visual Studio che nell'IDE di Visual Studio.
* È possibile condividere un suggerimento per il prodotto con Microsoft in [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* È possibile visualizzare lo stato dei problemi del prodotto e trovare una risposta nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/).
* È anche possibile comunicare con gli sviluppatori Microsoft e altri sviluppatori di Visual Studio partecipando alla [conversazione dedicata a Visual Studio nella community di Gitter](https://gitter.im/Microsoft/VisualStudio). Per questa opzione è necessario un account [GitHub](https://github.com/).

## <a name="see-also"></a>Vedere anche

* [Installare Build Tools in un contenitore](build-tools-container.md)
* [Problemi noti dei contenitori](build-tools-container-issues.md)
* [ID dei carichi di lavoro e dei componenti di Visual Studio Build Tools 2017](workload-component-id-vs-build-tools.md)
