---
title: Avviare una sessione di debug per un'app UWP | Microsoft Docs
ms.custom: seodec18
ms.date: 11/20/2018
ms.topic: conceptual
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
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 7c65662d054b8c3dd9e650fe088f7048cc3b4071
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60081853"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>Avviare una sessione di debug per un'app UWP

Questo articolo descrive come avviare una sessione di debug di Visual Studio per un'app Universal Windows Platform (UWP). Le app UWP possono essere scritte in XAML e C++, XAML e C#/Visual Basic. Per avviare il debug di un'app UWP, configurare la sessione di debug e scegliere il modo in cui avviare l'app.

::: moniker range=">=vs-2019"
> [!NOTE]
> A partire da Visual Studio 2019, le app UWP per HTML e JavaScript non sono più supportate.
::: moniker-end
::: moniker range="vs-2017"
In Visual Studio 2017, la maggior parte dei comandi e opzioni illustrate in questo articolo si applicano anche alle App UWP per HTML e JavaScript. In cui i comandi sono diversi tra gestito e C++ le app, le app JavaScript in genere sono gli stessi comandi per C++ le app UWP.
::: moniker-end

## <a name="BKMK_The_easy_way_to_start_debugging"></a>Avviare il debug nella barra degli strumenti di Visual Studio

Il modo più semplice per configurare e avviare il debug è dalla barra degli strumenti standard di Visual Studio.

![Eseguire il debug nella barra degli strumenti](../debugger/media/vsrun_select_target_device.png)

1. Dal **Configuration** elenco a discesa nel **Standard** sulla barra degli strumenti, seleziona **Debug**.

1. Dal **piattaforma** elenco a discesa, selezionare la piattaforma di destinazione per creare applicazioni per.

1. Nell'elenco a discesa accanto alla freccia verde, selezionare la destinazione di debug. È possibile scegliere un computer locale, dispositivo connesso a direct, il simulatore di Visual Studio locale, dispositivo remoto o un emulatore.

1. Per avviare il debug, selezionare il colore verde **avviare** freccia sulla barra degli strumenti, oppure scegliere **Debug** > **Avvia debug**, o premere **F5**.

   Visual Studio compila e avvia l'app con il debugger collegato.

Debug continua fino a quando non viene raggiunto un punto di interruzione, Sospendi manualmente l'esecuzione, si verifica un'eccezione non gestita, o l'app termina.

### <a name="BKMK_Choose_the_deployment_target"></a> Opzioni di destinazione di distribuzione

È possibile impostare la destinazione di debug sulla barra degli strumenti di Visual Studio o il progetto di pagina delle proprietà di debug. Selezionare una delle opzioni seguenti:

|||
|-|-|
|**Computer locale**|Esegue il debug dell'app nella sessione corrente nel computer locale.|
|**Simulatore**|Eseguire il debug dell'app nel simulatore di Visual Studio per le app UWP. Il simulatore è una finestra del desktop che simula funzioni del dispositivo, ad esempio rotazione del dispositivo, che potrebbe non esistere nel computer locale e i movimenti di tocco. L'opzione simulatore è disponibile solo se l'app **minima piattaforma di destinazione. Versione** è minore o uguale al sistema operativo nel computer locale. Per altre informazioni, vedere [eseguire App UWP nel simulatore](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Computer remoto**|Eseguire il debug dell'app in un dispositivo connesso al computer locale tramite una rete o un cavo Ethernet. Remote Tools per Visual Studio deve essere installato e in esecuzione nel dispositivo remoto. Per altre informazioni, vedere [eseguire App UWP in un computer remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|
|**Dispositivo**|Eseguire il debug dell'app in un dispositivo connessa tramite USB. Il dispositivo deve essere sbloccato dallo sviluppatore e avere la schermata sbloccata.|
|**Emulatore per dispositivi mobili**|Avviare l'emulatore specificato nel nome dell'emulatore, distribuire l'app e avviare il debug. Gli emulatori sono disponibili solo in computer Hyper-V abilitato.|

## <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Configurare il debug nella pagina delle proprietà del progetto

Per configurare le opzioni di debug aggiuntive, usare pagina delle proprietà debug del progetto.

**Per aprire le proprietà di debug:**

1. Nella **Esplora soluzioni**, selezionare il progetto e quindi selezionare la **delle proprietà** icona, o il progetto e scegliere **proprietà**.

1. Sul lato sinistro della **proprietà** riquadro:

   - Per C# e le app Visual Basic, selezionare **eseguire il Debug**.

     ![C#pagina delle proprietà debug progetto Visual Basic e](../debugger/media/dbg_csvb_debugpropertypage.png)

   - Per C++ App, selezionare **le proprietà di configurazione** > **debug**.

     ![C++Pagina delle proprietà Debug app UWP](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="BKMK_Choose_the_debugger_to_use"></a> Scegliere il debugger da utilizzare

Per C# e le app Visual Basic, Visual Studio esegue il debug di codice gestito per impostazione predefinita. È possibile effettuare il debug di codice aggiuntivo o altri tipi. È anche possibile impostare **tipo di Debugger** i valori per le attività in background che fanno parte del progetto.

Nelle App C++, Visual Studio esegue il debug del codice nativo per impostazione predefinita. È possibile scegliere di eseguire il debug di tipi specifici di codice al posto o in aggiunta, codice nativo.

**Per specificare i tipi di codice per eseguire il debug:**

- Per C# e le app Visual Basic, selezionare uno dei seguenti debugger dal **tipo di applicazione** e **tipo di processo in Background** elenchi a discesa sotto **tipo di Debugger** in il **Debug** pagina delle proprietà.

- Per C++ App, selezionare uno dei seguenti debugger dal **tipo di Debugger** casella a discesa la **debug** pagina delle proprietà.

|||
|-|-|
|**Solo gestito**|Esegue il debug del codice gestito nell'app. Il codice JavaScript e il codice C/C++ nativo vengono ignorati.|
|**Solo nativo**|Esegue il debug del codice C/C++ nativo nell'app. Il codice gestito e il codice JavaScript vengono ignorati.|
|**Misto (gestito e nativo)**|Esegue il debug sia del codice C++ nativo e del codice gestito nell'app. Il codice JavaScript viene ignorato. In C++ progetti, questa opzione, detta **gestito e nativo**.|
|**Script**|Esegue il debug del codice JavaScript nell'app. Il codice gestito e il codice nativo vengono ignorati.|
|**Nativo con script**|Eseguire il debug di codice C/C++ nativo e il codice JavaScript nell'app. Il codice gestito viene ignorato. Disponibile in C++ progetti o in background elencate solo le attività.|
|**Solo GPU (C++ AMP)**|Esegue il debug del codice C++ nativo eseguito su un'unità di elaborazione grafica (GPU). Disponibile in solo progetti C++.|

### <a name="BKMK__Optional__Disable_network_loopbacks"></a> Disabilitare i loopback di rete (facoltativi)

 Per la sicurezza, un'app UWP che viene installata in modalità standard non è possibile effettuare chiamate di rete per il dispositivo in che cui è installata. Esenti di Visual Studio distribuito le app da questa regola per impostazione predefinita, è possibile testarne le procedure di comunicazione in un singolo computer. Prima di rilasciare l'app, è consigliabile testare l'app senza l'esenzione.

**Per rimuovere l'esenzione relativa al loopback della rete:**

- Per C# e le app Visual Basic, deseleziona il **Consenti loopback della rete locale** casella di controllo sotto **opzioni di avvio** sul **Debug** pagina delle proprietà.

- Per oggetto visivo C++ le app, selezionare **No** dal **Consenti Loopback della rete locale** casella a discesa il **debug** pagina delle proprietà.

### <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> Reinstallare l'app all'avvio del debug (facoltativo)
 Per diagnosticare i problemi di installazione con un C# o app Visual Basic, selezionare **Disinstalla e reinstalla il pacchetto** sul **Debug** pagina delle proprietà. Questa opzione viene ricreata l'installazione originale all'avvio del debug. Questa opzione non è disponibile per C++ progetti.

### <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> Impostare le opzioni di autenticazione per il debug remoto

Per impostazione predefinita, è necessario fornire le credenziali di Windows per eseguire il debugger remoto quando si seleziona **computer remoto** come destinazione di distribuzione. È possibile modificare il requisito di autenticazione.

Il **universale (protocollo non crittografato)** è la modalità di autenticazione per dispositivi IoT, Xbox e HoloLens e Creators Update o versioni successive i PC Windows 10.

**Per modificare il metodo di autenticazione:**

- Per C# e le app Visual Basic, su di **eseguire il Debug** pagina delle proprietà, seleziona **computer remoto** come il **dispositivo di destinazione**. Quindi, selezionare **None** oppure **universale (protocollo non crittografato)** per **modalità di autenticazione**.

- Per C++ App, selezionare **computer remoto** sotto **Debugger da avviare** sul **debug** pagina delle proprietà. Quindi, selezionare **Nessuna autenticazione** oppure **universale (protocollo non crittografato)** per **tipo di autenticazione**.

> [!CAUTION]
> Non vi è alcuna sicurezza di rete quando si esegue il debugger remoto in **None** oppure **universale (protocollo non crittografato)** modalità. Scegliere queste modalità solo su reti attendibili che si sono certi non sono esposti da traffico ostile o codice dannoso.

## <a name="BKMK_Start_the_debugging_session"></a> Opzioni di avvio debug

Quando si seleziona **Debug** > **Avvia debug** oppure premere **F5**, Visual Studio avvia l'app con il debugger collegato. L'esecuzione continua fino a raggiungere un punto di interruzione. Sospendi manualmente l'esecuzione e si verifica un'eccezione non gestita o l'app termina.

### <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Avviare il debug ma Ritardo avvio dell'app

Per impostazione predefinita, Visual Studio avvia l'app immediatamente all'avvio del debug. È anche possibile impostare l'app per l'esecuzione in modalità di debug, avviare l'app all'esterno del debugger. Ad esempio, è possibile eseguire il debug avvio dell'app da di Windows **avviare** menu o debug un processo in background nell'app. Se si sceglie questa opzione, l'app viene avviata nel debugger all'avvio.

**Per disabilitare l'avvio automatico di app:**

- Per C# e le app Visual Basic, selezionare **non, ma eseguine il debug del codice quando viene avviato** sotto **opzioni di avvio** sul **Debug** pagina delle proprietà.

- Per C++ App, selezionare **No** dal **Avvia applicazione** casella a discesa la **debug** pagina delle proprietà.

Per altre informazioni sul debug di attività in background, vedere [Trigger di sospensione, ripresa e background eventi per le app UWP](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Eseguire il debug di un'app UWP in esecuzione o installata

È possibile usare **Debug pacchetto applicazione installato** per eseguire il debug di un'app UWP che è già installato o in esecuzione in un dispositivo locale o remoto. L'app potrebbe essere stata installata da di Microsoft Store, o potrebbe non essere un progetto di Visual Studio. Ad esempio, l'app può avere un sistema di compilazione personalizzato che non Usa Visual Studio.

È possibile avviare l'app installata immediatamente oppure è possibile impostare l'esecuzione nel debugger quando avviata con un altro metodo. Per altre informazioni, vedere [Trigger di sospensione, ripresa e background eventi per le app UWP)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

Per avviare un'app UWP in esecuzione o installata nel debugger, selezionare **Debug** > **altre destinazioni Debug** > **Debug pacchetto applicazione installato**. Per altre istruzioni, vedere [eseguire il Debug di un pacchetto dell'app installato](../debugger/debug-installed-app-package.md).

### <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Collegare il debugger a un'app di in esecuzione Windows 8.x

Per collegare il debugger a un'app in [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] , devi utilizzare Debuggable Package Manager per impostare l'esecuzione dell'app in modalità debug. Debuggable Package Manager viene installato con Remote Tools per Visual Studio.

1. Installare Remote Tools per Visual Studio nel dispositivo in cui è installato l'app. Per altre informazioni, vedere [installazione di remote tools](../debugger/remote-debugging.md).

1. Nella finestra di Windows **avviare** schermata, cercare e avviare **Debuggable Package Manager**.

   Viene visualizzata una finestra di PowerShell correttamente configurata per il cmdlet AppxDebug.

1. Specificare l'identificatore PackageFullName dell'app.

   1. Per visualizzare un elenco che includono PackageFullName di tutte le app, digitare `Get-AppxPackage` al prompt di PowerShell.

   1. Al prompt di PowerShell, immettere `Enable-AppxDebug <PackageFullName>`, dove \<PackageFullName > è l'identificatore PackageFullName dell'app.

1. Selezionare **Debug** > **Associa a processo**.

1. Nel **Connetti a processo** finestra di dialogo, specificare il dispositivo remoto nella **destinazione della connessione** casella.

   È possibile immettere il nome del dispositivo, selezionarlo dall'elenco a discesa nel **destinazione della connessione** casella o selezionarne **trovare** per trovare il dispositivo nel **le connessioni Remote** nella finestra di dialogo.

1. Per specificare il tipo di codice da sottoporre a debug, accanto al **collegarsi** , quindi selezionare **selezionare**.

1. Nel **Seleziona tipo di codice** finestra di dialogo Seleziona:
   - **Determina automaticamente il tipo di codice per eseguire il debug**, o
   - **Eseguire il debug di questi tipi di codice**e quindi selezionare uno o più tipi di codice dall'elenco.

1. Nel **processi disponibili** elencare, selezionare il processo dell'app per eseguire il debug.

1. Selezionare **collegare**.

 Visual Studio collega il debugger al processo. L'esecuzione continua fino a raggiungere un punto di interruzione. Sospendi manualmente l'esecuzione e si verifica un'eccezione non gestita o l'app termina.

::: moniker range="vs-2017"
> [!NOTE]
> Le app JavaScript vengono eseguite in un'istanza del processo *wwahost.exe*. Se più app JavaScript è in esecuzione, è necessario conoscere l'id processo numerico (PID) dell'app *wwahost.exe* processo a cui collegarsi ad esso.
>
> Il modo più semplice per collegare all'app JavaScript consiste nel chiudere tutte le altre App JavaScript. In alternativa, è possibile notare il PID di esecuzione *wwahost.exe* processi Windows Task Manager prima di avviare l'app. Quando si avvia l'app, relativi *wwahost.exe* PID sarà quello che è diverso da quelli annotati in precedenza.
::: moniker-end

## <a name="see-also"></a>Vedere anche
- [Eseguire il debug di app in Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)