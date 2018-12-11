---
title: Debug remoto di ASP.NET su un remoto con IIS 7.5 Computer | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71d249571830ac608bef12c4a47d0243de1859a5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764077"
---
# <a name="remote-debugging-aspnet-on-a-remote-iis-computer"></a>Debug remoto di ASP.NET in un Computer remoto con IIS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile distribuire un'applicazione Web ASP.NET in un computer Windows Server con IIS e configurarlo per il debug remoto. Questa guida illustra come impostare e configurare un'applicazione di Visual Studio 2015 MVC 4.5.2, distribuirla a IIS e collegare il debugger remoto da Visual Studio.

Queste procedure sono state testate in queste configurazioni di server:
* Windows Server 2012 R2 e IIS 10
* Windows Server 2008 R2 e IIS 7.5

La maggior parte delle informazioni in questo articolo si applica anche al debug remoto un'applicazione ASP.NET Core, ad eccezione del fatto che la distribuzione di App ASP.NET core è diversa e richiede passaggi aggiuntivi. Per distribuire un'app ASP.NET Core in IIS, è necessario completare tutte le sezioni del [questo articolo](https://docs.asp.net/en/latest/publishing/iis.html).

## <a name="prerequisites-install-the-remote-debugger-on-the-windows-server-computer"></a>Prerequisiti: installare il debugger remoto nel computer Windows Server

Per istruzioni su come scaricare il debugger remoto nel computer Windows Server, vedere [debug remoto](../debugger/remote-debugging.md).

Per eseguire il debug remoto delle applicazioni ASP.NET, è possibile eseguire l'applicazione del debugger remoto come amministratore o avviare il debugger remoto come servizio. Informazioni dettagliate su come eseguire il debugger remoto come servizio sono disponibili in [Remote Debugging](../debugger/remote-debugging.md).

Dopo l'installazione, assicurarsi che il debugger remoto è in esecuzione nel computer di destinazione. (In caso contrario, cercare **Remote Debugger** nel **avviare** menu. ) Nella finestra del debugger remoto appare come segue. (4020 è il numero di porta predefinito)

![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
## <a name="create-the-application-on-the-visual-studio-computer"></a>Creare l'applicazione nel computer di Visual Studio  
  
1. Creare una nuova applicazione MVC ASP.NET (**File/Nuovo/Progetto**, quindi selezionare **Visual C#/Web/Applicazione Web ASP.NET** . Nella sezione modelli **ASP.NET 4.5.2** selezionare **MVC**. Verificare che l'opzione **ospita nel Cloud** non è selezionata nella sezione Azure. Denominare il progetto **MyMVC**.)
1. Aprire il file HomeController.cs e impostare un punto di interruzione nel metodo `About()` .
1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Pubblica**.
1. Per **Selezionare una destinazione di pubblicazione**selezionare **Personalizzato** e denominare il profilo **MyMVC**. Scegliere **Avanti**.
1. Nella scheda **Connessione** impostare il campo **Metodo di pubblicazione** su **File System** e il campo **Percorso di destinazione** su una directory locale. Scegliere **Avanti**.

    ![RemoteDBG_Publish_Local](../debugger/media/remotedbg-publish-local.png "RemoteDBG_Publish_Local")
1. Impostare la configurazione su **Debug**. Fare clic su **Pubblica**.

    ![RemoteDBG_Publish_Debug_Config](../debugger/media/remotedbg-publish-debug-config.png "RemoteDBG_Publish_Debug_Config")
    
    L'applicazione verrà pubblicata nella directory locale.

## <a name="BKMK_deploy_asp_net"></a> Distribuire l'applicazione ASP.NET nel computer remoto Windows Server

 In questa sezione si presuppone che il computer Windows Server sia già abilitato IIS. In Windows Server 2012 R2, vedere [configurazione di IIS](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration) per abilitare IIS. (È possibile ignorare altre sezioni di questo articolo, a meno che si sta tentando di distribuire un'app ASP.NET Core. Per ASP.NET Core, seguire i passaggi nell'articolo per distribuire l'app anziché i passaggi descritti di seguito.)
1. Installare i componenti della piattaforma Web per installare ASP.NET 4.5 l'utilizzo di ASP.NET (dal nodo del Server in Windows Server 2012 R2, scegliere **Ottieni nuovi componenti della piattaforma Web** e quindi cercare ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg-iis-aspnet-45.png "RemoteDBG_IIS_AspNet_45")

    In Windows Server 2008 R2, installare ASP.NET 4 invece con il seguente comando: **\v4.0.30319\aspnet_regiis.exe - ir C:\Windows\Microsoft.NET\Framework (64)**
1. Copiare la directory del progetto ASP.NET dal computer di Visual Studio in una directory locale (denominata **C:\Publish**) nel computer Windows Server. È possibile copiare manualmente il progetto, usare Xcopy, Web Deploy, Robocopy, Powershell o altre opzioni.

    > [!CAUTION]
    >  Se è necessario apportare modifiche al codice o ricompilazione, è necessario ripubblicare e ripetere questo passaggio. Il file eseguibile copiato nel computer remoto deve corrispondere esattamente all'origine locale e ai simboli.
1. Assicurarsi che il file web.config riporti la versione corretta di .NET Framework.  Ad esempio, la versione di .NET Framework installata per impostazione predefinita in Windows Server 2008 R2 è 4.0.30319, ma è stato creato un ASP.NET 4.5.2 versione. Se un'app ASP.NET 4.0 è in esecuzione nel computer Windows Server, è necessario modificare la versione:
  
    ```xml
    <system.web>
        <authentication mode="None" />  
        <compilation debug="true" targetFramework="4.0.30319" />
        <httpRuntime targetFramework="4.0.30319" />
      </system.web>
  
    ```
1. Aprire **Gestione Internet Information Services (IIS)** e andare in **Siti**.
1. Fare clic con il pulsante destro del mouse sul nodo **Sito Web predefinito** e scegliere **Aggiungi applicazione**.
1. Impostare il **Alias** campo **MyMVC** e il campo di pool di applicazioni a **ASP.NET v4.0** (ASP.NET 4.5 non è un'opzione per il pool di applicazioni). Impostare il **Percorso fisico** su **C:\Publish** (dove è stata copiata la directory del progetto ASP.NET).

    >[!NOTE] 
    > Per le app ASP.NET Core, impostare il campo di pool di applicazioni **nessun codice gestito**.
1. Testare la distribuzione facendo clic **sito Web predefinito** e selezionare **Sfoglia**.
    Se l'app è stata distribuita correttamente, si verrà visualizzata la pagina web.

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a>Connettersi all'applicazione ASP.NET dal computer di Visual Studio

1. Nel computer di Visual Studio aprire la soluzione **MyMVC** .
1. In Visual Studio, fare clic su **Debug / Connetti a processo** (**Ctrl + Alt + P**).
1. Impostare il campo qualificatore  **\<nome del computer remoto >: 4020**.
1. Fare clic su **Aggiorna**.
    Nella finestra **Processi disponibili** verranno visualizzati alcuni processi.

    Non vengono visualizzati tutti i processi, provare a usare l'indirizzo IP anziché il nome del computer remoto (la porta è obbligatoria). Usare `ipconfig` in una riga di comando per ottenere l'indirizzo IPv4.
1. Selezionare  **Mostra i processi di tutti gli utenti**.
1. Cercare **w3wp.exe** e fare clic su **Connetti**.

     Per trovare rapidamente il nome del processo, digitare la prima lettera del processo.
     
    >[!NOTE]
    > Per un'app ASP.NET Core, scegliere il processo dnx.exe invece di w3wp.exe. (Il nome del processo può cambiare in una versione futura).

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")

1. Aprire il sito Web del computer remoto. In un browser, passare a **http://\<nome del computer remoto >**.
    
    Verrà visualizzata la pagina Web ASP.NET.
1. Nella pagina web ASP.NET, fare clic sul collegamento per il **sulle** pagina.

    Il punto di interruzione verrà raggiunto in Visual Studio.



