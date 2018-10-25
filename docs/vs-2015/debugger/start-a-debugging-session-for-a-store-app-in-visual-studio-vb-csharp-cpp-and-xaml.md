---
title: Avviare una sessione di debug per un'app di Store in Visual Studio (VB, c#, C++ e XAML) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.IVCAppHostRemoteDebugPageObject.MachineName
- VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType
- VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType
- ImmersiveProjects.Properties.Debug
- VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback
- AppPackage.Properties.Debug
- VC.Project.IVCAppHostRemoteDebugPageObject.Authentication
- VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 66ec0e79-8261-4c19-a618-3fd1b3f71bbd
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c667bdc47cbed95643a6b2a5637d0d63748c84cf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49927320"
---
# <a name="start-a-debugging-session-for-a-store-app-in-visual-studio-vb-c-c-and-xaml"></a>Avviare una sessione di debug per un'app dello Store in Visual Studio (VB, C#, C++ e XAML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si applica a Windows e Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  

 In questo argomento viene descritto come avviare una sessione di debug per le app di Store scritte in XAML, Visual C++, Visual C# o Visual Basic. Il debug di un'app comporta sia la configurazione della la sessione di debug che la scelta della modalità di avvio dell'app.  

> [!NOTE]
>  Per le app scritte in JavaScript e HTML Vedi [avviare una sessione di debug (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md).  

##  <a name="BKMK_In_this_topic"></a> In questo argomento  
 [Il modo più semplice per avviare il debug](#BKMK_The_easy_way_to_start_debugging)  

 [Configurare la sessione di debug](#BKMK_Configure_the_debugging_session)  

- [Aprire la pagina delle proprietà di debug per il progetto](#BKMK_Open_the_debugging_property_page_for_the_project)  

- [Scegliere le opzioni di configurazione della compilazione](#BKMK_Choose_the_build_configuration_options)  

- [Scegliere la destinazione di distribuzione](#BKMK_Choose_the_deployment_target)  

- [Scegliere il debugger da utilizzare](#BKMK_Choose_the_debugger_to_use)  

- [(Facoltativo) Ritardare l'avvio della sessione di debug](#BKMK__Optional__Delay_starting_the_debug_session)  

- [(Facoltativo) Disabilitare i loopback di rete](#BKMK__Optional__Disable_network_loopbacks)  

- [(Facoltativo) Reinstallare l'app all'avvio del debug](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)  

- [(Facoltativo) Disabilitare il requisito di autenticazione per avviare il debugger remoto](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)  

  [Avviare la sessione di debug](#BKMK_Start_the_debugging_session)  

- [Avviare i debug (F5)](#BKMK_Start_debugging__F5_)  

- [Avviare il debug (F5) ma ritardare l'avvio dell'app](#BKMK_Start_debugging__F5__but_delay_the_app_start)  

- [Avviare un'app installata nel debugger](#BKMK_Start_an_installed_app_in_the_debugger)  

- [Collegare il debugger a un'app in esecuzione](#BKMK_Attach_the_debugger_to_a_running_app_)  

  -   [Impostare l'esecuzione dell'app in modalità debug](#BKMK_Set_the_app_to_run_in_debug_mode)  

  -   [Collegare il debugger](#BKMK_Attach_the_debugger)  

##  <a name="BKMK_The_easy_way_to_start_debugging"></a> Il modo più semplice per avviare il debug  

1. Apri la soluzione dell'app in Visual Studio.  

2. Premere F5.  

   Visual Studio compila e avvia l'app con il debugger collegato. L'esecuzione continua fino a raggiungere un punto di interruzione. Sospendi manualmente l'esecuzione e si verifica un'eccezione non gestita o l'app termina. Per altre informazioni, vedere [esplorare una sessione di debug (Xaml e c#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md) .  

##  <a name="BKMK_Configure_the_debugging_session"></a> Configurare la sessione di debug  

###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Aprire la pagina delle proprietà di debug per il progetto  

1.  Selezionare il progetto in Esplora soluzioni. Scegli **Proprietà**dal menu di scelta rapida.  

2.  In questo modo si apre la pagina delle proprietà di debug per il progetto:  

    -   Per le app Visual C# e Visual Basic scegli **Debug**.  

         ![C&#35; &#47; pagina delle proprietà debug progetto VB](../debugger/media/dbg-csvb-debugpropertypage.png "DBG_CsVb_DebugPropertyPage")  

    -   Per le app Visual C++ espandi il nodo **Proprietà di configurazione**  , quindi scegli **Debug**.  

         ![C&#43; &#43; app di Windows Store pagina delle proprietà di debug](../debugger/media/dbg-cpp-debugpropertypage.png "DBG_CPP_DebugPropertyPage")  

###  <a name="BKMK_Choose_the_build_configuration_options"></a> Scegliere le opzioni di configurazione della compilazione  

1.  Dall'elenco **Configurazione** scegli **Debug** o **Debug (attivo)**.  

2.  Dall'elenco **Piattaforma** seleziona la piattaforma di destinazione per cui eseguire la compilazione. Nella maggior parte dei casi, **Qualsiasi CPU** (**Tutte le piattaforme** in Visual C++) rappresenta la scelta ottimale.  

###  <a name="BKMK_Choose_the_deployment_target"></a> Scegliere la destinazione di distribuzione  
 ![Si applica solo a Windows](../debugger/media/windows-only-content.png "windows_only_content")  

 Puoi distribuire ed eseguire il debug di un'app di Windows Store nel computer che esegue Visual Studio, nel simulatore di Visual Studio sul computer locale o in un dispositivo remoto.  

- Per le app Visual Basic e C# scegli la destinazione dall'elenco **Dispositivo di destinazione** nella pagina delle proprietà **Debug** del progetto.  

- Per le app C++ scegli la destinazione dall'elenco **Debugger da avviare** nella pagina delle proprietà **Debug** :  

  Scegli una delle seguenti opzioni:  

|||  
|-|-|  
|**Computer locale**|Esegue il debug dell'app nella sessione corrente nel computer locale. Visualizzare [Run Windows Store app nel computer locale](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
|**Simulatore**|Esegue il debug dell'app nel simulatore di Visual Studio per le app in [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] . Il simulatore è una finestra del desktop che consente di eseguire il debug delle funzionalità del dispositivo, ad esempio i movimenti tocco e la rotazione del dispositivo, che non sono disponibile nel computer locale. Visualizzare [Run Windows Store app nel simulatore](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Computer remoto**|Esegue il debug dell'app in un dispositivo connesso al computer locale su una rete Intranet o collegato direttamente tramite un cavo Ethernet. Per eseguire il debug in modalità remota, Visual Studio Remote Tools deve essere installato e in esecuzione sul dispositivo remoto. Visualizzare [Run Windows Store App in un computer remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  

 Se scegli **Computer remoto**, specifica il nome o l'indirizzo IP del computer remoto nei modi seguenti:  

- Immetti il nome o l'indirizzo IP del computer remoto.  

  -   Per le app C# e Visual Basic, immetti il nome o l'indirizzo IP nella casella **Computer remoto** .  

  -   Per le app C++, immetti il nome o l'indirizzo IP nella casella **Nome computer** .  

- Scegli il computer remoto nella finestra di dialogo **Seleziona connessione debugger remoto** .  

   Per aprire la finestra di dialogo:  

  - Per le app C# e Visual Basic scegli **Trova**.  

  - Per le app C++, scegliere la freccia verso il basso nella **nome macchina** e selezionare  **\<trova... >**.  

    ![Finestra di dialogo Seleziona connessione Debugger remoto](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  

  > [!NOTE]
  >  Nella finestra di dialogo **Seleziona connessione debugger remoto** sono visualizzati i computer sulla subnet locale e i computer collegati direttamente al computer che esegue Visual Studio tramite un cavo Ethernet. Per specificare un altro computer, immetti il nome nella casella **Nome computer** .  

  ![Si applica solo a Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")  

  Puoi distribuire un'app di Windows Phone Store ed eseguirne il debug in un dispositivo o in uno degli emulatori del telefono di Visual Studio. Seleziona il dispositivo o l'emulatore nell'elenco **Dispositivo di destinazione** .  

###  <a name="BKMK_Choose_the_debugger_to_use"></a> Scegliere il debugger da utilizzare  
 Per impostazione predefinita, Visual Studio esegue il debug del codice gestito nelle app Visual Basic e C#.  

 Per le applicazioni C# e Visual Basic puoi scegliere di eseguire il debug di codice nativo e gestito C/C++ nell'app. Seleziona la casella di controllo **Abilita debug codice non gestito** per includere il codice nativo nella sessione di debug.  

 Per impostazione predefinita, Visual Studio esegue il debug del codice nativo nell'app C++.  

 Per le app C++, puoi scegliere di eseguire il debug dei tipi di codice specifici presenti nei componenti dell'app al posto o in aggiunta al codice nativo. Specifica il codice per cui eseguire il debug nell'elenco **Tipo di debugger** nella pagina delle proprietà **Debug** del progetto dell'app.  

 Scegli uno di questi debugger dall'elenco **Processo applicativo** :  

|||  
|-|-|  
|**Solo script**|Esegue il debug del codice JavaScript nell'app. Il codice gestito e il codice nativo vengono ignorati.|  
|**Solo nativo**|Esegue il debug del codice C/C++ nativo nell'app. Il codice gestito e il codice JavaScript vengono ignorati.|  
|**Solo gestito**|Esegue il debug del codice gestito nell'app. Il codice JavaScript e il codice C/C++ nativo vengono ignorati.|  
|**Misto (gestito e nativo)**|Esegue il debug sia del codice C++ nativo e del codice gestito nell'app. Il codice JavaScript viene ignorato.|  
|**Solo GPU**|Esegue il debug del codice C++ nativo eseguito su un'unità di elaborazione grafica (GPU).|  

 ![Si applica solo a Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")  

 Per le app di Windows Store Phone, puoi anche scegliere il debugger da usare per i processi in background in **Processo attività in background**.  

###  <a name="BKMK__Optional__Delay_starting_the_debug_session"></a> (Facoltativo) Ritardare l'avvio della sessione di debug  
 Per impostazione predefinita, Visual Studio avvia immediatamente l'app quando avvii il debug. Puoi anche avviare una sessione di debug ma ritardare l'avvio dell'app. Quando scegli questa opzione, l'app viene aperta nel debugger quando viene avviata dalla schermata Start o tramite un contratto di attivazione oppure quando viene avviata da un altro processo o metodo. Puoi ritardare l'avvio dell'app anche quando vuoi eseguire il debug di un'attività in background mentre l'app stessa non è in esecuzione.  

 Per ritardare l'avvio dell'app, puoi procedere come segue:  

-   Per le app Visual C# e Visual Basic seleziona **Non eseguire il codice utente, ma eseguine il debug all'avvio** nella pagina delle proprietà **Debug** .  

-   Per le app Visual C++ scegli **Sì** dall'elenco **Avvia applicazione** nella pagina delle proprietà **Debug** .  

###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> (Facoltativo) Disabilitare i loopback di rete  
 ![Si applica solo a Windows](../debugger/media/windows-only-content.png "windows_only_content")  

 Per motivi di sicurezza, a un'app di Windows Store installata in modalità standard non è consentito effettuare chiamate di rete al dispositivo in cui è installata. Per impostazione predefinita, la distribuzione di Visual Studio crea una esenzione da questa regola per l'app distribuita. Questa esenzione ti consente di verificare le procedure di comunicazione in un singolo computer. Prima di inviare l'app a Windows Store, dovrai testare l'app senza l'esenzione.  

 Per rimuovere l'esenzione relativa al loopback della rete:  

-   Per le app Visual C# e Visual Basic, deseleziona la casella di controllo **Consenti loopback della rete locale** nella pagina delle proprietà **Debug** .  

-   Per le app Visual C++ scegli **No** dall'elenco **Consenti loopback della rete locale** nella pagina delle proprietà **Debug** .  

###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> (Facoltativo) Reinstallare l'app all'avvio del debug  
 Per diagnosticare i problemi di installazione e configurazione iniziale dell'app in Visual C# o Visual Basic, scegli **Disinstalla e reinstalla il pacchetto** nella pagina delle proprietà **Debug**  per ricreare un'installazione originale all'avvio del debug. Questa opzione non è disponibile per i progetti Visual C++.  

###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> (Facoltativo) Disabilitare il requisito di autenticazione per avviare il debugger remoto  
 ![Si applica solo a Windows](../debugger/media/windows-only-content.png "windows_only_content")  

 Per impostazione predefinita, è necessario fornire le credenziali per eseguire il debugger remoto.  

> [!IMPORTANT]
>  È possibile scegliere di eseguire il debugger remoto in modalità Nessuna autenticazione che, tuttavia, è fortemente sconsigliata perché priva di qualsiasi sicurezza di rete. Scegliere la modalità Nessuna autenticazione solo se si ha la certezza che la rete non è soggetta a rischi derivanti da traffico ostile o dannoso.  

 Per rimuovere il requisito di autenticazione:  

1. Per le app Visual C# e Visual Basic, deseleziona la casella di controllo **Usa autenticazione** nella pagina delle proprietà **Debug** .  

2. Per le app Visual C++ scegli **No** dall'elenco **Richiedi autenticazione** nella pagina delle proprietà **Debug** .  

   [In questo argomento](#BKMK_In_this_topic)  

##  <a name="BKMK_Start_the_debugging_session"></a> Avviare la sessione di debug  

###  <a name="BKMK_Start_debugging__F5_"></a> Avviare i debug (F5)  
 Quando si sceglie **Avvia debug** (tastiera: F5) nella **Debug** menu, Visual Studio avvia l'app con il debugger collegato. L'esecuzione continua fino a raggiungere un punto di interruzione. Sospendi manualmente l'esecuzione e si verifica un'eccezione o l'app termina.  

###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Avviare il debug (F5) ma ritardare l'avvio dell'app  
 Puoi impostare l'app per l'esecuzione in modalità di debug, ma avviarla con un metodo diverso dal debugger. Ad esempio, puoi decidere di eseguire il debug dell'avvio dell'app dal menu Start o di eseguire il debug di un processo in background nell'app senza avviare l'app. Per ritardare l'avvio dell'app, procedi come indicato di seguito:  

- Nella pagina delle proprietà **Debug** dell'app (**Debug** in Visual C++)  

  -   Per le app Visual C# e Visual Basic, scegli **Non eseguire il codice utente, ma eseguine il debug all'avvio**.  

  -   Per le app Visual C++ scegli **Sì** dall'elenco **Avvia applicazione** .  

- Scegli **Avvia debug** nel **eseguire il Debug** menu (tastiera: F5).  

- Avvia l'app dal menu Start, da un contratto di esecuzione o da un'altra routine.  

  L'app viene avviata in modalità debug. L'esecuzione continua fino a raggiungere un punto di interruzione. Sospendi manualmente l'esecuzione e si verifica un'eccezione non gestita o l'app termina.  

  . Per altre informazioni sul debug di attività in background, vedere [Trigger di sospensione, ripresa e background eventi per Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  

###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Avviare un'app installata nel debugger  
 Quando avvii il debug utilizzando F5, Visual Studio compila e distribuisce l'app, la imposta per l'esecuzione in modalità debug, quindi la avvia. Per avviare un'app già installata in un dispositivo, utilizza la finestra di dialogo Debug pacchetto applicazione installato. Questa è una procedura utile per il debug di un'app installata da Windows Store o quando disponi dei file di origine dell'app, ma non di un progetto di Visual Studio per l'app. Ad esempio, potresti disporre di un sistema di compilazione personalizzato che non utilizza progetti o soluzioni di Visual Studio.  

 L'app può essere installata nel dispositivo locale oppure in un dispositivo remoto.  Puoi avviare l'app immediatamente oppure impostarla per l'esecuzione nel debugger quando viene avviata da un altro processo o metodo, ad esempio dal menu Start o da un contratto di attivazione. Puoi anche impostarne l'esecuzione in modalità debug per eseguire il debug di un processo in background senza avviare l'app. Per altre informazioni, vedere [Trigger di sospensione, ripresa e background eventi per Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  

 Per impostare l'esecuzione di un'app installata in modalità debug, procedi come indicato di seguito:  

> [!NOTE]
>  L'app non deve essere in esecuzione all'avvio della procedura.  

1. Scegli **Debug pacchetto applicazione installato** dal menu **Debug pacchetto applicazione installato Installed App Package**.  

2. Scegli una delle opzioni seguenti dall'elenco:  


   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Computer locale**  |                                                                                                                Esegue il debug dell'app nella sessione corrente nel computer locale. Visualizzare [Run Windows Store app nel computer locale](../debugger/run-windows-store-apps-on-the-local-machine.md).                                                                                                                 |
   |   **Simulatore**    | Esegue il debug dell'app nel simulatore di Visual Studio per le app in [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] . Il simulatore è una finestra del desktop che consente di eseguire il debug delle funzionalità del dispositivo, ad esempio i movimenti tocco e la rotazione del dispositivo, che non sono disponibile nel computer locale. Visualizzare [Run Windows Store app nel simulatore](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Computer remoto** |                          Esegue il debug dell'app in un dispositivo connesso al computer locale su una rete Intranet o collegato direttamente tramite un cavo Ethernet. Per eseguire il debug in modalità remota, Visual Studio Remote Tools deve essere installato e in esecuzione sul dispositivo remoto. Visualizzare [Run Windows Store App in un computer remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |


3. Scegli l'app dall'elenco **Pacchetti applicazione installati** .  

4. Scegli il motore di debug da utilizzare dall'elenco **Esegui il debug di questi tipi di codice** .  

5. (Facoltativo) Scegli **Non eseguire il codice utente, ma eseguine il debug all'avvio** per il debug dell'app all'avvio tramite un altro metodo o per il debug di un processo in background.  

   Quando fai clic su **Start**l'app viene avviata o impostata per l'esecuzione in modalità debug.  

###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Collegare il debugger a un'app in esecuzione  
 Per collegare il debugger a un'app in [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , devi utilizzare Debuggable Package Manager per impostare l'esecuzione dell'app in modalità debug. Debuggable Package Manager viene installato con Visual Studio Remote Tools.  

 Il collegamento del debugger a un'app è utile quando devi eseguire il debug di un'app già installata, ad esempio un'app installata da [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]. Il collegamento è necessario quando disponi dei file di origine dell'app, ma non di un progetto di Visual Studio per l'app. Ad esempio, potresti disporre di un sistema di compilazione personalizzato che non utilizza progetti o soluzioni di Visual Studio.  

 Per collegare il debugger a un'app devi eseguire questi passaggi:  

1.  Imposta l'esecuzione dell'app in modalità debug. Questa operazione deve essere effettuata quando l'app non è in esecuzione.  

2.  Avvia l'app. Puoi avviare l'app dalla schermata Start, da un contratto di esecuzione o tramite un altro metodo.  

3.  Collega il debugger all'app in esecuzione.  

####  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Impostare l'esecuzione dell'app in modalità debug  

1.  Installa Visual Studio Remote Tools sul dispositivo in cui è installata l'app. Vedere [Installazione di Strumenti remoti](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).  

2.  Nella schermata Start cerca `Debuggable Package Manager` e avvialo.  

     Viene visualizzata una finestra di PowerShell correttamente configurata per il cmdlet AppxDebug.  

3.  Per abilitare il debug di un'app, devi specificare l'identificatore PackageFullName dell'app. Per visualizzare un elenco di tutte le app che includono PackageFullName, digita `Get-AppxPackage` al prompt di PowerShell.  

4.  Al prompt di PowerShell immetti `Enable-AppxDebug` *PackageFullName* in cui *PackageFullName* è l'identificatore PackageFullName dell'app.  

####  <a name="BKMK_Attach_the_debugger"></a> Collegare il debugger  
 Per collegare il debugger:  

1. Scegliere **Connetti a processo** dal menu **Debug**.  

    Verrà visualizzata la finestra di dialogo **Connetti a processo** .  

2. Per connetterti a un'app in un dispositivo remoto, specifica il dispositivo remoto nella casella **Qualificatore** . È possibile:  

   -   Immetti il nome nella casella **Qualificatore** .  

   -   Fai clic sulla freccia in giù nella casella **Qualificatore** , quindi scegli il dispositivo da un elenco di dispositivi collegati precedentemente.  

   -   Scegli **Trova** per selezionare il dispositivo da un elenco di dispositivi sulla subnet locale.  

3. Specifica il tipo di codice di cui vuoi eseguire il debug nella casella **Connetti a** .  

    Scegli **Seleziona** , quindi effettua una delle seguenti operazioni:  

   -   Scegli **Determina automaticamente il tipo di codice di cui eseguire il debug**.  

   -   Scegli **Esegui il debug di questi tipi di codice** , quindi scegli uno o più tipi dall'elenco.  

4. Nell'elenco **Processi disponibili**  scegli il processo dell'app.  

5. Scegliere **Connetti**.  

   Visual Studio collega il debugger al processo. L'esecuzione continua fino a raggiungere un punto di interruzione. Sospendi manualmente l'esecuzione e si verifica un'eccezione non gestita o l'app termina.  

   [In questo argomento](#BKMK_In_this_topic)  

## <a name="see-also"></a>Vedere anche  
 [Debug apps in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Esplorare una sessione di debug (Xaml e C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)



