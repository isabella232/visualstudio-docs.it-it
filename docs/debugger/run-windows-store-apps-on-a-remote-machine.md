---
title: Eseguire App UWP in un computer remoto | Microsoft Docs
ms.custom: ''
ms.date: 01/05/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 2845057fe970299d249d580d97b557a5ed311fc0
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38795972"
---
# <a name="run-uwp-apps-on-a-remote-machine-in-visual-studio"></a>Eseguire App UWP in un computer remoto in Visual Studio
  
Per eseguire un'app UWP in un computer remoto, è necessario associare ad esso utilizzando Remote Tools per Visual Studio. Remote tools consente di eseguire, debug, profilatura e testare un'app UWP in esecuzione in un dispositivo da un secondo computer che esegue Visual Studio. In esecuzione in un dispositivo remoto può essere particolarmente efficiente quando il computer di Visual Studio non supporta funzionalità specifiche per le app UWP, ad esempio il tocco, georilevazione e orientamento fisico. In questo argomento vengono descritte le procedure per configurare e avviare una sessione remota.

In alcuni scenari, gli strumenti remoti vengono installati automaticamente quando si distribuisce in un dispositivo remoto.

- Per i PC Windows 10 che esegue Creators Update e versioni successive, Strumenti connessione remota verranno installati automaticamente.
- Per i dispositivi Windows 10 Xbox, IOT e HoloLens, remote tools verrà installato automaticamente.
- Per dispositivi mobili Windows 10, è necessario essere fisicamente connessi al telefono, è necessario abilitare [modalità sviluppatore](/windows/uwp/get-started/enable-your-device-for-development) ed è necessario selezionare **dispositivo** come destinazione di debug. Strumenti remoti non sono necessari né supportati.

Per i PC Windows 10 che eseguono la versione di aggiornamento una pre-dell'autore di Windows, è necessario installare remote tools sul computer remoto manualmente il prima di eseguire il debug. Seguire le istruzioni in questo argomento. 
  
##  <a name="BKMK_Prerequisites"></a> Prerequisiti  
 Per eseguire il debug su un dispositivo remoto:  
  
- Il dispositivo remoto e computer di Visual Studio deve essere connesso in rete o collegati direttamente tramite un cavo Ethernet o USB. Il debug tramite Internet non è supportato.  

- È necessario abilitare [modalità sviluppatore](/windows/uwp/get-started/enable-your-device-for-development). 
  
- Per i PC Windows 10 che eseguono una versione precedente a Update Windows 10 Creators di Windows 10, devi [installare ed eseguire i componenti di debug remoti](#BKMK_download).
  
##  <a name="BKMK_Security"></a> Sicurezza  
Per impostazione predefinita **universale (protocollo non crittografato)** viene usato in Windows 10. Questo protocollo deve essere utilizzato solo su reti attendibili. La connessione di debug è protetto da utenti malintenzionati in grado di intercettare e modificare i dati passati tra lo sviluppo e il computer remoto.
  
> [!WARNING]
>  Non vi è alcuna sicurezza di rete quando si imposta la modalità di autenticazione **universale (protocollo non crittografato)** oppure **None**. Scegliere queste modalità solo se si è certi che la rete non è a rischi derivanti da traffico ostile o dannoso.  
  
##  <a name="BKMK_DirectConnect"></a> Come connettersi direttamente tramite un cavo USB 

In Windows 10, è possibile distribuire in un dispositivo USB-connected scegliendo **periferica** invece di **computer remoto** come destinazione di distribuzione (è possibile farlo nel **Standard** sulla barra degli strumenti o nella pagina delle proprietà Debug).

##  <a name="BKMK_ConnectVS"></a> Configurare il progetto di Visual Studio per il debug remoto  
 Specificare il dispositivo remoto a cui è possibile connettersi nelle proprietà del progetto. La procedura varia in base al linguaggio di programmazione. È possibile digitare il nome di rete del dispositivo remoto oppure è possibile selezionarlo dal **connessione remota** nella finestra di dialogo.  
  
 ![Finestra di dialogo Seleziona connessione Debugger remoto](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 Nella finestra di dialogo sono elencati solo i dispositivi che eseguono il debugger remoto presenti sulla subnet locale del computer con installato Visual Studio.  
  
> [!TIP]
>  In caso di problemi di connessione a un dispositivo remoto, provare a immettere l'indirizzo IP del dispositivo. Per determinare l'indirizzo IP di un dispositivo, aprire una finestra di comando e digitare **ipconfig**. L'indirizzo IP è indicato come **IPv4 Address**.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Scegliere il dispositivo remoto per progetti c# e Visual Basic  
  
1.  In Esplora soluzioni seleziona il nome del progetto, quindi scegli **Proprietà** dal menu di scelta rapida.  
  
2.  Selezionare **Debug**.  
  
3.  Scegliere **Computer remoto** dall'elenco **Dispositivo di destinazione** .  
  
4.  Immettere il nome di rete del dispositivo remoto nella casella **Computer remoto** o selezionare **Trova** per scegliere il dispositivo nella finestra di dialogo **Seleziona connessione debugger remoto** . 

    ![Proprietà del progetto per il debug remoto gestito](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Scegliere il dispositivo remoto per progetti JavaScript e C++  
  
1.  In Esplora soluzioni seleziona il nome del progetto, quindi scegli **Proprietà** dal menu di scelta rapida.  
  
2.  Espandere il nodo **Proprietà di configurazione** , quindi selezionare **Debug**.  
  
3.  Scegliere **Debugger remoto** dall'elenco **Debugger da avviare** .  
  
4.  Immettere il nome di rete del dispositivo remoto nella casella **Nome computer** o selezionare la freccia in giù nella casella per scegliere il dispositivo nella finestra di dialogo **Seleziona connessione debugger remoto** .  

    ![C&#43; &#43; le proprietà per il debug remoto di progetto](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")
  
## <a name="BKMK_download"></a> Scaricare e installare gli strumenti remoti (pre-Creators Update)

Se si usa versioni di aggiornamento di una pre-dell'autore di Windows 10, quindi seguire queste istruzioni. In caso contrario, è possibile ignorare questa sezione.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Configurare il debugger remoto

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]  
  
##  <a name="BKMK_RunRemoteDebug"></a> Avviare una sessione di debug remota  
 È possibile avviare, arrestare ed esplorare una sessione di debug remoto come una sessione locale. Nelle versioni di pre-Creators Update di Windows 10, assicurarsi che Remote Debugging Monitor è in esecuzione nel dispositivo remoto.  
  
 Scegliere quindi **Avvia debug** dal menu **Debug** (tastiera: F5). Il progetto viene ricompilato, quindi distribuito e avviato sul dispositivo remoto. Il debugger sospende l'esecuzione in corrispondenza dei punti di interruzione. Nel codice sarà possibile quindi eseguire un'istruzione, eseguire un'istruzione/routine e uscire da un'istruzione/routine. Scegli **Termina debug** per terminare la sessione di debug e chiudere l'app remota.
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni avanzate di distribuzione remoto](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)  
 [Test delle app UWP con Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Eseguire il debug di App in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
