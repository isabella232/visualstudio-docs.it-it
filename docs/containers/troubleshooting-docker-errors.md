---
title: Risoluzione degli errori dei client Docker in Windows | Microsoft Docs
description: Risoluzione dei problemi che si verificano quando si usa Visual Studio per creare e distribuire app Web in Docker su Windows mediante Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: troubleshooting
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 31b9d8649abed0f9901aa872ff3939c25e3025b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "87235108"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Risolvere i problemi di sviluppo di Visual Studio con Docker

Quando si lavora con Visual Studio container Tools, è possibile che si verifichino problemi durante la compilazione o il debug dell'applicazione. Di seguito sono descritti alcuni passaggi comuni per la risoluzione dei problemi.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>La condivisione dei volumi non è abilitata. Abilitare la condivisione dei volumi nelle impostazioni di Docker CE per Windows (solo per i contenitori Linux)

Per risolvere il problema:

1. Fare doppio clic su **Docker per Windows** nell'area di notifica e quindi selezionare **Impostazioni**.
1. Fare clic su **Unità condivise** e condividere l'unità di sistema e l'unità in cui si trova il progetto.

> [!NOTE]
> Se i file risultano condivisi, potrebbe comunque essere necessario fare clic sul collegamento "Reimposta credenziali" nella parte inferiore della finestra di dialogo per abilitare di nuovo la condivisione dei volumi. Per continuare dopo aver reimpostato le credenziali, potrebbe essere necessario riavviare Visual Studio.

![unità condivise](media/troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> Versioni di Visual Studio successive a Visual Studio 2017 versione 15,6 richiesta quando non sono configurate **unità condivise** .

### <a name="container-type"></a>Tipo di contenitore

Quando si aggiunge il supporto di Docker a un progetto, scegliere un contenitore Windows o Linux. L'host Docker deve eseguire lo stesso tipo di contenitore. Per modificare il tipo di contenitore nell'istanza di Docker in esecuzione, fare clic con il pulsante destro del mouse sull'icona di Docker sulla barra delle applicazioni e scegliere **Switch to Windows containers** (Passa ai contenitori Windows) o **Switch to Linux containers** (Passa ai contenitori Linux).

## <a name="unable-to-start-debugging"></a>Impossibile avviare il debug

Un motivo potrebbe essere correlato alla presenza di componenti di debug non aggiornati nella cartella del profilo utente. Eseguire i comandi seguenti per rimuovere queste cartelle in modo che vengano scaricati i componenti di debug più recenti alla successiva sessione di debug.

- del %userprofile%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Errori specifici della rete durante il debug dell'applicazione

Provare a eseguire lo script scaricabile dall'articolo relativo alla [pulizia dei componenti di rete dell'host dei contenitori](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking), che aggiornerà i componenti di rete nel computer host.

## <a name="mounts-denied"></a>Montaggi negati

Quando si usa Docker per macOs, potrebbe verificarsi un errore durante il riferimento alla cartella /usr/local/share/dotnet/sdk/NuGetFallbackFolder. Aggiunge la cartella alla scheda Condivisione file in Docker

## <a name="docker-users-group"></a>Gruppo utenti Docker

È possibile che si verifichi l'errore seguente in Visual Studio quando si utilizzano i contenitori:

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

È necessario essere un membro del gruppo "Docker-Users" per avere le autorizzazioni per lavorare con i contenitori docker.  Per aggiungere se stessi al gruppo in Windows 10, attenersi alla procedura seguente:

1. Dal menu Start aprire **Gestione computer**.
1. Espandere **utenti e gruppi locali**e scegliere **gruppi**.
1. Trovare il gruppo **Docker-Users** , fare clic con il pulsante destro del mouse e scegliere **Aggiungi al gruppo**.
1. Aggiungere l'account utente o gli account.
1. Disconnettersi ed eseguire nuovamente l'accesso per rendere effettive le modifiche.

È inoltre possibile utilizzare il `net localgroup` comando al prompt dei comandi dell'amministratore per aggiungere utenti a gruppi specifici.

```cmd
net localgroup docker-users DOMAIN\username /add
```

In PowerShell usare la funzione [Add-LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember) .

## <a name="low-disk-space"></a>Spazio su disco insufficiente

Per impostazione predefinita, Docker archivia le immagini nella cartella *% ProgramData%/Docker/* , che in genere si trova nell'unità di sistema, * C:\ProgramData\Docker \* . Per evitare che immagini occupano spazio prezioso nell'unità di sistema, è possibile modificare il percorso della cartella immagini.  Dall'icona Docker sulla barra delle applicazioni, aprire Docker Settings, scegliere **daemon**e passare da **Basic** a **Advanced**. Nel riquadro di modifica aggiungere l' `graph` impostazione della proprietà con il valore della posizione desiderata per le immagini docker:

```json
    "graph": "D:\\mypath\\images"
```

![Screenshot dell'impostazione del percorso dell'immagine Docker](media/troubleshooting-docker-errors/docker-settings-image-location.png)

Fare clic su **applica** per riavviare docker. Questa procedura modifica il file di configurazione in *% ProgramData% \docker\config\daemon.json*. Le immagini compilate in precedenza non vengono spostate.

## <a name="microsoftdockertools-github-repo"></a>Repository GitHub Microsoft/DockerTools

Per qualsiasi altro problema riscontrato, vedere i problemi di [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues).

## <a name="see-also"></a>Vedere anche

- [Risoluzione dei problemi di Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)