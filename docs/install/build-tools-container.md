---
title: Installare Visual Studio Build Tools in un contenitore
titleSuffix: ''
description: Informazioni su come installare Visual Studio Build Tools in un contenitore di Windows per supportare flussi di lavoro di integrazione continua e recapito continuo (CI/CD).
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 37ce2fc60ac2a57baddf62e68a900349ed072f4d
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2018
ms.locfileid: "53160088"
---
# <a name="install-build-tools-into-a-container"></a>Installare Build Tools in un contenitore

È possibile installare Visual Studio Build Tools in un contenitore di Windows per supportare flussi di lavoro di integrazione continua e recapito continuo (CI/CD). Questo articolo illustra le modifiche di configurazione di Docker necessarie, nonché i [carichi di lavoro e i componenti](workload-component-id-vs-build-tools.md) che è possibile installare in un contenitore.

I [contenitori](https://www.docker.com/what-container) sono un ottimo modo per inserire un sistema di compilazione coerente in un pacchetto utilizzabile non solo in un ambiente server CI/CD, ma anche per gli ambienti di sviluppo. Ad esempio, è possibile montare il codice sorgente in un contenitore per la compilazione in un ambiente personalizzato, pur continuando a usare Visual Studio o altri strumenti per scrivere il codice. Se il flusso di lavoro CI/CD usa la stessa immagine del contenitore, è possibile essere certi che la compilazione del codice avvenga in modo coerente. È possibile usare i contenitori anche per la coerenza del runtime, un'esigenza comune per i microservizi che usano più contenitori con un sistema di orchestrazione, ma ciò esula dagli scopi di questo articolo.

Se Visual Studio Build Tools non include ciò che serve per la compilazione del codice sorgente, le stesse procedure sono valide anche per altri prodotti Visual Studio. Si noti, tuttavia, che i contenitori di Windows non supportano un'interfaccia utente interattiva pertanto tutti i comandi devono essere automatizzati.

## <a name="overview"></a>Panoramica

Si usa [Docker](https://www.docker.com/what-docker) per creare un'immagine da cui è possibile creare contenitori per la compilazione del codice sorgente. Il Dockerfile di esempio installa la versione più recente di Visual Studio Build Tools 2017 e altri programmi utili, spesso usati per la compilazione di codice sorgente. È possibile personalizzare ulteriormente il Dockerfile per includere altri strumenti e script per eseguire test, pubblicare l'output della compilazione e altro ancora.

Se è già stato installato Docker per Windows, è possibile procedere al passaggio 3.

## <a name="step-1-enable-hyper-v"></a>Passaggio 1. Abilitare Hyper-V

Per impostazione predefinita, Hyper-V non è abilitato ed è necessario che lo sia per avviare Docker per Windows, perché attualmente è supportato solo l'isolamento Hyper-V per Windows 10.

* [Abilitare Hyper-V in Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)
* [Abilitare Hyper-V in Windows Server 2016](https://docs.microsoft.com/windows-server/virtualization/hyper-v/get-started/install-the-hyper-v-role-on-windows-server)

> [!NOTE]
> La virtualizzazione deve essere abilitata nel computer. In genere è abilitata per impostazione predefinita. Tuttavia, se l'installazione di Hyper-V non riesce, fare riferimento alla documentazione del sistema per informazioni su come abilitare la virtualizzazione.

## <a name="step-2-install-docker-for-windows"></a>Passaggio 2. Installare Docker per Windows

Se si usa Windows 10, è possibile [scaricare e installare Docker Community Edition](https://docs.docker.com/docker-for-windows/install). Se si usa Windows Server 2016, seguire le [istruzioni per installare Docker Enterprise Edition](https://docs.docker.com/install/windows/docker-ee).

## <a name="step-3-switch-to-windows-containers"></a>Passaggio 3. Passare ai contenitori di Windows

È possibile installare Build Tools 2017 solo in Windows e ciò richiede il [passaggio ai contenitori di Windows](https://docs.docker.com/docker-for-windows/#getting-started-with-windows-containers). I contenitori di Windows in Windows 10 supportano solo l'[isolamento Hyper-V](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container), mentre i contenitori di Windows in Windows Server 2016 supportano sia l'isolamento Hyper-V che l'isolamento dei processi.

## <a name="step-4-expand-maximum-container-disk-size"></a>Passaggio 4. Espandere le dimensioni massime del disco del contenitore

Visual Studio Build Tools e, in maggior misura Visual Studio, richiedono una grande quantità di spazio su disco per l'installazione di tutti gli strumenti. Anche se il Dockerfile di esempio disabilita la cache dei pacchetti, è necessario aumentare le dimensioni del disco delle immagini dei contenitori per tenere conto dello spazio necessario. Attualmente in Windows è possibile aumentare le dimensioni del disco solo modificando la configurazione di Docker.

**In Windows 10**:

1. [Fare clic con il pulsante destro del mouse sull'icona di Docker per Windows](https://docs.docker.com/docker-for-windows/#docker-settings) sulla barra delle applicazioni e scegliere **Impostazioni**.
2. Fare clic sulla sezione [Daemon](https://docs.docker.com/docker-for-windows/#docker-daemon).
3. [Impostare il pulsante **Basic** (Base)](https://docs.docker.com/docker-for-windows/#edit-the-daemon-configuration-file) su **Advanced** (Avanzate).
4. Aggiungere la proprietà di matrice JSON seguente per aumentare lo spazio su disco a 120 GB (più che sufficienti per Build Tools e con possibilità di espansione).

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Questa proprietà viene aggiunta alle impostazioni già definite. Ad esempio, applicando queste modifiche al file di configurazione del daemon predefinito, si ottiene:

   ```json
   {
     "registry-mirrors": [],
     "insecure-registries": [],
     "debug": true,
     "experimental": true,
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

5. Fare clic su **Applica**.

**In Windows Server 2016**:

1. Arrestare il servizio "docker":

   ```shell
   sc.exe stop docker
   ```

2. Da un prompt dei comandi con privilegi elevati, modificare "%ProgramData%\Docker\config\daemon.json" (o quanto specificato per `dockerd --config-file`).
3. Aggiungere la proprietà di matrice JSON seguente per aumentare lo spazio su disco a 120 GB (più che sufficienti per Build Tools e con possibilità di espansione).

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   Questa proprietà viene aggiunta alle impostazioni già definite.
4. Salvare e chiudere il file.
5. Avviare il servizio "docker":

   ```shell
   sc.exe start docker
   ```

## <a name="step-5-create-and-build-the-dockerfile"></a>Passaggio 5. Creare e compilare il Dockerfile

Salvare il Dockerfile di esempio seguente in un nuovo file su disco. Se il file è denominato semplicemente "Dockerfile", viene riconosciuto per impostazione predefinita.

> [!NOTE]
> Questo Dockerfile di esempio esclude solo le versioni precedenti di Windows SDK che non possono essere installate in contenitori. Con le versioni precedenti il comando di compilazione ha esito negativo.

1. Aprire un prompt dei comandi.
2. Creare una nuova directory (operazione consigliata):

   ```shell
   mkdir C:\BuildTools
   ```

3. Passare alla nuova directory:

   ```shell
   cd C:\BuildTools
   ```

3. Salvare il contenuto seguente in C:\BuildTools\Dockerfile.

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.1.
   FROM microsoft/dotnet-framework:4.7.1

   # Restore the default Windows shell for correct batch processing below.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --all `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!NOTE]
   > Se si basa l'immagine direttamente su microsoft/windowsservercore, .NET Framework potrebbe non essere installato correttamente e non viene indicato alcun errore di installazione. Il codice gestito potrebbe non essere eseguito dopo il completamento dell'installazione. Basare invece l'immagine su [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) o versione successiva. Si noti anche che le immagini più recenti potrebbero usare PowerShell come `SHELL` predefinita impedendo l'esecuzione delle istruzioni `RUN` e `ENTRYPOINT`.

4. Eseguire il comando seguente in tale directory.

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   Questo comando compila il Dockerfile nella directory corrente con 2 GB di memoria. L'impostazione predefinita di 1 GB non è sufficiente quando sono installati alcuni carichi di lavoro. Tuttavia, si potrebbe riuscire a completare la compilazione con solo 1 GB di memoria a seconda dei requisiti di compilazione.

   L'immagine finale viene contrassegnata con "buildtools2017:latest" in modo da poterla eseguire facilmente in un contenitore come "buildtools2017", dato che il tag "latest" è il valore predefinito se non si specifica alcun tag. Se si vuole usare una versione specifica di Visual Studio Build Tools 2017 in uno [scenario più avanzato](advanced-build-tools-container.md), è possibile contrassegnare il contenitore con un numero di build di Visual Studio specifico, oltre a usare il tag "latest", in modo che i contenitori possano usare una versione specifica in modo coerente.

## <a name="step-6-using-the-built-image"></a>Passaggio 6. Uso dell'immagine compilata

Dopo avere creato un'immagine, è possibile eseguirla in un contenitore per eseguire compilazioni sia automatiche che interattive. L'esempio usa il prompt dei comandi per gli sviluppatori, in modo che la variabile PATH e altre variabili di ambiente siano già configurate.

1. Aprire un prompt dei comandi.
2. Eseguire il contenitore per avviare un ambiente di PowerShell con tutte le variabili di ambiente per gli sviluppatori impostate:

   ```shell
   docker run -it buildtools2017
   ```

Per usare questa immagine per il flusso di lavoro CI/CD, è possibile pubblicarla nel proprio [Registro Azure Container](https://azure.microsoft.com/services/container-registry) o in un altro [registro Docker](https://docs.docker.com/registry/deploying) interno, in modo che i server possano semplicemente eseguirne il pull.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Esempio avanzato per i contenitori](advanced-build-tools-container.md)
* [Problemi noti dei contenitori](build-tools-container-issues.md)
* [ID dei carichi di lavoro e dei componenti di Visual Studio Build Tools 2017](workload-component-id-vs-build-tools.md)
