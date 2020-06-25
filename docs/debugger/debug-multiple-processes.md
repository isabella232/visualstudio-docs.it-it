---
title: Eseguire il debug di più processi | Microsoft Docs
ms.date: 11/20/2018
ms.topic: how-to
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
ms.openlocfilehash: 94a61e0083b17fa095b419a2066a4f8b9c39dfb7
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350602"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Eseguire il debug di più processi (C#, Visual Basic, C++)

Visual Studio è in grado di eseguire il debug di una soluzione con diversi processi. È possibile avviare e passare da un processo all'altra, interrompere, continuare ed eseguire un'istruzione alla volta, interrompere il debug e terminare o disconnettersi dai singoli processi.

## <a name="start-debugging-with-multiple-processes"></a>Avviare il debug con più processi

Quando più di un progetto in una soluzione Visual Studio può essere eseguito in modo indipendente, è possibile selezionare il progetto avviato dal debugger. Il progetto di avvio corrente viene visualizzato in grassetto in **Esplora soluzioni**.

Per modificare il progetto di avvio, in **Esplora soluzioni**fare clic con il pulsante destro del mouse su un progetto diverso e selezionare **Imposta come progetto di avvio**.

Per avviare il debug di un progetto da **Esplora soluzioni** senza renderlo il progetto di avvio, fare clic con il pulsante destro del mouse sul progetto e scegliere **debug**  >  **Avvia nuova istanza** o **Esegui istruzione nuova istanza**.

**Per impostare il progetto di avvio o più progetti dalle proprietà della soluzione:**

1. Selezionare la soluzione in **Esplora soluzioni** , quindi selezionare l'icona **Proprietà** sulla barra degli strumenti oppure fare clic con il pulsante destro del mouse sulla soluzione e scegliere **proprietà**.

1. Nella pagina **Proprietà** selezionare progetto di **avvio proprietà comuni**  >  **Startup Project**.

   ![Modifica del tipo di avvio per un progetto](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. Selezionare **selezione corrente**, **progetto di avvio singolo** e un file di progetto o **più progetti di avvio**.

   Se si selezionano **più progetti di avvio**, è possibile modificare l'ordine di avvio e l'azione da eseguire per ogni progetto: **Start**, **Avvia senza eseguire debug**o **nessuno**.

1. Selezionare **applica**oppure **OK** per applicare e chiudere la finestra di dialogo.

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> Connettersi a un processo

Il debugger può anche essere *collegato* alle app in esecuzione in processi esterni a Visual Studio, anche su dispositivi remoti. Dopo aver eseguito la connessione a un'app, è possibile usare il debugger di Visual Studio. Le funzionalità di debug potrebbero essere limitate. Dipende dal fatto che l'app sia stata compilata con informazioni di debug, che si disponga dell'accesso al codice sorgente dell'app e che il compilatore JIT tenga traccia delle informazioni di debug.

Per ulteriori informazioni, vedere [Connetti a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Per connettersi a un processo in esecuzione:**

1. Con l'app in esecuzione, selezionare **debug**  >  **Connetti a processo**.

   ![Finestra di dialogo Connetti a processo](../debugger/media/dbg_attachtoprocessdlg.png "Finestra di dialogo Connetti a processo")

1. Nella finestra di dialogo **Connetti a processo** selezionare il processo dall'elenco **processi disponibili** e quindi selezionare **Connetti**.

>[!NOTE]
>Il debugger non si connette automaticamente a un processo figlio che viene avviato da un processo sottoposto a debug, anche se il progetto figlio si trova nella stessa soluzione. Per eseguire il debug di un processo figlio, connettersi al processo figlio dopo l'avvio oppure configurare l'editor del registro di sistema di Windows per avviare il processo figlio in una nuova istanza del debugger.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Utilizzare l'editor del registro di sistema per avviare automaticamente un processo nel debugger

In alcuni casi potrebbe essere necessario eseguire il debug del codice di avvio per un'app avviata da un altro processo. Può ad esempio trattarsi di servizi o operazioni di installazione personalizzate. È possibile avviare il debugger e connettersi automaticamente all'app.

1. Avviare l'editor del registro di sistema di Windows eseguendo *regedit.exe*.

1. Nell'editor del registro di sistema passare a **HKEY_LOCAL_MACHINE opzioni di esecuzione file di NT\CurrentVersion\Image \Software\Microsoft\Windows**.

1. Selezionare la cartella dell'app da avviare nel debugger.

   Se l'app non è elencata come cartella figlio, fare clic con il pulsante destro del mouse su **Opzioni di esecuzione file di immagine**, selezionare **nuova**  >  **chiave**e digitare il nome dell'app. In alternativa, fare clic con il pulsante destro del mouse sulla nuova chiave nell'albero, scegliere **Rinomina**e quindi immettere il nome dell'app.

1. Fare clic con il pulsante destro del mouse sulla nuova chiave nell'albero e scegliere **nuovo**  >  **valore stringa**.

1. Modificare il nome del nuovo valore da **nuovo valore #1** a `debugger` .

1. Fare clic con il pulsante destro del mouse su **debugger** e scegliere **modifica**.

   ![Finestra di dialogo Modifica stringa](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "Finestra di dialogo Modifica stringa")

1. Nella finestra di dialogo **Modifica stringa** Digitare `vsjitdebugger.exe` nella casella **dati valore** , quindi fare clic su **OK**.

   ![Voce di avvio automatico del debug in regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "Voce di avvio automatico del debug in regedit.exe")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Eseguire il debug con più processi
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Quando si esegue il debug di un'app con diversi processi, i comandi di interruzione, esecuzione di istruzioni e continuazione del debugger hanno effetto su tutti i processi per impostazione Ad esempio, quando un processo viene sospeso in corrispondenza di un punto di interruzione, viene sospesa anche l'esecuzione di tutti gli altri processi. È possibile modificare questo comportamento predefinito per ottenere un maggiore controllo sulle destinazioni dei comandi di esecuzione.

**Per modificare se tutti i processi vengono sospesi quando un processo viene interrotto:**

- In **strumenti** (o **debug**) > **Opzioni**  >  **debug**  >  **generale**selezionare o deselezionare la casella di controllo **Interrompi tutti i processi quando un processo viene interrotto** .

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Comandi per interrompere, eseguire le istruzioni e continuare

La tabella seguente descrive i comportamenti dei comandi di debug quando la casella di controllo **Interrompi tutti i processi quando si interrompe un processo** è selezionata o deselezionata:

|**Comando**|Selezionato|Deselezionato|
|-|-|-|
|**Esegui debug**   >  **Interrompi tutto**|Interruzione di tutti i processi.|Interruzione di tutti i processi.|
|**Esegui debug**  >  **Continua**|Ripresa di tutti i processi.|Ripresa di tutti i processi sospesi.|
|**Esegui debug**  >  **Esegui istruzione**, **Esegui istruzione**/routine o Esci **da istruzione** /routine|Esecuzione di tutti i processi durante l'esecuzione delle istruzioni del processo corrente. <br />Successiva interruzione di tutti i processi.|Esecuzione delle istruzioni del processo corrente. <br />Ripresa dei processi sospesi. <br />Continuazione dei processi in esecuzione.|
|**Esegui debug**  >  **Esegui istruzione processo corrente**, **Esegui istruzione/** routine o Esci **da istruzione** /routine processo corrente|N/D|Esecuzione delle istruzioni del processo corrente.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|Punto di **interruzione** della finestra di origine|Interruzione di tutti i processi.|Interruzione solo del processo della finestra di origine.|
|Finestra **di origine in esecuzione fino al cursore**<br />La finestra di origine deve essere nel processo corrente.|Esecuzione di tutti i processi mentre il processo della finestra di origine viene eseguito fino al cursore e quindi interrotto.<br />Successiva interruzione di tutti gli altri processi.|Esecuzione del processo della finestra di origine fino al cursore.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|**Processo di Break** > finestra **processi**|N/D|Interruzione del processo selezionato.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|Finestra **processi** > **continuare il processo**|N/D|Ripresa del processo selezionato.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Individuare i file di origine e di simboli (con estensione pdb)
Per esplorare il codice sorgente di un processo, il debugger deve accedere ai file di origine e ai file di simboli. Per altre informazioni, vedere [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Se non è possibile accedere ai file per un processo, è possibile spostarsi usando la finestra **Disassembly** . Per ulteriori informazioni, vedere [procedura: utilizzare la finestra Disassembly](../debugger/how-to-use-the-disassembly-window.md).

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Passaggio tra processi

Quando si esegue il debug, è possibile connettersi a più processi, ma in un determinato momento solo un processo è attivo nel debugger. È possibile impostare il processo attivo o *corrente* nella barra degli strumenti **Posizione di debug** o nella finestra **Processi**. Per passare da un processo all'altro, entrambi i processi devono essere in modalità di interruzione.

**Per impostare il processo corrente dalla barra degli strumenti posizione di debug:**

1. Per aprire la barra degli strumenti **posizione di debug** , selezionare **Visualizza**  >  **barra degli strumenti**  >  **posizione di debug**.

1. Durante il debug, sulla barra degli strumenti **posizione di debug** selezionare il processo che si desidera impostare come processo corrente dall'elenco a discesa **processo** .

   ![Passare da un processo all'altra](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**Per impostare il processo corrente dalla finestra processi:**

1. Per aprire la finestra **processi** , durante il debug, selezionare **debug**  >  **Windows**  >  **processi**Windows.

1. Nella finestra **processi** il processo corrente è contrassegnato da una freccia gialla. Fare doppio clic sul processo che si desidera impostare come processo corrente.

   ![Finestra processi](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Il passare a un processo lo imposta come processo corrente a scopo di debug. Le finestre del debugger mostrano lo stato del processo corrente e i comandi per l'esecuzione di istruzioni hanno effetto solo sul processo corrente.

## <a name="stop-debugging-with-multiple-processes"></a>Arrestare il debug con più processi

Per impostazione predefinita, quando si seleziona **debug**  >  **Interrompi debug**, il debugger termina o disconnette da tutti i processi.

- Se il processo corrente è stato avviato nel debugger, il processo viene terminato.

- Se il debugger è stato connesso al processo corrente, viene disconnesso e il processo rimane in esecuzione.

Se si avvia il debug di un processo da una soluzione di Visual Studio, quindi ci si connette a un altro processo già in esecuzione e si sceglie **Interrompi debug**, termina la sessione di debug. Il processo avviato in Visual Studio termina, mentre il processo collegato continua a funzionare.

Per controllare il modo in cui l' **arresto del debug** influisca su un singolo processo, nella finestra **processi** fare clic con il pulsante destro del mouse su un processo e quindi selezionare o deselezionare la casella di controllo Disconnetti al **termine del debug** .

>[!NOTE]
>L'opzione **Interrompi tutti i processi quando un processo interrompe** il debugger non influisce sull'arresto, la terminazione o la disconnessione dai processi.

### <a name="stop-terminate-and-detach-commands"></a>Interrompere, terminare e disconnettere i comandi

La tabella seguente descrive i comportamenti del debugger arrestare, terminare e scollegare i comandi con più processi:

|**Comando**|**Descrizione**|
|-|-|
|**Esegui debug**  >  **Arresta debug**|A meno che il comportamento non venga modificato nella finestra **processi** , i processi avviati dal debugger vengono terminati e i processi collegati vengono scollegati.|
|**Esegui debug**  >  **Termina tutto**|Tutti i processi sono stati terminati.|
|**Esegui debug**  >  **Scollega tutto**|Il debugger si disconnette da tutti i processi.|
|Finestra **processi** > **scollegare il processo**|Il debugger si disconnette da tutti i processi selezionati.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|Finestra **processi** > **Termina processo**|Il processo selezionato è terminato.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|Finestra **processi** > **scollegare quando si arresta il debug**|Se questa opzione è selezionata, **debug**  >  **Interrompi debug** disconnette dal processo selezionato. <br />Se questa opzione non è **selezionata,**  >  il debug**Interrompi debug** termina il processo selezionato. |

## <a name="see-also"></a>Vedi anche

- [Specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Connetti a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Esplorazione del codice con il debugger](../debugger/navigating-through-code-with-the-debugger.md)
- [Debug just-in-Time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Eseguire il debug di applicazioni multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)