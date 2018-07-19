---
title: Distribuire ASP.NET in IIS usando distribuzione Web
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
ms.openlocfilehash: 4705ca6e72001f8930e2fa4270515df53e1213a8
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080850"
---
# <a name="deploy-aspnet-to-a-remote-iis-computer-using-web-deploy-in-visual-studio"></a>Distribuire ASP.NET in un computer IIS remoto usando distribuzione Web in Visual Studio

Questo articolo illustra come impostare e configurare un'applicazione MVC di ASP.NET di Visual Studio 2017 4.5.2 e distribuirla in IIS. Questo articolo include i passaggi di configurazione di una configurazione di base di IIS in Windows server e la distribuzione dell'app da Visual Studio. Questi passaggi sono, per assicurarsi che il server ha richiesto i componenti installati e che si è pronti per la distribuzione. Se si distribuisce un'applicazione ASP.NET Core, alcuni passaggi sono diversi. Per distribuire un'app ASP.NET Core, vedere [pubblica un'applicazione a IIS tramite l'importazione delle impostazioni di pubblicazione](../deployment/tutorial-import-publish-settings-iis.md) per le istruzioni. In alcuni scenari ASP.NET e ASP.NET Core, è più veloce da distribuire a IIS tramite l'importazione delle impostazioni di pubblicazione.

Queste procedure sono state testate in queste configurazioni di server:
* Windows Server 2012 R2 e IIS 8 (per Windows Server 2008 R2, i passaggi di server sono diversi)

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Creazione di ASP.NET 4.5.2 dell'applicazione nel computer di Visual Studio
  
1. Nel computer che esegue Visual Studio, scegliere **File** > **nuovo progetto**.

1. Sotto **Visual c#** oppure **Visual Basic**, scegliere **Web**, quindi nel riquadro centrale scegliere **applicazione Web ASP.NET (.NET Framework)** e quindi fare clic su **OK**.

    Se i modelli di progetto specificato non è visibile, fare clic sul **aperto Visual Studio Installer** collegamento nel riquadro sinistro della finestra di **nuovo progetto** nella finestra di dialogo. Verrà avviato il Programma di installazione di Visual Studio. Vedere i prerequisiti descritti in questo articolo per identificare i necessari Visual Studio carichi di lavoro, che devono essere installati.

1. Scegli **MVC** (.NET Framework) e assicurarsi che **Nessuna autenticazione** sia selezionata e quindi fare clic su **OK**.

1. Digitare un nome come **MyWebApp** e fare clic su **OK**.

    Visual Studio crea il progetto.

1. Scegli **compilare** > **Compila soluzione** per compilare il progetto.

## <a name="install-and-configure-iis-on-windows-server"></a>Installare e configurare IIS in Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aggiornare le impostazioni di sicurezza del browser in Windows Server

Se sicurezza avanzata è abilitata in Internet Explorer (è abilitata per impostazione predefinita), potrebbe essere necessario aggiungere alcuni domini come siti attendibili per poter scaricare alcuni dei componenti server web. Aggiungere i siti attendibili scegliendo **Opzioni Internet** > **sicurezza** > **siti attendibili** > **siti** . Aggiungere i domini seguenti.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Quando si scarica il software, è possibile ricevere le richieste di concedere l'autorizzazione per caricare vari script del sito web e risorse. Alcune di queste risorse non sono necessarie, ma per semplificare il processo, fare clic su **Add** quando richiesto.

## <a name="install-aspnet-45-on-windows-server"></a>Installare ASP.NET 4.5 in Windows Server

Se si desiderano informazioni più dettagliate per installare ASP.NET in IIS, vedere [IIS 8.0 usando ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Nel riquadro sinistro di Server Manager, selezionare **IIS**. Fare doppio clic su server e selezionare **Internet Information Services (IIS) Manager**.

1. Usare l'installazione guidata piattaforma Web (WebPI) per installare ASP.NET 4.5 (dal nodo del Server in Windows Server 2012 R2, scegliere **Ottieni nuovi componenti della piattaforma Web** e quindi cercare ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Se si usa Windows Server 2008 R2, installare ASP.NET 4 invece con il seguente comando:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Riavviare il sistema (o eseguire **net stop was /y** aggiungendo **net start w3svc** da un prompt dei comandi per visualizzare una modifica al percorso di sistema).

## <a name="install-web-deploy-36-on-windows-server"></a>3.6 in Windows Server di distribuzione di installazione Web

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="configure-aspnet-web-site-on-the-windows-server-computer"></a>Configurare il sito Web ASP.NET nel computer Windows Server

1. Aprire l'Explorer di Windows e creare una nuova cartella denominata **C:\Publish**, in cui in seguito si distribuirà il progetto ASP.NET.

2. Se non è già aperto, aprire il **Internet Information Services (IIS) Manager**. (Nel riquadro sinistro di Server Manager, selezionare **IIS**. Fare doppio clic su server e selezionare **Internet Information Services (IIS) Manager**.)

3. Sotto **connessioni** nel riquadro a sinistra, passare alla **siti**.

4. Selezionare il **sito Web predefinito**, scegliere **impostazioni di base**e impostare il **percorso fisico** al **C:\Publish**.

5. Fare clic con il pulsante destro del mouse sul nodo **Sito Web predefinito** e scegliere **Aggiungi applicazione**.

6. Impostare il **Alias** campo **MyASPApp**, accettare il valore predefinito del Pool di applicazioni (**DefaultAppPool**) e impostare il **percorso fisico** a  **C:\Publish**.

7. Sotto **connessioni**, selezionare **pool di applicazioni**. Aprire **DefaultAppPool** e impostare il campo di pool di applicazioni **ASP.NET v4.0** (ASP.NET 4.5 non è un'opzione per il pool di applicazioni).

8. Il sito selezionato in Gestione IIS, scegliere **Edit Permissions**e assicurarsi che tale account IUSR, IIS_IUSRS o l'utente sia configurato per il Pool di applicazioni è un utente autorizzato con diritti di lettura ed esecuzione. Se nessuno di questi utenti sono presenti, aggiungere IUSR come utente con diritti di lettura ed esecuzione.

## <a name="publish-and-deploy-the-app-using-web-deploy-from-visual-studio"></a>Pubblicare e distribuire l'app tramite distribuzione Web da Visual Studio

[!INCLUDE [deploy-app-web-deploy](../deployment/includes/deploy-app-web-deploy.md)]

Inoltre, potrebbe essere necessario leggere la sezione seguente su come risolvere i problemi di porte.

## <a name="troubleshoot-open-required-ports-on-windows-server"></a>Risoluzione dei problemi: Aprire le porte necessarie in Windows Server

Nella maggior parte delle configurazioni, vengono aperte le porte richieste dall'installazione di ASP.NET e distribuzione Web. Tuttavia, devi verificare che le porte siano aperte.

> [!NOTE]
> In una VM di Azure, è necessario aprire le porte attraverso il [gruppo di sicurezza di rete](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Porte necessarie:

* 80 - required per IIS
* 8172 - richiesto per la distribuzione Web per distribuire l'app da Visual Studio

1. Per aprire una porta in Windows Server, aprire il **avviare** menu, cercare **Windows Firewall con sicurezza avanzata**.

2. Quindi scegliere **regole connessioni in entrata** > **nuova regola** > **porta**. Scegli **successivo** e in **porte locali specifiche**, immettere il numero di porta, fare clic su **successiva**, quindi **Consenti solo connessioni**, fare clic su Avanti, e aggiungere il nome (**IIS**, **distribuzione Web**, o **msvsmon**) per la regola in ingresso.

    Se si desidera visualizzare ulteriori dettagli sulla configurazione di Windows Firewall, vedere [configurare il Firewall di Windows per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Creare regole aggiuntive per le altre porte necessarie.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione è stato creato un file di impostazioni di pubblicazione, viene importato in Visual Studio e distribuita un'app ASP.NET in IIS. È anche possibile distribuire tramite l'importazione delle impostazioni di pubblicazione.

> [!div class="nextstepaction"]
> [Distribuire in IIS tramite l'importazione delle impostazioni di pubblicazione](../deployment/tutorial-import-publish-settings-iis.md)
