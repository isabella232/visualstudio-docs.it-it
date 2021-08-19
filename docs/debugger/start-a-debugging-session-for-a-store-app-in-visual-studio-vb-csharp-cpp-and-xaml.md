---
title: Avviare una sessione di debug per un'app UWP | Microsoft Docs
description: Avviare una Visual Studio di debug per un'app UWP (Universal Windows Platform). Configurare la sessione di debug e scegliere la modalità di avvio dell'app.
ms.custom: SEO-VS-2020
ms.date: 11/20/2018
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- uwp
ms.openlocfilehash: 073b29afe8af9b6b23d7eda1b30631018674e9c5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146719"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>Avviare una sessione di debug per un'app UWP

Questo articolo descrive come avviare una sessione Visual Studio di debug per un'app UWP (Universal Windows Platform). Le app UWP possono essere scritte in XAML e C++, XAML e C#/Visual Basic. Per avviare il debug di un'app UWP, configurare la sessione di debug e scegliere la modalità di avvio dell'app.

::: moniker range=">=vs-2019"
> [!NOTE]
> A partire Visual Studio 2019, le app UWP per HTML e JavaScript non sono più supportate.
::: moniker-end
::: moniker range="vs-2017"
In Visual Studio 2017, la maggior parte dei comandi e delle opzioni illustrati in questo articolo si applica anche alle app UWP per HTML e JavaScript. Quando i comandi sono diversi tra le app gestite e le app C++, le app JavaScript sono in genere uguali ai comandi per le app UWP C++.
::: moniker-end

## <a name="start-debugging-from-the-visual-studio-toolbar"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Avviare il debug dalla barra degli Visual Studio strumenti

Il modo più semplice per configurare e avviare il debug è dalla barra Visual Studio standard.

![Eseguire il debug dalla barra degli strumenti](../debugger/media/vsrun_select_target_device.png)

1. **Nell'elenco a** discesa Configurazione sulla **barra degli strumenti Standard** selezionare **Debug.**

1. Nell'elenco **a** discesa Piattaforma selezionare la piattaforma di destinazione per cui eseguire la compilazione.

1. Nell'elenco a discesa accanto alla freccia verde selezionare la destinazione di debug. È possibile scegliere un computer locale, un dispositivo connesso direttamente, un simulatore Visual Studio, un dispositivo remoto o un emulatore.

1. Per avviare il debug, selezionare la freccia **verde Avvia** sulla barra degli strumenti oppure selezionare **Debug**  >  **Avvia** debug oppure premere **F5.**

   Visual Studio compila e avvia l'app con il debugger collegato.

Il debug continua fino a quando non viene raggiunto un punto di interruzione, l'esecuzione viene sospesa manualmente, si verifica un'eccezione non gestita o l'app termina.

### <a name="deployment-target-options"></a><a name="BKMK_Choose_the_deployment_target"></a> Opzioni di destinazione della distribuzione

È possibile impostare la destinazione di debug nella barra Visual Studio o nella pagina delle proprietà di debug del progetto. Selezionare una delle opzioni seguenti:

|Nome|Descrizione|
|-|-|
|**Computer locale**|Esegue il debug dell'app nella sessione corrente nel computer locale.|
|**Simulatore**|Eseguire il debug dell'app nel simulatore Visual Studio per le app UWP. Il simulatore è una finestra desktop che simula le funzioni del dispositivo, ad esempio i movimenti tocco e la rotazione del dispositivo, che potrebbero non esistere nel computer locale. L'opzione simulatore è disponibile  solo se la versione minima della piattaforma di destinazione dell'app è minore o uguale al sistema operativo nel computer locale. Per altre informazioni, vedere [Eseguire app UWP nel simulatore.](../debugger/run-windows-store-apps-in-the-simulator.md)|
|**Computer remoto**|Eseguire il debug dell'app in un dispositivo connesso al computer locale tramite un cavo di rete o Ethernet. Il Remote Tools per Visual Studio deve essere installato e in esecuzione nel dispositivo remoto. Per altre informazioni, vedere [Eseguire app UWP in un computer remoto.](../debugger/run-windows-store-apps-on-a-remote-machine.md)|
|**Dispositivo**|Eseguire il debug dell'app in un dispositivo connesso tramite USB. Il dispositivo deve essere sbloccato dallo sviluppatore e lo schermo deve essere sbloccato.|
|**Dispositivi mobili Emulator**|Avviare l'emulatore specificato nel nome dell'emulatore, distribuire l'app e avviare il debug. Gli emulatori sono disponibili solo nei computer abilitati per Hyper-V.|

## <a name="configure-debugging-in-the-project-property-page"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Configurare il debug nella pagina delle proprietà del progetto

Per configurare opzioni di debug aggiuntive, usare la pagina delle proprietà di debug del progetto.

**Per aprire le proprietà di debug:**

1. In **Esplora soluzioni** selezionare il progetto e quindi  selezionare l'icona Proprietà oppure fare clic con il pulsante destro del mouse sul progetto e **scegliere Proprietà.**

1. Sul lato sinistro del **riquadro** Proprietà:

   - Per le app C# Visual Basic, selezionare **Debug.**

     ![Pagina delle proprietà di debug Visual Basic progetto C# e C#](../debugger/media/dbg_csvb_debugpropertypage.png)

   - Per le app C++, selezionare **Debug delle proprietà** di  >  **configurazione.**

     ![Pagina delle proprietà Debug di app UWP C++](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a> Scegliere il debugger da utilizzare

Per le app C# e Visual Basic, Visual Studio esegue il debug del codice gestito per impostazione predefinita. È possibile scegliere di eseguire il debug di altri tipi di codice o di altri tipi. È anche possibile impostare **i valori del tipo** di debugger per tutte le attività in background che fanno parte del progetto.

Nelle app C++ Visual Studio debug del codice nativo per impostazione predefinita. È possibile scegliere di eseguire il debug di tipi specifici di codice anziché, o in aggiunta al codice nativo.

**Per specificare i tipi di codice di cui eseguire il debug:**

- Per le app C# e Visual Basic, selezionare uno  dei debugger  seguenti dagli elenchi a discesa Tipo di applicazione e Tipo di processo in background in **Tipo** di debugger nella pagina **delle proprietà Debug.**

- Per le app C++, selezionare uno dei debugger seguenti dall'elenco a discesa **Tipo** di debugger nella **pagina delle proprietà** Debug.

|Nome|Descrizione|
|-|-|
|**Solo gestito**|Esegue il debug del codice gestito nell'app. Il codice JavaScript e il codice C/C++ nativo vengono ignorati.|
|**Solo nativo**|Esegue il debug del codice C/C++ nativo nell'app. Il codice gestito e il codice JavaScript vengono ignorati.|
|**Misto (gestito e nativo)**|Esegue il debug sia del codice C++ nativo e del codice gestito nell'app. Il codice JavaScript viene ignorato. Nei progetti C++ questa opzione è denominata **Managed e Native.**|
|**Script**|Esegue il debug del codice JavaScript nell'app. Il codice gestito e il codice nativo vengono ignorati.|
|**Nativo con script**|Eseguire il debug del codice C/C++ nativo e del codice JavaScript nell'app. Il codice gestito viene ignorato. Disponibile solo nei progetti C++ o nelle attività in background.|
|**Solo GPU (C++ AMP)**|Esegue il debug del codice C++ nativo eseguito su un'unità di elaborazione grafica (GPU). Disponibile solo nei progetti C++.|

### <a name="disable-network-loopbacks-optional"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a> Disabilitare i loopback di rete (facoltativo)

 Per motivi di sicurezza, un'app UWP installata in modo standard non può effettuare chiamate di rete al dispositivo in cui è installata. Visual Studio esenta le app distribuite da questa regola per impostazione predefinita, pertanto è possibile testare le procedure di comunicazione in un singolo computer. Prima di rilasciare l'app, è consigliabile testare l'app senza l'esenzione.

**Per rimuovere l'esenzione relativa al loopback della rete:**

- Per le app C# e Visual Basic, deselezionare la casella di controllo Consenti **loopback** di rete locale in **Opzioni** di avvio nella **pagina delle proprietà Debug.**

- Per le app C++, selezionare **No** dall'elenco a discesa **Consenti loopback** della rete locale nella **pagina delle proprietà** Debug.

### <a name="reinstall-the-app-when-you-start-debugging-optional"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> Reinstallare l'app all'avvio del debug (facoltativo)
 Per diagnosticare i problemi di installazione con un'app C# o Visual Basic, selezionare Disinstalla e quindi reinstallare **il** pacchetto nella pagina **delle proprietà Debug.** Questa opzione ricrea l'installazione originale all'avvio del debug. Questa opzione non è disponibile per i progetti C++.

### <a name="set-authentication-options-for-remote-debugging"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> Impostare le opzioni di autenticazione per il debug remoto

Per impostazione predefinita, è necessario Windows credenziali per eseguire il debugger remoto quando si seleziona **Computer remoto** come destinazione della distribuzione. È possibile modificare il requisito di autenticazione.

La modalità di autenticazione **universale (protocollo** non crittografato) è per i dispositivi IoT, Xbox e HoloLens e creator's Update o versioni successive Windows 10 PC.

**Per modificare il metodo di autenticazione:**

- Per le app C# Visual Basic, nella pagina delle proprietà **Debug** selezionare **Computer remoto** come Dispositivo di **destinazione.** Selezionare quindi **Nessuno o** Universale **(protocollo non crittografato) per** Modalità di **autenticazione.**

- Per le app C++, selezionare **Computer remoto** in **Debugger da avviare** nella pagina delle **proprietà** Debug. Selezionare quindi **Nessuna autenticazione o** Universale **(protocollo non crittografato)** per **Tipo di autenticazione**.

> [!CAUTION]
> Non esiste alcuna sicurezza di rete quando si esegue il debugger remoto in modalità **Nessuno** o **Universale (protocollo non** crittografato). Scegliere queste modalità solo nelle reti attendibili che non sono a rischio di codice dannoso o di traffico ostile.

## <a name="debugging-start-options"></a><a name="BKMK_Start_the_debugging_session"></a> Opzioni di avvio del debug

Quando si seleziona **Debug** Avvia debug o si  >   preme **F5,** Visual Studio avvia l'app con il debugger collegato. L'esecuzione continua fino a raggiungere un punto di interruzione. Sospendi manualmente l'esecuzione e si verifica un'eccezione non gestita o l'app termina.

### <a name="start-debugging-but-delay-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Avviare il debug ma ritardare l'avvio dell'app

Per impostazione predefinita, Visual Studio'app viene avviata immediatamente all'avvio del debug. È anche possibile impostare l'app per l'esecuzione in modalità di debug, ma avviare l'app all'esterno del debugger. Ad esempio, potrebbe essere necessario eseguire il debug dell'avvio dell'app dal menu **Start** Windows oppure eseguire il debug di un processo in background nell'app. Se si sceglie questa opzione, l'app viene avviata nel debugger all'avvio.

**Per disabilitare l'avvio automatico dell'app:**

- Per le app C# e Visual Basic, selezionare Non **avviare,** ma eseguire il debug del codice all'avvio in **Opzioni** di avvio nella **pagina delle proprietà** Debug.

- Per le app C++, selezionare **No** nell'elenco **a discesa Avvia** applicazione nella pagina delle **proprietà** Debug.

Per altre informazioni sul debug delle attività in background, vedere Attivare eventi [di sospensione, ripresa ed eventi in background per le app UWP.](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)

### <a name="debug-an-installed-or-running-uwp-app"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Eseguire il debug di un'app UWP installata o in esecuzione

È possibile usare **Debug pacchetto app installato** per eseguire il debug di un'app UWP già installata o in esecuzione in un dispositivo locale o remoto. L'app potrebbe essere stata installata dal Microsoft Store o potrebbe non essere un Visual Studio progetto. Ad esempio, l'app potrebbe avere un sistema di compilazione personalizzato che non usa Visual Studio.

È possibile avviare immediatamente l'app installata oppure impostarla per l'esecuzione nel debugger quando viene avviata con un altro metodo. Per altre informazioni, vedere [Attivare eventi di sospensione, ripresa ed eventi in background per le app UWP.](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)

Per avviare un'app UWP installata o in esecuzione nel debugger, selezionare **Debug** altre destinazioni  >  **di debug** Debug Pacchetto app  >  **installato**. Per altre istruzioni, vedere [Eseguire il debug di un pacchetto di app installato.](../debugger/debug-installed-app-package.md)

### <a name="attach-the-debugger-to-a-running-windows-8x-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Connettere il debugger a un'app Windows 8.x in esecuzione

Per collegare il debugger a un'app in [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] , devi utilizzare Debuggable Package Manager per impostare l'esecuzione dell'app in modalità debug. L'Gestione pacchetti Debuggable viene installato con l'Remote Tools per Visual Studio.

1. Installare il Remote Tools per Visual Studio nel dispositivo in cui è installata l'app. Per altre informazioni, vedere [Installazione degli strumenti remoti](../debugger/remote-debugging.md).

1. Nella schermata Windows **Start** cercare e avviare **Debuggable Gestione pacchetti**.

   Viene visualizzata una finestra di PowerShell correttamente configurata per il cmdlet AppxDebug.

1. Specificare l'identificatore PackageFullName dell'app.

   1. Per visualizzare un elenco che include PackageFullName di tutte le app, digitare `Get-AppxPackage` al prompt di PowerShell.

   1. Al prompt di PowerShell immettere `Enable-AppxDebug <PackageFullName>` , dove \<PackageFullName> è l'identificatore PackageFullName dell'app.

1. Selezionare **Debug**  >  **collegamento a processo**.

1. Nella finestra **di dialogo Collega a** processo specificare il dispositivo remoto nella casella **Destinazione** connessione .

   È possibile immettere il nome del dispositivo,  selezionarlo nell'elenco a discesa nella casella Destinazione connessione oppure selezionare Trova per trovare il dispositivo nella **finestra di** dialogo Connessioni remote . 

1. Per specificare il tipo di codice di cui si vuole eseguire il debug, accanto alla **casella Associa a** selezionare **Seleziona**.

1. Nella finestra **di dialogo Seleziona tipo** di codice selezionare una delle opzioni seguenti:
   - **Determinare automaticamente il tipo di codice di cui eseguire il debug** o
   - **Eseguire il debug di questi** tipi di codice e quindi selezionare uno o più tipi di codice dall'elenco.

1. **Nell'elenco Processi disponibili selezionare** il processo dell'app di cui eseguire il debug.

1. Selezionare **Allega**.

 Visual Studio collega il debugger al processo. L'esecuzione continua fino a raggiungere un punto di interruzione. Sospendi manualmente l'esecuzione e si verifica un'eccezione non gestita o l'app termina.

::: moniker range="vs-2017"
> [!NOTE]
> Le app JavaScript vengono eseguite in un'istanza *delwwahost.exe* processo. Se è *in* esecuzione più di un'app JavaScript, è necessario conoscere l'ID processo numerico (PID) del processo diwwahost.exedell'app per connettersi ad essa.
>
> Il modo più semplice per connettersi all'app JavaScript è chiudere tutte le altre app JavaScript. In caso contrario, è possibile prendere nota dei PIN diwwahost.exe *processi* in Windows Gestione attività prima di avviare l'app. Quando si avvia l'app, il *wwahost.exe* PID sarà diverso da quello indicato in precedenza.
::: moniker-end

## <a name="see-also"></a>Vedi anche

- [Eseguire il debug di app in Visual Studio](../debugger/debugging-windows-store-and-windows-universal-apps.md)