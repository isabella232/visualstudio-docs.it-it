---
title: Attivare eventi di sospensione/ripresa/in background durante il debug della UWP
description: Vedere come attivare eventi di sospensione, ripresa e in background durante il debug di app UWP (Universal Windows Platform) in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/16/2018
ms.topic: how-to
f1_keywords:
- vs.debug.error.background_task_activate_failure
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
ms.openlocfilehash: 01ae0d08e0211c48c8ff96052d7a12fe5f9aeb56
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112776"
---
# <a name="how-to-trigger-suspend-resume-and-background-events-while-debugging-uwp-apps-in-visual-studio"></a>Come attivare eventi di sospensione, ripresa e in background durante il debug di app UWP in Visual Studio

Quando non esegui il debug, Windows **Process Lifetime Management** (PLM) controlla lo stato di esecuzione dell'app, cioè avvio, sospensione, ripresa e terminazione, in risposta alle azioni dell'utente e allo stato del dispositivo. Quando esegui il debug, Windows disabilita questi eventi di attivazione. In questo argomento viene descritto come generare tali eventi nel debugger.

Viene inoltre descritto come eseguire il debug di **attività in background**. Le attività in background consentono di eseguire determinate operazioni in un processo in background, anche quando l'app non è in esecuzione. Puoi utilizzare il debugger per attivare la modalità di debug dell'app, quindi avviare l'attività in background ed eseguire il debug, senza avviare l'interfaccia utente.

Per altre informazioni sulle Gestione del ciclo di vita dei processi e in background, vedere [Avvio, ripresa e multitasking.](/windows/uwp/launch-resume/index)

## <a name="trigger-process-lifetime-management-events"></a><a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a> Attivare gli eventi di Process Lifetime Management
 Windows possibile sospendere l'app quando l'utente si allontana da essa o quando Windows passa a uno stato a basso consumo. Puoi rispondere all'evento `Suspending` per salvare i dati utente e dell'app rilevanti in un archivio permanente e per liberare risorse. Quando un'app viene riattivata dallo stato **Sospeso** , passa allo stato **In esecuzione** e continua dal punto in cui si trovava al momento della sospensione. Puoi rispondere all'evento `Resuming` per ripristinare o aggiornare lo stato dell'app e recuperare le risorse.

 Anche se Windows tenta di mantenere in memoria quante più app sospese possibile, può terminare un'app se non sono disponibili risorse sufficienti per mantenerla in memoria. Un utente può anche chiudere in modo esplicito l'app. Non esiste un evento speciale per indicare che l'utente ha chiuso un'app.

 Nel debugger di Visual Studio, puoi sospendere, riprendere e terminare manualmente le app per eseguire il debug degli eventi relativi al ciclo di vita di elaborazione. Per eseguire il debug di un evento relativo al ciclo di vita di elaborazione:

1. Impostare un punto di interruzione nel gestore dell'evento di cui si vuole eseguire il debug.

2. Premere **F5** per avviare il debug.

3. Sulla barra degli strumenti **Posizione di debug** scegli l'evento da generare:

     ![Sospensione, ripresa, fine e attività in background](../debugger/media/dbg_suspendresumebackground.png)

     **Sospendi e** termina chiude l'app e termina la sessione di debug.

## <a name="trigger-background-tasks"></a><a name="BKMK_Trigger_background_tasks"></a> Attivare attività in background
 Qualsiasi app può registrare un'attività in background per rispondere a determinati eventi di sistema, anche quando l'app non è in esecuzione. Le attività in background non possono eseguire codice che aggiorna direttamente l'interfaccia utente. Visualizzano invece informazioni all'utente con aggiornamenti di riquadri, aggiornamenti di notifiche e notifiche di tipo avviso popup. Per altre informazioni, vedere [Supporto dell'app con attività in background.](/previous-versions/windows/apps/hh977046(v=win.10))

 Puoi attivare eventi che avviano attività in background per l'app dal debugger.

> [!NOTE]
> Il debugger può attivare solo gli eventi che non contengono dati, come gli eventi che segnalano una modifica dello stato del dispositivo. Devi attivare manualmente le attività in background che richiedono l'input dell'utente o altri dati.

 Il modo più realistico di generare un evento di attività in background si verifica quando l'app non è in esecuzione. È tuttavia supportata anche l'attivazione dell'evento in una sessione di debug standard.

### <a name="trigger-a-background-task-event-from-a-standard-debug-session"></a><a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a> Attivare un evento di attività in background da una sessione di debug standard

1. Imposta un punto di interruzione nel codice dell'attività in background di cui desideri eseguire il debug.

2. Premere **F5** per avviare il debug.

3. Dall'elenco degli eventi sulla barra degli strumenti **Posizione di debug** scegli l'attività in background che vuoi avviare.

     ![Sospensione, ripresa, fine e attività in background](../debugger/media/dbg_suspendresumebackground.png)

### <a name="trigger-a-background-task-when-the-app-is-not-running&quot;></a><a name=&quot;BKMK_Trigger_a_background_task_when_the_app_is_not_running&quot;></a> Attivare un'attività in background quando l'app non è in esecuzione

1. Imposta un punto di interruzione nel codice dell'attività in background di cui desideri eseguire il debug.

2. Apri la pagina delle proprietà di debug per il progetto di avvio. In Esplora soluzioni selezionare il progetto. Scegli **Proprietà** dal menu **Debug**.

     Per i progetti C++, espandere **Proprietà di configurazione** e quindi scegliere **Debug.**

3. Eseguire una delle operazioni seguenti:

    - Per i progetti Visual C# e Visual Basic, scegli **Non eseguire il codice utente, ma eseguine il debug all'avvio**.

         ![Proprietà dell&#35;&#47;VB di avvio del debug C](../debugger/media/dbg_csvb_dontlaunchapp.png &quot;DBG_CsVb_DontLaunchApp")

    - Per i progetti C++, scegliere **No dall'elenco** **Avvia** applicazione.

         ![Proprietà di debug&#43;&#43;&#47;VB avvia applicazione C](../debugger/media/dbg_cppjs_dontlaunchapp.png "DBG_CppJs_DontLaunchApp")

4. Premi **F5** per mettere l'app in modalità debug. Nota che nell'elenco **Processo** sulla barra degli strumenti **Posizione di debug** è visualizzato il nome del pacchetto dell'app per indicare che sei in modalità debug.

     ![Elenco dei processi attività in background](../debugger/media/dbg_backgroundtask_processlist.png "DBG_BackgroundTask_ProcessList")

5. Dall'elenco degli eventi sulla barra degli strumenti **Posizione di debug** scegli l'attività in background che vuoi avviare.

     ![Sospensione, ripresa, fine e attività in background](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")

## <a name="trigger-process-lifetime-management-events-and-background-tasks-from-an-installed-app"></a><a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a> Attivare Gestione del ciclo di vita dei processi eventi e attività in background da un'app installata
 Usare la **finestra di dialogo Debug** pacchetto app installato per caricare un'app già installata nel debugger. Ad esempio, è possibile eseguire il debug di un'app installata da Microsoft Store o eseguire il debug di un'app quando si hanno i file di origine per l'app, ma non un progetto Visual Studio per l'app. La finestra **di dialogo** Debug pacchetto app installato consente di avviare un'app in modalità di debug nel computer Visual Studio o in un dispositivo remoto oppure di impostare l'app per l'esecuzione in modalità di debug ma non per avviarla. Per altre informazioni, vedere Eseguire [il debug di un pacchetto dell'app installato.](../debugger/debug-installed-app-package.md)

 Una volta caricata l'app nel debugger, puoi utilizzare una qualsiasi tra le procedure descritte sopra.

## <a name="diagnosing-background-task-activation-errors"></a><a name="BKMK_Diagnosing_background_task_activation_errors"></a> Diagnosi degli errori di attivazione delle attività in background
 I log di diagnostica in Windows Visualizzatore eventi per l'infrastruttura in background contengono informazioni dettagliate che è possibile usare per diagnosticare e risolvere gli errori delle attività in background. Per visualizzare il log:

1. Aprire l'applicazione Visualizzatore eventi.

2. Nel riquadro **Azioni** scegli **Visualizza** e verificare che **Visualizza registri analitici e di debug** sia selezionata.

3. Sulla barra degli strumenti **Visualizzatore eventi (locale)** espandi i nodi **Registri applicazioni e servizi** > **Microsoft** > **Windows** > **BackgroundTasksInfrastructure**.

4. Scegli il log **Diagnostica** .

## <a name="see-also"></a>Vedi anche
- [Test delle app UWP con Visual Studio](../test/unit-test-your-code.md)
- [Eseguire il debug di app in Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
- [Ciclo di vita dell'applicazione](/windows/uwp/launch-resume/app-lifecycle)
- [Launching, resuming, and multitasking](/windows/uwp/launch-resume/index)
