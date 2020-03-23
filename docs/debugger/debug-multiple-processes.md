---
title: Eseguire il debug di più processi . Documenti Microsoft
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 160e219b6fc2ab314f8d0dd91043c18101f2c3a5
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302224"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Eseguire il debug di più processi (C, Visual Basic, C

Visual Studio può eseguire il debug di una soluzione con diversi processi. È possibile avviare e passare da un processo all'altro, interrompere, continuare ed eseguire l'origine, interrompere il debug e terminare o disconnettersi dai singoli processi.

## <a name="start-debugging-with-multiple-processes"></a>Avviare il debug con più processiStart debugging with multiple processes

Quando più di un progetto in una soluzione di Visual Studio può essere eseguito in modo indipendente, è possibile selezionare il progetto avviato dal debugger. Il progetto di avvio corrente viene visualizzato in grassetto in **Esplora soluzioni**.

Per modificare il progetto di avvio, in **Esplora soluzioni**fare clic con il pulsante destro del mouse su un progetto diverso e **scegliere Imposta come progetto di avvio**.

Per avviare il debug di un progetto da **Esplora soluzioni** senza renderlo il progetto di avvio, fare clic con il pulsante destro del mouse sul progetto e selezionare **Avvia debug** > **nuova istanza** o Esegui nella **nuova istanza**.

**Per impostare il progetto di avvio o più progetti dalle proprietà della soluzione:To set the startup project or multiple projects from solution Properties:**

1. Selezionare la soluzione in **Esplora soluzioni,** quindi selezionare l'icona **Proprietà** nella barra degli strumenti oppure fare clic con il pulsante destro del mouse sulla soluzione e scegliere **Proprietà**.

1. Nella pagina **Proprietà** selezionare Progetto di**avvio** **delle proprietà** > comuni .

   ![Modifica del tipo di avvio per un progetto](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. Selezionare **Selezione corrente**, **Progetto di avvio singolo** e un file di progetto oppure Progetti di **avvio multipli**.

   Se si seleziona **Progetti di avvio multipli**, è possibile modificare l'ordine di avvio e l'azione da eseguire per ogni progetto: **Start**, Start **without debugging**o **None**.

1. Selezionare **Applica**o **OK** per applicare e chiudere la finestra di dialogo.

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> Connettersi a un processo

Il debugger può anche *connettersi* alle app in esecuzione in processi esterni a Visual Studio, anche nei dispositivi remoti. Dopo aver eseguito la connessione a un'app, puoi usare il debugger di Visual Studio.After you attach to an app, you can use the Visual Studio debugger. Le funzionalità di debug potrebbero essere limitate. Dipende se l'app è stata compilata con le informazioni di debug, se si ha accesso al codice sorgente dell'app e se il compilatore JIT tiene traccia delle informazioni di debug.

Per ulteriori informazioni, vedere [Connettersi ai processi in esecuzione.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

**Per connettersi a un processo in esecuzione:**

1. Con l'app in esecuzione, selezionare **Esegui debug** > **da collegare a elaborare**.

   ![Finestra di dialogo Connetti a processo](../debugger/media/dbg_attachtoprocessdlg.png "Finestra di dialogo Connetti a processo")

1. Nella finestra di dialogo **Connetti a processo** selezionare il processo dall'elenco Processi **disponibili,** quindi selezionare **Connetti**.

>[!NOTE]
>Il debugger non si connette automaticamente a un processo figlio che viene avviato da un processo sottoposto a debug, anche se il progetto figlio si trova nella stessa soluzione. Per eseguire il debug di un processo figlio, connettersi al processo figlio dopo l'avvio oppure configurare l'editor del Registro di sistema di Windows per avviare il processo figlio in una nuova istanza del debugger.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Utilizzare l'editor del Registro di sistema per avviare automaticamente un processo nel debugger

In alcuni stati, potrebbe essere necessario eseguire il debug del codice di avvio per un'app avviata da un altro processo. Può ad esempio trattarsi di servizi o operazioni di installazione personalizzate. È possibile avviare il debugger e connettersi automaticamente all'app.

1. Avviare l'Editor del Registro di sistema di Windows eseguendo *regedit.exe*.

1. Nell'Editor del Registro di sistema, passare a HKEY_LOCAL_MACHINE , **Software , Microsoft Windows NT , CurrentVersion , Opzioni**di esecuzione file di immagine .

1. Selezionare la cartella dell'app da avviare nel debugger.

   Se l'app non è elencata come cartella figlio, fare clic con il pulsante destro del mouse su Opzioni di **esecuzione file**di immagine , selezionare **Nuova** > **chiave**e digitare il nome dell'app. In alternativa, fare clic con il pulsante destro del mouse sulla nuova chiave nell'albero, selezionare **Rinomina**e quindi immettere il nome dell'app.

1. Fare clic con il pulsante destro del mouse sulla nuova chiave nell'albero e selezionare **Nuovo** > **valore stringa**.

1. Modificare il nome del nuovo valore `debugger`da Nuovo valore **#1** a .

1. Fare clic con il pulsante destro del mouse su **debugger** e **scegliere Modifica**.

   ![Finestra di dialogo Modifica stringa](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "Finestra di dialogo Modifica stringa")

1. Nella finestra di dialogo `vsjitdebugger.exe` Modifica **stringa** digitare la casella Dati **valore** e quindi scegliere **OK**.

   ![Voce di avvio automatico del debug in regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "Voce di avvio automatico del debug in regedit.exe")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Eseguire il debug con più processiDebug with multiple processes
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Quando si esegue il debug di un'app con diversi processi, i comandi del debugger di interruzione, esecuzione e continuazione influiscono su tutti i processi per impostazione predefinita. Ad esempio, quando un processo viene sospeso in corrispondenza di un punto di interruzione, viene sospesa anche l'esecuzione di tutti gli altri processi. È possibile modificare questo comportamento predefinito per ottenere un maggiore controllo sulle destinazioni dei comandi di esecuzione.

**Per modificare se tutti i processi vengono sospesi quando un processo si interrompe:**

- In **Strumenti** (o **Debug**) > **Opzioni** > **di debug** > **generale**selezionare o deselezionare la casella di controllo Interrompi tutti i processi in caso di interruzione di **un processo** .

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Comandi per interrompere, eseguire le istruzioni e continuare

Nella tabella seguente vengono descritti i comportamenti dei comandi di debug quando la casella di controllo **Interrompi tutti i processi quando si interrompe un processo** è selezionata o deselezionata:

|**Comando**|Selezionato|Deselezionato|
|-|-|-|
|**Interruzione di debug**  > **tutti**|Interruzione di tutti i processi.|Interruzione di tutti i processi.|
|**Eseguire il debug** > **continua**|Ripresa di tutti i processi.|Ripresa di tutti i processi sospesi.|
|**Eseguire il debug** > **passo in**, Eseguire **l'istruzione/slittare**o **uscire da un'istruzione/ac9>debug** in , eseguire un|Esecuzione di tutti i processi durante l'esecuzione delle istruzioni del processo corrente. <br />Successiva interruzione di tutti i processi.|Esecuzione delle istruzioni del processo corrente. <br />Ripresa dei processi sospesi. <br />Continuazione dei processi in esecuzione.|
|**Eseguire il debug** > **dell'istruzione nel processo corrente**, eseguire **l'istruzione Esegui istruzione nel processo corrente**o Eseguire **l'eistruzione del processo correnteDebug** Step Into Current Process , Step Over Current Process, or Step Out Current Process|N/D|Esecuzione delle istruzioni del processo corrente.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|Punto di interruzione della finestra di **origineSource** window Breakpoint|Interruzione di tutti i processi.|Interruzione solo del processo della finestra di origine.|
|Finestra di origine **Esegui fino al cursore**<br />La finestra di origine deve essere nel processo corrente.|Esecuzione di tutti i processi mentre il processo della finestra di origine viene eseguito fino al cursore e quindi interrotto.<br />Successiva interruzione di tutti gli altri processi.|Esecuzione del processo della finestra di origine fino al cursore.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|**Finestra Processi** > **Processo di interruzione**|N/D|Interruzione del processo selezionato.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|**Finestra Processi** > **Processo di continuazione**|N/D|Ripresa del processo selezionato.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Individuare i file di origine e di simboli (con estensione pdb)
Per esplorare il codice sorgente di un processo, il debugger deve accedere ai relativi file di origine e ai file di simboli. Per altre informazioni, vedere [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Se non è possibile accedere ai file di un processo, è possibile spostarsi utilizzando la finestra **Disassembly.** Per ulteriori informazioni, vedere [Procedura: utilizzare la finestra Disassembly](../debugger/how-to-use-the-disassembly-window.md).

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Passaggio tra processi

È possibile connettersi a più processi durante il debug, ma nel debugger è attivo un solo processo alla volta. È possibile impostare il processo attivo o *corrente* nella barra degli strumenti **Posizione di debug** o nella finestra **Processi**. Per passare da un processo all'altro, entrambi i processi devono essere in modalità di interruzione.

**Per impostare il processo corrente dalla barra degli strumenti Posizione di debug:**

1. Per aprire la barra degli strumenti **Posizione di debug,** selezionare **Visualizza** > **opzioni barre degli strumenti** > **Posizione di debug**.

1. Durante il debug, nella barra degli strumenti **Posizione di debug** selezionare il processo che si desidera impostare come processo corrente dall'elenco a discesa **Processo.**

   ![Passare da un processo all'altro](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**Per impostare il processo corrente dalla finestra Processi:**

1. Per aprire la finestra **Processi** , durante il debug, selezionare **Esegui debug** > **processi****Windows** > .

1. Nella finestra **Processi,** il processo corrente è contrassegnato da una freccia gialla. Fare doppio clic sul processo che si desidera impostare come processo corrente.

   ![Finestra Processi](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Il passaggio a un processo lo imposta come processo corrente a scopo di debug. Le finestre del debugger mostrano lo stato del processo corrente e i comandi di istruzioni influiscono solo sul processo corrente.

## <a name="stop-debugging-with-multiple-processes"></a>Interrompere il debug con più processi

Per impostazione predefinita, quando si seleziona **Debug** > **Interrompi debug**, il debugger termina o si disconnette da tutti i processi.

- Se il processo corrente è stato avviato nel debugger, il processo viene terminato.

- Se il debugger è stato connesso al processo corrente, viene disconnesso e il processo rimane in esecuzione.

Se si avvia il debug di un processo da una soluzione di Visual Studio, connettersi a un altro processo già in esecuzione e quindi scegliere **Interrompi debug**, la sessione di debug termina. Il processo avviato in Visual Studio termina, mentre il processo a cui è stato associato continua l'esecuzione.

Per controllare il modo in cui **Termina debug** influisce su un singolo processo, nella finestra **Processi** fare clic con il pulsante destro del mouse su un processo e quindi selezionare o deselezionare la casella di controllo **Scollega quando il debug è stato interrotto.**

>[!NOTE]
>L'opzione **Interrompi tutti i processi quando un processo interrompe** il debugger non influisce sull'arresto, la terminazione o la disconnessione dai processi.

### <a name="stop-terminate-and-detach-commands"></a>Interrompere, terminare e disconnettere i comandi

Nella tabella seguente vengono descritti i comportamenti dei comandi stop, terminate e disconnessione del debugger con più processi:

|**Comando**|**Descrizione**|
|-|-|
|**Debug** > **Stop Debugging**|A meno che il comportamento non venga modificato nella finestra Processi, i processi **avviati** dal debugger vengono terminati e i processi collegati vengono scollegati.|
|**Termina tutto debug** > **Terminate All**|Tutti i processi sono terminati.|
|**Debug** > **Scollega tutto**|Il debugger si disconnette da tutti i processi.|
|**Finestra Processi** > **Scollega processo**|Il debugger si disconnette da tutti i processi selezionati.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|**Finestra Processi** > **Termina processo**|Il processo selezionato viene terminato.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|**Finestra Processi** > **Scollega quando il debug si interrompe**|Se l'opzione è selezionata, **la disconnessione di Debug** > **Stop Debugging** viene disconnessa dal processo selezionato. <br />Se non è selezionata, **Debug** > **Stop Debugging** termina il processo selezionato. |

## <a name="see-also"></a>Vedere anche

- [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md)
- [Debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Eseguire il debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)