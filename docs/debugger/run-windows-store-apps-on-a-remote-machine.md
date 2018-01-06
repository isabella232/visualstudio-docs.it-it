---
title: Eseguire App UWP in un computer remoto | Documenti Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: "43"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: ebae0886db71b0b06f346d6bd174951b1c5d4752
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="run-uwp-apps-on-a-remote-machine"></a>Eseguire App UWP in un computer remoto
![Si applica solo a Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
Per eseguire un'app UWP in un computer remoto, è necessario collegare utilizzando Visual Studio Remote Tools. Remote Tools consentono di eseguire, eseguire il debug, profilare e testare un'app UWP in esecuzione in un dispositivo da un secondo computer che esegue Visual Studio. Esecuzione in un dispositivo remoto può essere particolarmente efficiente quando il computer di Visual Studio non supporta funzionalità specifiche per le app UWP, ad esempio tocco, la georilevazione e orientamento fisico. In questo argomento vengono descritte le procedure per configurare e avviare una sessione remota.

In alcuni scenari, gli strumenti remoti vengono installati automaticamente quando si distribuisce in un dispositivo remoto.

- Per i PC Windows 10 esegue creatori di aggiornamento e versioni successive, vedere [eseguire il Debug di un pacchetto dell'App installato](debug-installed-app-package.md#remote). Strumenti connessione remota verranno installati automaticamente.
- Per i dispositivi Windows 10 Xbox, IOT e HoloLens, vedere [eseguire il Debug di un pacchetto dell'App installato](debug-installed-app-package.md#remote). Strumenti connessione remota verranno installati automaticamente.
- Per Windows Phone, è necessario essere fisicamente connessi al telefono, è necessario installare un [licenza per sviluppatori](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh974578.aspx) (Windows Phone 8 e 8.1) o abilitare [modalità sviluppatore](/windows/uwp/get-started/enable-your-device-for-development) (Windows Mobile 10), ed è necessario Selezionare **dispositivo** come destinazione di debug. Strumenti remoti non necessari o supportati.

Per i PC Windows 8.1 e versione di aggiornamento di una pre-del creatore di Windows i PC Windows 10, è necessario installare remote tools sul computer remoto manualmente il prima di poter eseguire il debug. Seguire le istruzioni in questo argomento.
  
##  <a name="BKMK_Prerequisites"></a> Prerequisiti  
 Per eseguire il debug su un dispositivo remoto:  
  
-   Il dispositivo remoto e il computer che esegue Visual Studio devono essere connessi in rete o collegati direttamente tramite un cavo Ethernet. Il debug tramite Internet non è supportato.  

- Per lo sviluppo, è necessario abilitare il dispositivo remoto.

    - Per i dispositivi Windows 8 e Windows 8.1, una [licenza per sviluppatori](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh974578.aspx) deve essere installato nel dispositivo remoto.
    - Per i dispositivi Windows 10, è necessario abilitare [modalità sviluppatore](/windows/uwp/get-started/enable-your-device-for-development). 
  
-   Per i PC Windows 10 in esecuzione una versione precedente a aggiornamento del Windows 10 creatore di Windows 10, è necessario installare ed eseguire i componenti di debug remoti.
  
-   È necessario essere un amministratore del dispositivo remoto per configurare il firewall durante l'installazione. È necessario disporre dell'accesso utente sul dispositivo remoto per connetterti al debugger remoto o eseguirlo.  
  
##  <a name="BKMK_Security"></a> Sicurezza  
 Per impostazione predefinita, il debugger remoto utilizza l'autenticazione di Windows.  
  
> [!WARNING]
>  È inoltre possibile scegliere di eseguire il debugger remoto in modalità Nessuna autenticazione che, tuttavia, è fortemente sconsigliata perché priva di qualsiasi sicurezza di rete. Scegliere la modalità Nessuna autenticazione solo se si ha la certezza che la rete non è soggetta a rischi derivanti da traffico ostile o dannoso.  
  
##  <a name="BKMK_DirectConnect"></a> Come connettersi direttamente a un dispositivo remoto  
 Per connettersi direttamente a un dispositivo remoto, collegare il computer che esegue Visual Studio al dispositivo tramite un cavo Ethernet standard. Se il dispositivo non dispone di una porta Ethernet, è possibile utilizzare un adattatore da USB a Ethernet per il collegamento al cavo.  
  
## <a name="BKMK_download"></a>Scaricare e installare Remote Tools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
## <a name="BKMK_setup"></a>Impostare il debugger remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]
  
##  <a name="BKMK_ConnectVS"></a> Configurazione del progetto di Visual Studio per il debug remoto  
 Specificare il dispositivo remoto a cui è possibile connettersi nelle proprietà del progetto. La procedura varia in base al linguaggio di programmazione. Puoi digitare il nome di rete del dispositivo remoto o selezionarlo nella finestra di dialogo Seleziona connessione debugger remoto.  
  
 ![Finestra di dialogo Seleziona connessione Debugger remoto](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 Nella finestra di dialogo sono elencati solo i dispositivi che eseguono il debugger remoto presenti sulla subnet locale del computer con installato Visual Studio.  
  
> [!TIP]
>  In caso di problemi di connessione a un dispositivo remoto, provare a immettere l'indirizzo IP del dispositivo. Per determinare l'indirizzo IP di un dispositivo, aprire una finestra di comando e digitare **ipconfig**. L'indirizzo IP è indicato come **IPv4 Address**.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Scelta del dispositivo remoto per progetti C# e Visual Basic  
 ![Proprietà del progetto per il debug remoto gestito](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1.  In Esplora soluzioni seleziona il nome del progetto, quindi scegli **Proprietà** dal menu di scelta rapida.  
  
2.  Selezionare **Debug**.  
  
3.  Scegliere **Computer remoto** dall'elenco **Dispositivo di destinazione** .  
  
4.  Immettere il nome di rete del dispositivo remoto nella casella **Computer remoto** o selezionare **Trova** per scegliere il dispositivo nella finestra di dialogo **Seleziona connessione debugger remoto** .  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Scelta del dispositivo remoto per progetti JavaScript e C++  
 ![C &#43; &#43; le proprietà per il debug remoto di progetto](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1.  In Esplora soluzioni seleziona il nome del progetto, quindi scegli **Proprietà** dal menu di scelta rapida.  
  
2.  Espandere il nodo **Proprietà di configurazione** , quindi selezionare **Debug**.  
  
3.  Scegliere **Debugger remoto** dall'elenco **Debugger da avviare** .  
  
4.  Immettere il nome di rete del dispositivo remoto nella casella **Nome computer** o selezionare la freccia in giù nella casella per scegliere il dispositivo nella finestra di dialogo **Seleziona connessione debugger remoto** .  
  
##  <a name="BKMK_RunRemoteDebug"></a> Esecuzione di una sessione di debug remoto  
 È possibile avviare, arrestare ed esplorare una sessione di debug remoto come una sessione locale. Prima di avviare il debug, assicurarsi che Remote Debugging Monitor sia in esecuzione sul dispositivo remoto.  
  
 Scegliere quindi **Avvia debug** dal menu **Debug** (tastiera: F5). Il progetto viene ricompilato, quindi distribuito e avviato sul dispositivo remoto. Il debugger sospende l'esecuzione in corrispondenza dei punti di interruzione. Nel codice sarà possibile quindi eseguire un'istruzione, eseguire un'istruzione/routine e uscire da un'istruzione/routine. Scegli **Termina debug** per terminare la sessione di debug e chiudere l'app remota. Per ulteriori informazioni, vedere [Debug delle App in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Test delle app UWP con Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Debug delle App in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)