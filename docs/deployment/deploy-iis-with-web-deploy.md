---
title: Distribuire ASP.NET in IIS utilizzando la distribuzione Web
ms.custom: ''
ms.date: 06/04/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: a63d9947f544ddff1de81aaf34ed62c9646fba3d
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34794203"
---
# <a name="deploy-aspnet-to-a-remote-iis-computer-using-web-deploy-in-visual-studio"></a>Distribuire ASP.NET in un Computer remoto IIS usando distribuzione Web in Visual Studio

In questo articolo viene illustrato come impostare e configurare un'applicazione di Visual Studio 2017 ASP.NET MVC 4.5.2 e distribuirlo a IIS. In questo articolo include i passaggi per la configurazione di una configurazione di base di IIS in Windows server e distribuzione dell'app da Visual Studio. Vengono inclusi per assicurarsi che il server ha richiesto i componenti installati e che si è pronti per distribuire questi passaggi. Se si distribuisce un'applicazione ASP.NET Core, alcuni passaggi sono diversi. Per distribuire un'app di ASP.NET Core, vedere [pubblica un'applicazione a IIS tramite l'importazione delle impostazioni di pubblicazione](../deployment/tutorial-import-publish-settings-iis.md) per istruzioni. In alcuni scenari ASP.NET e ASP.NET Core, è più veloce per distribuire in IIS tramite l'importazione delle impostazioni di pubblicazione.

Queste procedure sono state testate su queste configurazioni del server:
* Windows Server 2012 R2 e IIS 8 (per Windows Server 2008 R2, i passaggi di server sono diversi)

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Creare ASP.NET 4.5.2 applicazione nel computer di Visual Studio
  
1. Nel computer che esegue Visual Studio, scegliere **File > Nuovo progetto**.

1. Sotto **Visual c#** oppure **Visual Basic**, scegliere **Web**, quindi nel riquadro centrale scegliere **applicazione Web ASP.NET (.NET Framework)** e quindi fare clic su **OK**.

    Se i modelli di progetto specificato non viene visualizzato, fare clic sul **aperto Visual Studio Installer** collegamento nel riquadro sinistro della finestra di **nuovo progetto** finestra di dialogo. Verrà avviato il Programma di installazione di Visual Studio. Vedere i prerequisiti descritti in questo articolo per identificare i necessari Visual Studio carichi di lavoro, che deve essere installato.

1. Scegliere **MVC** (.NET Framework) e assicurarsi che **Nessuna autenticazione** sia selezionata e quindi fare clic su **OK**.

1. Digitare un nome come **MyWebApp** e fare clic su **OK**.

    Visual Studio crea il progetto.

1. Scegliere **compilazione > Compila soluzione** per compilare il progetto.

## <a name="bkmk_configureIIS"></a> Installare e configurare IIS in Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aggiornare le impostazioni di sicurezza del browser in Windows Server

Se sicurezza avanzata è abilitata in Internet Explorer (è abilitata per impostazione predefinita), potrebbe essere necessario aggiungere alcuni domini come siti attendibili per consentire il download alcuni dei componenti server web. Aggiungere siti attendibili, passare a **Opzioni Internet > sicurezza > siti attendibili > siti**. Aggiungere i seguenti domini.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Quando si scarica il software, è possibile ricevere le richieste per concedere autorizzazioni per caricare vari script del sito web e risorse. Alcune di queste risorse non sono necessarie, ma per semplificare il processo, fare clic su **Aggiungi** quando richiesto.

## <a name="BKMK_deploy_asp_net"></a> Installare ASP.NET 4.5 in Windows Server

Se si desiderano informazioni più dettagliate per installare ASP.NET in IIS, vedere [IIS 8.0 usando ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Nel riquadro sinistro di Server Manager, selezionare **IIS**. Il server e scegliere **Internet Information Services (IIS) Manager**.

1. Utilizzare l'installazione guidata piattaforma Web (WebPI) per installare ASP.NET 4.5 (scegliere il nodo del Server in Windows Server 2012 R2, **ottenere nuovi componenti della piattaforma Web** e quindi cercare ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Se si utilizza Windows Server 2008 R2, installare ASP.NET 4 invece con il seguente comando:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Riavviare il sistema (o eseguire **net stop stato /y** seguito da **net start w3svc** da un prompt dei comandi per visualizzare una modifica al percorso di sistema).

## <a name="BKMK_install_webdeploy"></a> 3.6 in Windows Server di distribuzione Web di installazione

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="BKMK_deploy_asp_net"></a> Configura sito Web di ASP.NET sul computer del Server di Windows

1. Aprire Esplora risorse e creare una nuova cartella **C:\Publish**, in cui verranno distribuiti in un secondo momento il progetto ASP.NET.

2. Se non è già aperto, aprire il **Internet Information Services (IIS) Manager**. (Nel riquadro sinistro di Server Manager, selezionare **IIS**. Il server e scegliere **Gestione Internet Information Services (IIS)**.)

3. In **connessioni** nel riquadro a sinistra, passare a **siti**.

4. Selezionare il **sito Web predefinito**, scegliere **le impostazioni di base**e impostare il **percorso fisico** a **C:\Publish**.

5. Fare clic con il pulsante destro del mouse sul nodo **Sito Web predefinito** e scegliere **Aggiungi applicazione**.

6. Impostare il **Alias** campo **MyASPApp**, accettare il valore predefinito di Pool di applicazioni (**DefaultAppPool**) e impostare il **percorso fisico** a  **C:\Publish**.

7. In **connessioni**selezionare **pool di applicazioni**. Aprire **DefaultAppPool** e impostare il campo pool di applicazioni su **ASP.NET v 4.0** (ASP.NET 4.5 non è un'opzione per il pool di applicazioni).

8. Con il sito selezionato in Gestione IIS, scegliere **Modifica autorizzazioni**e assicurarsi che tale account IUSR, IIS_IUSRS o l'utente configurato per il Pool di applicazioni è un utente autorizzato con diritti di lettura ed esecuzione. Se nessuno di questi utenti sono presenti, aggiungere IUSR come utente con diritti di lettura ed esecuzione.

## <a name="bkmk_webdeploy"></a> Pubblicare e distribuire l'app usando distribuzione Web da Visual Studio

[!INCLUDE [deploy-app-web-deploy](../deployment/includes/deploy-app-web-deploy.md)]

Inoltre, è necessario leggere la sezione su [risoluzione dei problemi relativi a porte](#bkmk_openports).

## <a name="bkmk_openports"></a> Risoluzione dei problemi: Aprire le porte necessarie in Windows Server

Nella maggior parte delle installazioni, vengono aperte le porte richieste dall'installazione di ASP.NET e distribuzione Web. Tuttavia, devi verificare che le porte siano aperte.

> [!NOTE]
> In una macchina virtuale di Azure, è necessario aprire porte tramite il [il gruppo di sicurezza di rete](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Porte richieste:

* 80 - necessari per IIS
* 8172 - necessari per distribuzione Web distribuire l'app da Visual Studio

1. Per aprire una porta in Windows Server, aprire il **avviare** menu, cercare **Windows Firewall con sicurezza avanzata**.

2. Scegliere quindi **regole connessioni in entrata > nuova regola > porta**. Scegliere **Avanti** e in **porte locali specifiche**, immettere il numero di porta, fare clic su **Avanti**, quindi **Consenti la connessione**, fare clic su Avanti, e aggiungere il nome (**IIS**, **distribuzione Web**, o **msvsmon**) per la regola in ingresso.

    Se si desidera visualizzare ulteriori dettagli su come configurare Windows Firewall, vedere [configurare Windows Firewall per debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Creare regole aggiuntive per le altre porte necessarie.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è creato un file di impostazioni di pubblicazione, importato in Visual Studio e distribuito un'app ASP.NET in IIS. È inoltre possibile distribuire tramite l'importazione delle impostazioni di pubblicazione.

> [!div class="nextstepaction"]
> [Distribuire a IIS tramite l'importazione delle impostazioni di pubblicazione](../deployment/tutorial-import-publish-settings-iis.md)