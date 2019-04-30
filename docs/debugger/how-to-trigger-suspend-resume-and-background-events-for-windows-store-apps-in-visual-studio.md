---
title: Trigger di sospensione, ripresa e background eventi durante il debug di UWP | Microsoft Docs
ms.custom: seodec18
ms.date: 01/16/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.error.background_task_activate_failure
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
ms.openlocfilehash: c0c5c6a1bfb161f8eed37cbf9c95740596977852
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388491"
---
# <a name="how-to-trigger-suspend-resume-and-background-events-while-debugging-uwp-apps-in-visual-studio"></a>Come attivare sospensione, ripresa e background eventi durante il debug di App UWP in Visual Studio
Quando non esegui il debug, Windows **Process Lifetime Management** (PLM) controlla lo stato di esecuzione dell'app, cioè avvio, sospensione, ripresa e terminazione, in risposta alle azioni dell'utente e allo stato del dispositivo. Quando esegui il debug, Windows disabilita questi eventi di attivazione. In questo argomento viene descritto come generare tali eventi nel debugger.

 Viene inoltre descritto come eseguire il debug di **attività in background**. Le attività in background consentono di eseguire determinate operazioni in un processo in background, anche quando l'app non è in esecuzione. Puoi utilizzare il debugger per attivare la modalità di debug dell'app, quindi avviare l'attività in background ed eseguire il debug, senza avviare l'interfaccia utente.

 Per ulteriori informazioni su Process Lifetime Management e le attività in background, vedi [Launching, resuming, and multitasking](/windows/uwp/launch-resume/index).

## <a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a> Attivare gli eventi di Process Lifetime Management
 Windows può sospendere l'app quando l'utente passa a un'altra visualizzazione o quando viene attivata la modalità basso consumo. Puoi rispondere all'evento `Suspending` per salvare i dati utente e dell'app rilevanti in un archivio permanente e per liberare risorse. Quando un'app viene riattivata dallo stato **Sospeso** , passa allo stato **In esecuzione** e continua dal punto in cui si trovava al momento della sospensione. Puoi rispondere all'evento `Resuming` per ripristinare o aggiornare lo stato dell'app e recuperare le risorse.

 Anche se Windows tenta di mantenere in memoria quante più app sospese possibile, può terminare un'app se non sono disponibili risorse sufficienti per mantenerla in memoria. Un utente può anche chiudere in modo esplicito l'app. Non esiste un evento speciale per indicare che l'utente ha chiuso un'app.

 Nel debugger di Visual Studio, puoi sospendere, riprendere e terminare manualmente le app per eseguire il debug degli eventi relativi al ciclo di vita di elaborazione. Per eseguire il debug di un evento relativo al ciclo di vita di elaborazione:

1. Imposta un punto di interruzione nel gestore dell'evento di cui vuoi eseguire il debug.

2. Premere **F5** per avviare il debug.

3. Sulla barra degli strumenti **Posizione di debug** scegli l'evento da generare:

     ![Sospendere, riprendere, terminare e attività in background](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")

     Nota che **Sospendi e termina** chiude l'app e termina la sessione di debug.

## <a name="BKMK_Trigger_background_tasks"></a> Attivare attività in background
 Qualsiasi app può registrare un'attività in background per rispondere a determinati eventi di sistema, anche quando l'app non è in esecuzione. Le attività in background non possono eseguire codice che aggiorna direttamente l'interfaccia utente. Visualizzano invece informazioni all'utente con aggiornamenti di riquadri, aggiornamenti di notifiche e notifiche di tipo avviso popup. Per altre informazioni, vedere [Supporting your app with background tasks](https://msdn.microsoft.com/library/4c7bb148-eb1f-4640-865e-41f627a46e8e).

 Puoi attivare eventi che avviano attività in background per l'app dal debugger.

> [!NOTE]
> Il debugger può attivare solo gli eventi che non contengono dati, come gli eventi che segnalano una modifica dello stato del dispositivo. Devi attivare manualmente le attività in background che richiedono l'input dell'utente o altri dati.

 Il modo più realistico di generare un evento di attività in background si verifica quando l'app non è in esecuzione. È tuttavia supportata anche l'attivazione dell'evento in una sessione di debug standard.

### <a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a> Attivare un evento di attività in background da una sessione di debug standard

1. Imposta un punto di interruzione nel codice dell'attività in background di cui desideri eseguire il debug.

2. Premere **F5** per avviare il debug.

3. Dall'elenco degli eventi sulla barra degli strumenti **Posizione di debug** scegli l'attività in background che vuoi avviare.

     ![Sospendere, riprendere, terminare e attività in background](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")

### <a name="BKMK_Trigger_a_background_task_when_the_app_is_not_running"></a> Attivare un'attività in background quando l'app non è in esecuzione

1. Imposta un punto di interruzione nel codice dell'attività in background di cui desideri eseguire il debug.

2. Apri la pagina delle proprietà di debug per il progetto di avvio. Selezionare il progetto in Esplora soluzioni. Scegli **Proprietà** dal menu **Debug**.

     Per C++ progetti, espandere **le proprietà di configurazione** e quindi scegliere **debug**.

3. Eseguire una delle operazioni seguenti:

    - Per i progetti Visual C# e Visual Basic, scegli **Non eseguire il codice utente, ma eseguine il debug all'avvio**.

         ![C&#35;&#47;proprietà avvio applicazione debug Visual Basic](../debugger/media/dbg_csvb_dontlaunchapp.png "DBG_CsVb_DontLaunchApp")

    - Per oggetto visivo C++ progetti, scegliere **No** dal **Avvia applicazione** elenco.

         ![C&#43;&#43;&#47;proprietà di debug applicazione avviare VB](../debugger/media/dbg_cppjs_dontlaunchapp.png "DBG_CppJs_DontLaunchApp")

4. Premi **F5** per mettere l'app in modalità debug. Nota che nell'elenco **Processo** sulla barra degli strumenti **Posizione di debug** è visualizzato il nome del pacchetto dell'app per indicare che sei in modalità debug.

     ![Elenco dei processi attività in background](../debugger/media/dbg_backgroundtask_processlist.png "DBG_BackgroundTask_ProcessList")

5. Dall'elenco degli eventi sulla barra degli strumenti **Posizione di debug** scegli l'attività in background che vuoi avviare.

     ![Sospendere, riprendere, terminare e attività in background](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")

## <a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a> Attivare gli eventi di Process Lifecycle Management e le attività in background da un'app installata
 Usare la **Debug pacchetto applicazione installato** finestra di dialogo per caricare un'app già installata nel debugger. Ad esempio, si potrebbe eseguire il debug di un'app installata da Microsoft Store o eseguire il debug di un'app quando si dispone di file di origine per l'app, ma non a un progetto di Visual Studio per l'app. Il **Debug pacchetto applicazione installato** nella finestra di dialogo ti consente di avviare un'app in modalità di debug nel computer di Visual Studio o in un dispositivo remoto o per impostare l'app per l'esecuzione in modalità di debug ma non avviarlo. Per altre informazioni, vedere [eseguire il Debug di un pacchetto dell'app installato](../debugger/debug-installed-app-package.md).

 Una volta caricata l'app nel debugger, puoi utilizzare una qualsiasi tra le procedure descritte sopra.

## <a name="BKMK_Diagnosing_background_task_activation_errors"></a> Diagnostica degli errori di attivazione di attività in background
 I log di diagnostica nel Visualizzatore eventi di Windows per l'infrastruttura in background includono informazioni dettagliate che è possibile usare per diagnosticare e risolvere gli errori delle attività in background. Per visualizzare il log:

1. Aprire l'applicazione Visualizzatore eventi.

2. Nel riquadro **Azioni** scegli **Visualizza** e verificare che **Visualizza registri analitici e di debug** sia selezionata.

3. Sulla barra degli strumenti **Visualizzatore eventi (locale)** espandi i nodi **Registri applicazioni e servizi** > **Microsoft** > **Windows** > **BackgroundTasksInfrastructure**.

4. Scegli il log **Diagnostica** .

## <a name="see-also"></a>Vedere anche
- [Test delle app UWP con Visual Studio](../test/testing-store-apps-with-visual-studio.md)
- [Eseguire il debug di app in Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)
- [Ciclo di vita dell'applicazione](/windows/uwp/launch-resume/app-lifecycle)
- [Launching, resuming, and multitasking](/windows/uwp/launch-resume/index)