---
title: Avviare una sessione di debug per le app di Store in Visual Studio (JavaScript) | Microsoft Docs
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
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: fb91203f-2cf4-44d3-8ed9-93bc5aaa50b8
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 887914eb88387e5185d30f304587a9e62c43dcca
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748399"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>Avviare una sessione di debug per le app dello Store in Visual Studio (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si applica a Windows e Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  

 Questo argomento descrive come avviare una sessione di debug per app Windows Store scritte in JavaScript e HTML5. Puoi avviare il debug con una sola sequenza di tasti oppure puoi configurare la sessione di debug per scenari specifici e poi scegliere il modo in cui avviare l'app.  

> [!NOTE]
>  Per le app scritte in XAML e Visual c#, Visual C++ o Visual Basic, vedere [avviare una sessione di debug (VB, c#, C++ e XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  

##  <a name="BKMK_In_this_topic"></a> In questo argomento  
 [In questo argomento](#BKMK_In_this_topic)  

 [Il modo più semplice per avviare il debug](#BKMK_The_easy_way_to_start_debugging)  

 [Configurare la sessione di debug](#BKMK_Configure_the_debugging_session)  

- [Aprire la pagina delle proprietà di debug per il progetto](#BKMK_Open_the_debugging_property_page_for_the_project)  

- [Scegliere le opzioni di configurazione della compilazione](#BKMK_Choose_the_build_configuration_options)  

- [Scegliere la destinazione di distribuzione](#BKMK_Choose_the_deployment_target)  

- [Scegliere il debugger da utilizzare](#BKMK_Choose_the_debugger_to_use)  

- [(Facoltativo) Ritardare l'avvio dell'app nella sessione di debug](#BKMK__Optional__Delay_starting_app_in_the_debug_session)  

- [(Facoltativo) Disabilitare i loopback di rete](#BKMK__Optional__Disable_network_loopbacks)  

  [Avviare la sessione di debug](#BKMK_Start_the_debugging_session)  

- [Avviare i debug (F5)](#BKMK_Start_debugging__F5_)  

- [Avviare il debug (F5) ma ritardare l'avvio dell'app](#BKMK_Start_debugging__F5__but_delay_the_app_start)  

  [Avviare un'app installata nel debugger](#BKMK_Start_an_installed_app_in_the_debugger)  

  [Collegare il debugger a un'app in esecuzione](#BKMK_Attach_the_debugger_to_a_running_app_)  

- [Impostare l'esecuzione dell'app in modalità debug](#BKMK_Set_the_app_to_run_in_debug_mode)  

- [Collegare il debugger](#BKMK_Attach_the_debugger)  

##  <a name="BKMK_The_easy_way_to_start_debugging"></a> Il modo più semplice per avviare il debug  
 ![Si applica solo a Windows](../debugger/media/windows-only-content.png "windows_only_content")  

1. Apri la soluzione dell'app in Visual Studio.  

2. Se la soluzione contiene progetti sia per app Windows Store sia per app Windows Store Phone, assicurati che il progetto di cui vuoi eseguire il debug sia il progetto di avvio. In Esplora soluzioni, selezionare il progetto e quindi scegliere **imposta come progetto di avvio** dal menu di scelta rapida.  

3. Premere F5.  

   ![Si applica solo a Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")  

   Visual Studio compila e avvia l'app con il debugger collegato. L'esecuzione continua fino a raggiungere un punto di interruzione. Sospendi manualmente l'esecuzione e si verifica un'eccezione non gestita o l'app termina. Per altre informazioni, vedere [Guida introduttiva: eseguire il Debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md).  

##  <a name="BKMK_Configure_the_debugging_session"></a> Configurare la sessione di debug  
 Dato che lo script non è compilato, sono escluse le impostazioni relative a configurazione e piattaforma di compilazione. Se si esegue il debug di un componente C++ o gestito, impostare il **Configuration** a **Debug** scegliere la piattaforma di destinazione dal **configurazione** finestra di dialogo.  

###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Aprire la pagina delle proprietà di debug per il progetto  

1.  Selezionare il progetto in Esplora soluzioni. Scegli **Proprietà**dal menu di scelta rapida.  

2.  Espandere la **le proprietà di configurazione** nodo, quindi **debug**  

###  <a name="BKMK_Choose_the_build_configuration_options"></a> Scegliere le opzioni di configurazione della compilazione  

1.  Dall'elenco **Configurazione** scegli **Debug** o **Debug (attivo)**.  

2.  Dall'elenco **Piattaforma** seleziona la piattaforma di destinazione per cui eseguire la compilazione. Nella maggior parte dei casi **qualsiasi CPU** è la scelta migliore.  

###  <a name="BKMK_Choose_the_deployment_target"></a> Scegliere la destinazione di distribuzione  
 Puoi distribuire ed eseguire il debug di un'app nel computer Visual Studio, nel simulatore di Visual Studio sul computer locale o in un computer remoto. Scegli la destinazione di **Debugger da avviare** elenco le **debug** pagina delle proprietà per il progetto.  

 ![Si applica solo a Windows](../debugger/media/windows-only-content.png "windows_only_content")  

 Per un'app Windows Store, scegli una di queste opzioni dal **dispositivo di destinazione** elenco:  

|||  
|-|-|  
|**Computer locale**|Esegue il debug dell'app nella sessione corrente nel computer locale. Visualizzare [Run Windows Store app nel computer locale](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
|**Simulatore**|Esegue il debug dell'app nel simulatore di Visual Studio per le app in [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] . Il simulatore è una finestra del desktop che consente di eseguire il debug delle funzionalità del dispositivo, ad esempio i movimenti tocco e la rotazione del dispositivo, che non sono disponibile nel computer locale. Visualizzare [Run Windows Store app nel simulatore](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Computer remoto**|Esegue il debug dell'app in un dispositivo connesso al computer locale su una rete Intranet o collegato direttamente tramite un cavo Ethernet. Per eseguire il debug in modalità remota, Visual Studio Remote Tools deve essere installato e in esecuzione sul dispositivo remoto. Visualizzare [Run Windows Store App in un computer remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  

 Se scegli **Computer remoto**, specifica il nome o l'indirizzo IP del computer remoto nei modi seguenti:  

- Immettere il nome o indirizzo IP del computer in remoto il **nome macchina** casella.  

- Scegliere la freccia in giù la **nome macchina** e selezionare  **\<trova... >**. Scegliere quindi il computer remoto nella **Seleziona connessione Debugger remoto** nella finestra di dialogo.  

   ![Seleziona connessione Debugger remoto](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")  

  > [!NOTE]
  >  Nella finestra di dialogo Seleziona connessione debugger remoto sono visualizzati i computer sulla subnet locale e i computer collegati direttamente al computer che esegue Visual Studio tramite un cavo Ethernet. Per specificare un altro computer, immetti il nome nella casella **Nome computer** .  

  ![Si applica solo a Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")  

  Per un'app Windows Store Phone, scegli **periferica** o uno degli emulatori nel **dispositivo di destinazione** elenco.  

###  <a name="BKMK_Choose_the_debugger_to_use"></a> Scegliere il debugger da utilizzare  
 Per impostazione predefinita, il debugger viene collegato al codice JavaScript nell'app. Puoi scegliere di eseguire il debug del codice gestito e C++ nativo dei componenti dell'app invece che del codice JavaScript. Specifica il codice per cui eseguire il debug nell'elenco **Tipo di debugger** nella pagina delle proprietà **Debug** del progetto dell'app.  

 Scegliere uno di questi debugger dal **tipo di Debugger** elenco:  

|||  
|-|-|  
|**Solo script**|Esegue il debug del codice JavaScript nell'app. Il codice gestito e il codice nativo vengono ignorati.|  
|**Solo nativo**|Esegue il debug del codice C/C++ nativo nell'app. Il codice gestito e il codice JavaScript vengono ignorati.|  
|**Nativo con Script**|Esegue il debug del codice C++ nativo e del codice JavaScript nell'app.|  
|**Solo gestito**|Esegue il debug del codice gestito nell'app. Il codice JavaScript e il codice C/C++ nativo vengono ignorati.|  
|**Misto (gestito e nativo)**|Esegue il debug sia del codice C++ nativo e del codice gestito nell'app. Il codice JavaScript viene ignorato.|  

###  <a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a> (Facoltativo) Ritardare l'avvio dell'app nella sessione di debug  
 Per impostazione predefinita, Visual Studio avvia immediatamente l'app quando avvii il debug. Puoi anche avviare una sessione di debug ma ritardare l'avvio dell'app. L'app viene avviata nel debugger quando viene avviata dal menu Start o da un contratto di attivazione oppure da un altro processo o metodo. Puoi anche ritardare l'avvio per eseguire il debug di eventi in background nell'app che vuoi si verifichino quando l'app non è in esecuzione.  

 Si specifica se vuoi ritardare l'avvio dell'app nel **Avvia applicazione** elenco le **debug** pagina delle proprietà del progetto dell'app. Scegli una delle seguenti opzioni:  

-   Scegli **No** per ritardare l'avvio dell'app.  

-   Scegli **Sì** per avviare immediatamente l'app.  

###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> (Facoltativo) Disabilitare i loopback di rete  
 ![Si applica solo a Windows](../debugger/media/windows-only-content.png "windows_only_content")  

 Per motivi di sicurezza, a un'app di Windows Store installata in modalità standard non è consentito effettuare chiamate di rete al dispositivo in cui è installata. Per impostazione predefinita, la distribuzione di Visual Studio crea una esenzione da questa regola per l'app distribuita. Questa esenzione ti consente di verificare le procedure di comunicazione in un singolo computer. Prima di inviare l'app a Windows Store, dovrai testare l'app senza l'esenzione.  

 Per rimuovere l'esenzione di loopback di rete, scegliere **No** dalle **Consenti loopback della rete locale** elenco il **debug** pagina delle proprietà.  

##  <a name="BKMK_Start_the_debugging_session"></a> Avviare la sessione di debug  

###  <a name="BKMK_Start_debugging__F5_"></a> Avviare i debug (F5)  
 Quando si sceglie **Avvia debug** nel **Debug** menu (tastiera: F5), Visual Studio avvia l'app con il debugger collegato. L'esecuzione continua fino a raggiungere un punto di interruzione. Sospendi manualmente l'esecuzione e si verifica un'eccezione non gestita o l'app termina.  

###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Avviare il debug (F5) ma ritardare l'avvio dell'app  
 Puoi impostare l'app per l'esecuzione in modalità di debug, ma avviarla con un metodo diverso dal debugger. Ad esempio, puoi decidere di eseguire il debug dell'avvio dell'app dal menu Start o di eseguire il debug di un processo in background nell'app senza avviare l'app. Per ritardare l'avvio dell'app, procedi come indicato di seguito:  

1. Nel **Debug** pagina dell'app le proprietà del progetto, scegliere **No** dal **Avvia applicazione** elenco.  

2. Scegli **Avvia debug** nel **eseguire il Debug** menu (tastiera: F5).  

3. Avvia l'app dal menu Start, da un contratto di esecuzione o da un'altra routine.  

   L'app viene avviata in modalità debug. L'esecuzione continua fino a raggiungere un punto di interruzione. Sospendi manualmente l'esecuzione e si verifica un'eccezione non gestita o l'app termina.  

   . Per altre informazioni sul debug di attività in background, vedere [Trigger di sospensione, ripresa e background eventi per Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  

##  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Avviare un'app installata nel debugger  
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

##  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Collegare il debugger a un'app in esecuzione  
 Per collegare il debugger a un'app in [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , devi utilizzare Debuggable Package Manager per impostare l'esecuzione dell'app in modalità debug. Debuggable Package Manager viene installato con Visual Studio Remote Tools.  

 Il collegamento del debugger a un'app è utile quando devi eseguire il debug di un'app già installata, come un'app installata da Windows Store. Il collegamento è necessario quando disponi dei file di origine dell'app, ma non di un progetto di Visual Studio per l'app. Ad esempio, potresti disporre di un sistema di compilazione personalizzato che non utilizza progetti o soluzioni di Visual Studio.  

 Per collegare il debugger a un'app:  

1.  Imposta l'esecuzione dell'app in modalità debug. Questa operazione deve essere effettuata quando l'app non è in esecuzione.  

2.  Avvia l'app. Puoi avviare l'app dal menu Start, da un contratto di esecuzione o con un altro metodo.  

3.  Collega il debugger all'app in esecuzione.  

###  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Impostare l'esecuzione dell'app in modalità debug  

1.  Installa Visual Studio Remote Tools sul dispositivo in cui è installata l'app. Visualizzare [installazione di remote tools](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).  

2.  Nel menu Start cerca `Debuggable Package Manager` e avvialo.  

     Viene visualizzata una finestra di PowerShell correttamente configurata per il cmdlet AppxDebug.  

3.  Per abilitare il debug di un'app, devi specificare l'identificatore PackageFullName dell'app. Per visualizzare un elenco di tutte le app che includono PackageFullName, digita `Get-AppxPackage` al prompt di PowerShell.  

4.  Al prompt di PowerShell immetti `Enable-AppxDebug` *PackageFullName* in cui *PackageFullName* è l'identificatore PackageFullName dell'app.  

###  <a name="BKMK_Attach_the_debugger"></a> Collegare il debugger  

> [!TIP]
>  Le app JavaScript vengono eseguite in un'istanza del processo wwahost.exe. Se vengono eseguite altre app JavaScript quando colleghi il debugger all'app, dovrai conoscere l'ID processo numerico (PID) del processo wwahost.exe in cui viene eseguita l'app.  
>   
>  Il modo più semplice per gestire questa situazione consiste nel chiudere tutte le altre app JavaScript. Altrimenti, puoi aprire Gestione attività di Windows prima di avviare l'app e annotare gli ID dei processi wwahost.exe. Quando si specifica il processo a cui collegarsi nel **processi disponibili** wwahost.exe dell'app nella finestra di dialogo avrà un id diverso da quelli annotati.  

 Per collegare il debugger:  

1. Scegliere **Connetti a processo** dal menu **Debug**.  

    Verrà visualizzata la finestra di dialogo **Connetti a processo** .  

2. Per connetterti a un'app in un dispositivo remoto, specifica il dispositivo remoto nella casella **Qualificatore** . È possibile:  

   -   Immetti il nome nella casella **Qualificatore** .  

   -   Scegliere la freccia in giù nella **qualificatore** casella e seleziona il dispositivo da un elenco di dispositivi collegati a prima.  

   -   Scegli **trovare** per scegliere il dispositivo da un elenco di dispositivi sulla subnet locale.  

3. Specifica il tipo di codice di cui vuoi eseguire il debug nella casella **Connetti a** .  

    Scegli **Seleziona** , quindi effettua una delle seguenti operazioni:  

   -   Scegli **Determina automaticamente il tipo di codice di cui eseguire il debug**.  

   -   Scegli **Esegui il debug di questi tipi di codice** , quindi scegli uno o più tipi dall'elenco.  

4. Nel **processi disponibili** scegliere appropriato **wwahost.exe** processo. Usare la **titolo** colonna per identificare l'app.  

5. Scegliere **Connetti**.  

   Visual Studio collega il debugger al processo. L'esecuzione continua fino a raggiungere un punto di interruzione. Sospendi manualmente l'esecuzione e si verifica un'eccezione non gestita o l'app termina.  

## <a name="see-also"></a>Vedere anche  
 [Controllare l'esecuzione in una sessione di debug (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)   
 [Guida introduttiva: Debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Trigger di sospensione, ripresa e background eventi per Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)   
 [Eseguire il debug di app in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)



