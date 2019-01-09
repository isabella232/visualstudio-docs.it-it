---
title: Esempio avanzato per i contenitori
description: ''
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.custom: ''
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 408c66d87dbc932e09e1d5744ab5595672a00534
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307632"
---
# <a name="advanced-example-for-containers"></a>Esempio avanzato per i contenitori

Il Dockerfile di esempio in [Installare Build Tools in un contenitore](build-tools-container.md) usa sempre l'immagine [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) basata sull'immagine microsoft/windowsservercore più recente e il programma di installazione più recente di Visual Studio Build Tools 2017. Se si pubblica questa immagine in un [registro Docker](https://azure.microsoft.com/services/container-registry) a disposizione per il pull, l'immagine potrebbe essere appropriata per molti scenari. Nella pratica, tuttavia, è più comune essere specifici in merito all'immagine di base usata, i file binari scaricati e le versioni degli strumenti installate.

Il Dockerfile di esempio seguente usa un tag di versione specifico dell'immagine microsoft/dotnet-framework. L'uso di un tag specifico per un'immagine di base è comune e rende più facile ricordare che per la creazione o la ricreazione delle immagini viene sempre usata la stessa base.

> [!NOTE]
> Non è possibile installare Visual Studio in microsoft/windowsservercore:10.0.14393.1593, o in qualsiasi immagine basata su di esso, che presenta problemi noti di avvio del programma di installazione in un contenitore. Per altre informazioni, vedere i [problemi noti](build-tools-container-issues.md).

Nell'esempio seguente viene scaricata l'ultima versione di Build Tools 2017. Se si vuole usare una versione precedente di Build Tools che è possibile installare in un contenitore in un secondo momento, è necessario prima [creare](create-an-offline-installation-of-visual-studio.md) e [mantenere](update-a-network-installation-of-visual-studio.md) un layout.

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
   > [!WARNING]
   > Non è possibile installare Visual Studio 2017 versione 15.8 o versioni precedenti (qualsiasi prodotto) in mcr<span></span>.microsoft\.com\/windows\/servercore:1809 o versioni successive. Non viene visualizzato un errore.
   >
   > Per altre informazioni, vedere [Problemi noti dei contenitori](build-tools-container-issues.md).

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

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installare Build Tools in un contenitore](build-tools-container.md)
* [Problemi noti dei contenitori](build-tools-container-issues.md)
* [ID dei carichi di lavoro e dei componenti di Visual Studio Build Tools 2017](workload-component-id-vs-build-tools.md)
