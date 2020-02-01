---
title: Risoluzione degli errori dei client Docker in Windows | Microsoft Docs
description: Risolvere i problemi riscontrati quando si usa Visual Studio per creare e distribuire app Web in Docker in Windows tramite Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: conceptual
ms.workload: multiple
ms.date: 10/13/2017
ms.author: ghogen
ms.openlocfilehash: ce7645b8b4f71cf94d7320a0072d15b2b8083dec
ms.sourcegitcommit: 4be64917e4224fd1fb27ba527465fca422bc7d62
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76923019"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Risolvere i problemi di sviluppo di Visual Studio con Docker

Quando si lavora con Visual Studio container Tools, è possibile che si verifichino problemi durante la compilazione o il debug dell'applicazione. Di seguito sono riportati alcuni passaggi comuni per la risoluzione dei problemi.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>La condivisione del volume non è abilitata. Abilitare la condivisione dei volumi nelle impostazioni Docker CE per Windows (solo per i contenitori Linux)

Per risolvere il problema:

1. Fare clic con il pulsante destro del mouse su **Docker per Windows** nell'area di notifica e quindi scegliere **Impostazioni**.
1. Selezionare **unità condivise** e condividere l'unità di sistema insieme all'unità in cui risiede il progetto.

> [!NOTE]
> Se i file vengono visualizzati condivisi, potrebbe essere necessario fare clic sul pulsante "Reimposta credenziali..." nella parte inferiore della finestra di dialogo per abilitare nuovamente la condivisione del volume. Per continuare dopo la reimpostazione delle credenziali, potrebbe essere necessario riavviare Visual Studio.

![unità condivise](media/troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> Versioni di Visual Studio successive a Visual Studio 2017 versione 15,6 richiesta quando non sono configurate **unità condivise** .

### <a name="container-type"></a>Tipo di contenitore

Quando si aggiunge il supporto di Docker a un progetto, scegliere un contenitore Windows o Linux. L'host Docker deve eseguire lo stesso tipo di contenitore. Per modificare il tipo di contenitore nell'istanza di Docker in esecuzione, fare clic con il pulsante destro del mouse sull'icona di Docker sulla barra delle applicazioni e scegliere **Switch to Windows containers** (Passa ai contenitori Windows) o **Switch to Linux containers** (Passa ai contenitori Linux).

## <a name="unable-to-start-debugging"></a>Non è possibile avviare il debug

Un motivo potrebbe essere correlato alla presenza di componenti di debug non aggiornati nella cartella del profilo utente. Eseguire i comandi seguenti per rimuovere le cartelle in modo che i componenti di debug più recenti vengano scaricati alla successiva sessione di debug.

- del%UserProfile%\vsdbg
- del%UserProfile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Errori specifici della rete durante il debug dell'applicazione

Provare a eseguire lo script scaricabile da [Cleanup container host networking](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking), che aggiornerà i componenti correlati alla rete nel computer host.

## <a name="mounts-denied"></a>Montaggi negati

Quando si usa Docker per macOS, è possibile che si verifichi un errore che fa riferimento alla cartella/usr/local/share/dotnet/sdk/NuGetFallbackFolder. Aggiunge la cartella alla scheda Condivisione file in Docker

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

È inoltre possibile utilizzare il comando `net localgroup` al prompt dei comandi dell'amministratore per aggiungere utenti a gruppi specifici.

```cmd
net localgroup docker-users DOMAIN\username /add
```

In PowerShell usare la funzione [Add-LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember) .

## <a name="low-disk-space"></a>Spazio su disco insufficiente

Per impostazione predefinita, Docker archivia le immagini nella cartella *% ProgramData%/Docker/* , che in genere si trova nell'unità di sistema * C:\ProgramData\Docker\*. Per evitare che immagini occupano spazio prezioso nell'unità di sistema, è possibile modificare il percorso della cartella immagini.  Dall'icona Docker sulla barra delle applicazioni, aprire Docker Settings, scegliere **daemon**e passare da **Basic** a **Advanced**. Nel riquadro di modifica aggiungere l'impostazione della proprietà `graph` con il valore della posizione desiderata per le immagini docker:

```json
    "graph": "D:\\mypath\\images"
```

![Screenshot dell'impostazione del percorso dell'immagine Docker](media/troubleshooting-docker-errors/docker-settings-image-location.png)

Fare clic su **applica** per riavviare docker. Questa procedura modifica il file di configurazione in *%ProgramData%\docker\config\daemon.JSON*. Le immagini compilate in precedenza non vengono spostate.

## <a name="microsoftdockertools-github-repo"></a>Repository GitHub Microsoft/DockerTools

Per eventuali altri problemi riscontrati, vedere problemi relativi a [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues) .