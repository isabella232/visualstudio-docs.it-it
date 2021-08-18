---
title: Eseguire il debug di più processi | Microsoft Docs
description: Eseguire il debug di più processi in Visual Studio. Avviare e passare da un processo all'altro, interrompere, continuare, scorrere l'origine e terminare o disconnettersi da singoli processi.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 742c121b7d45f8772f8ae4d53be5282f24d4313f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031050"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Eseguire il debug di più processi (C#, Visual Basic, C++)

Visual Studio possibile eseguire il debug di una soluzione con diversi processi. È possibile avviare e passare da un processo all'altro, interrompere, continuare ed eseguire istruzioni nell'origine, arrestare il debug e terminare o disconnettersi da singoli processi.

## <a name="start-debugging-with-multiple-processes"></a>Avviare il debug con più processi

Quando più di un progetto in una Visual Studio soluzione può essere eseguito in modo indipendente, è possibile selezionare il progetto avviato dal debugger. Il progetto di avvio corrente viene visualizzato in grassetto in **Esplora soluzioni**.

Per modificare il progetto di avvio, in Esplora soluzioni fare **clic** con il pulsante destro del mouse su un progetto diverso e scegliere Imposta **come Project**.

Per avviare il debug di un **progetto Esplora soluzioni** senza impostarlo come progetto di avvio, fare clic con il pulsante destro del mouse sul progetto e scegliere **Debug** Avvia nuova istanza o Esegui  >   istruzione in nuova **istanza**.

**Per impostare il progetto di avvio o più progetti da Proprietà soluzione:**

1. Selezionare la soluzione **in** Esplora soluzioni quindi  selezionare l'icona Proprietà sulla barra degli strumenti oppure fare clic con il pulsante destro del mouse sulla soluzione e scegliere **Proprietà**.

1. Nella pagina **Proprietà** selezionare **Proprietà** comuni Avvio  >  **Project**.

   ![Modifica del tipo di avvio per un progetto](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. Selezionare **Selezione corrente,** **Progetto di avvio singolo** e un file di progetto o Progetti di avvio **multipli**.

   Se si seleziona Più progetti **di** avvio, è possibile modificare l'ordine di avvio e l'azione da eseguire per ogni progetto: **Avvia**, Avvia senza **eseguire debug** o **Nessuno**.

1. Selezionare **Applica** o **OK per** applicare e chiudere la finestra di dialogo.

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> Connettersi a un processo

Il debugger può anche *connettersi* alle app in esecuzione nei processi Visual Studio, anche nei dispositivi remoti. Dopo aver collegato un'app, è possibile usare il debugger Visual Studio app. Le funzionalità di debug potrebbero essere limitate. Dipende se l'app è stata compilata con informazioni di debug, se si ha accesso al codice sorgente dell'app e se il compilatore JIT sta verificando le informazioni di debug.

Per altre informazioni, vedere [Connettersi ai processi in esecuzione.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

**Per connettersi a un processo in esecuzione:**

1. Con l'app in esecuzione, selezionare **Esegui debug** connessione  >  **al processo**.

   ![Finestra di dialogo Collega a processo](../debugger/media/dbg_attachtoprocessdlg.png "Finestra di dialogo Connetti a processo")

1. Nella finestra **di dialogo Collega a** processo selezionare il processo dall'elenco **Processi** disponibili e quindi selezionare **Collega**.

>[!NOTE]
>Il debugger non si connette automaticamente a un processo figlio che viene avviato da un processo sottoposto a debug, anche se il progetto figlio si trova nella stessa soluzione. Per eseguire il debug di un processo figlio, connettersi al processo figlio dopo l'avvio o configurare l'editor del Registro di sistema Windows per avviare il processo figlio in una nuova istanza del debugger.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Usare l'editor del Registro di sistema per avviare automaticamente un processo nel debugger

A volte potrebbe essere necessario eseguire il debug del codice di avvio per un'app avviata da un altro processo. Può ad esempio trattarsi di servizi o operazioni di installazione personalizzate. È possibile avviare il debugger e connettersi automaticamente all'app.

1. Avviare l'Windows del Registro di sistema eseguendo *regedit.exe*.

1. Nell'editor del Registro di sistema passare **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options**.

1. Selezionare la cartella dell'app da avviare nel debugger.

   Se l'app non è elencata come cartella figlio, fare clic con il pulsante destro del mouse su Opzioni di esecuzione **file** di immagine , selezionare **Nuova**  >  **chiave** e digitare il nome dell'app. In caso contrario, fare clic con il pulsante destro del mouse sulla nuova chiave nell'albero, **scegliere Rinomina** e quindi immettere il nome dell'app.

1. Fare clic con il pulsante destro del mouse sulla nuova chiave nell'albero e **scegliere Nuovo valore**  >  **stringa**.

1. Modificare il nome del nuovo valore da **New Value #1** in `debugger` .

1. Fare clic con il **pulsante destro** del mouse sul debugger e **scegliere Modifica**.

   ![Finestra di dialogo Modifica stringa](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "Finestra di dialogo Modifica stringa")

1. Nella finestra **di dialogo Modifica** stringa digitare nella casella Dati `vsjitdebugger.exe` **valore** e quindi selezionare **OK**.

   ![Voce di avvio automatico del debug in regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "Voce di avvio automatico del debug in regedit.exe")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Eseguire il debug con più processi
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Quando si esegue il debug di un'app con più processi, i comandi di interruzione, esecuzione di istruzioni e continuazione del debugger influiscono su tutti i processi per impostazione predefinita. Ad esempio, quando un processo viene sospeso in corrispondenza di un punto di interruzione, viene sospesa anche l'esecuzione di tutti gli altri processi. È possibile modificare questo comportamento predefinito per ottenere un maggiore controllo sulle destinazioni dei comandi di esecuzione.

**Per modificare se tutti i processi vengono sospesi in caso di interruzione di un processo:**

- In **Strumenti** (o **Debug**) > Opzioni di debug generale selezionare o deselezionare la casella di controllo Interrompi tutti i processi in caso di  >    >  interruzione **di un** processo.

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Comandi per interrompere, eseguire le istruzioni e continuare

Nella tabella seguente vengono descritti i comportamenti  dei comandi di debug quando la casella di controllo Interrompi tutti i processi in caso di interruzione di un processo è selezionata o deselezionata:

|**Comando**|Opzione selezionata|Deselezionato|
|-|-|-|
|**Eseguire il debug**   >  **Interrompi tutto**|Interruzione di tutti i processi.|Interruzione di tutti i processi.|
|**Eseguire il debug**  >  **Continua**|Ripresa di tutti i processi.|Ripresa di tutti i processi sospesi.|
|**Eseguire il debug**  >  **Eseguire un'istruzione,** **un'istruzione** o **un'istruzione/uscita**|Esecuzione di tutti i processi durante l'esecuzione delle istruzioni del processo corrente. <br />Successiva interruzione di tutti i processi.|Esecuzione delle istruzioni del processo corrente. <br />Ripresa dei processi sospesi. <br />Continuazione dei processi in esecuzione.|
|**Eseguire il debug**  >  **Eseguire un'istruzione nel processo corrente,** **eseguire il passaggio del processo corrente** o uscire dal processo **corrente**|N/A|Esecuzione delle istruzioni del processo corrente.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|Punto di interruzione della finestra **di origine**|Interruzione di tutti i processi.|Interruzione solo del processo della finestra di origine.|
|Finestra di origine **Esegui fino al cursore**<br />La finestra di origine deve essere nel processo corrente.|Esecuzione di tutti i processi mentre il processo della finestra di origine viene eseguito fino al cursore e quindi interrotto.<br />Successiva interruzione di tutti gli altri processi.|Esecuzione del processo della finestra di origine fino al cursore.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|**Finestra Processi >** **processo di interruzione**|N/A|Interruzione del processo selezionato.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|**Finestra Processi** > **Continua processo**|N/A|Ripresa del processo selezionato.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Individuare i file di origine e di simboli (con estensione pdb)
Per spostarsi nel codice sorgente di un processo, il debugger deve accedere ai file di origine e ai file di simboli. Per altre informazioni, vedere [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Se non è possibile accedere ai file per un processo, è possibile spostarsi usando la **finestra Disassembly.** Per altre informazioni, vedere [Procedura: Usare la finestra Disassembly](../debugger/how-to-use-the-disassembly-window.md).

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Passaggio tra processi

È possibile connettersi a più processi durante il debug, ma nel debugger è attivo un solo processo in un determinato momento. È possibile impostare il processo attivo o *corrente* nella barra degli strumenti **Posizione di debug** o nella finestra **Processi**. Per passare da un processo all'altro, entrambi i processi devono essere in modalità di interruzione.

**Per impostare il processo corrente dalla barra degli strumenti Percorso di debug:**

1. Per aprire la barra **degli strumenti Percorso di** debug, selezionare Visualizza **barre** degli strumenti  >  **Percorso** di  >  **debug**.

1. Durante il debug, nella barra **degli strumenti Posizione** di debug selezionare il processo che si vuole impostare come processo corrente dall'elenco a **discesa** Processo.

   ![Passare da un processo all'altro](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**Per impostare il processo corrente dalla finestra Processi:**

1. Per aprire la **finestra Processi** durante il debug, selezionare **Debug**  >  **Windows**  >  **processi**.

1. Nella finestra **Processi il** processo corrente è contrassegnato da una freccia gialla. Fare doppio clic sul processo che si desidera impostare come processo corrente.

   ![Finestra Processi](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Il passaggio a un processo lo imposta come processo corrente a scopo di debug. Le finestre del debugger mostrano lo stato del processo corrente e i comandi di esecuzione di istruzioni influiscono solo sul processo corrente.

## <a name="stop-debugging-with-multiple-processes"></a>Arrestare il debug con più processi

Per impostazione predefinita, quando si seleziona **Debug**  >  **Arresta debug**, il debugger termina o si disconnette da tutti i processi.

- Se il processo corrente è stato avviato nel debugger, il processo viene terminato.

- Se il debugger è stato connesso al processo corrente, viene disconnesso e il processo rimane in esecuzione.

Se si avvia il debug di un processo da una soluzione Visual Studio, quindi ci si connette a un altro processo già in esecuzione e quindi si sceglie Arresta debug **,** la sessione di debug termina. Il processo avviato in Visual Studio termina, mentre il processo a cui si è collegati continua a essere in esecuzione.

Per controllare il  modo in cui Arresta  debug influisce su un singolo processo, nella finestra Processi fare clic con il pulsante destro del mouse su un processo e quindi selezionare o deselezionare la casella di controllo Disconnetti all'arresto **del** debug .

>[!NOTE]
>**L'opzione Interrompi** tutti i processi quando un processo interrompe il debugger non influisce sull'arresto, la chiusura o la disconnessione dai processi.

### <a name="stop-terminate-and-detach-commands"></a>Interrompere, terminare e disconnettere i comandi

Nella tabella seguente vengono descritti i comportamenti dei comandi di arresto, terminazione e disconnessione del debugger con più processi:

|**Comando**|**Descrizione**|
|-|-|
|**Eseguire il debug**  >  **Arresta debug**|A meno che il  comportamento non venga modificato nella finestra Processi, i processi avviati dal debugger vengono terminati e i processi collegati vengono scollegati.|
|**Eseguire il debug**  >  **Termina tutto**|Tutti i processi vengono terminati.|
|**Eseguire il debug**  >  **Scollega tutto**|Il debugger si disconnette da tutti i processi.|
|**Finestra Processi** > **processo di scollegamento**|Il debugger si disconnette da tutti i processi selezionati.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|**Finestra Processi** > **Termina processo**|Il processo selezionato è terminato.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|**Finestra Processi >** **scollegamento all'arresto del debug**|Se questa opzione è **selezionata,**  >  **Debug Arresta** debug si disconnette dal processo selezionato. <br />Se non è selezionata, **Debug**  >  **Arresta debug termina** il processo selezionato. |

## <a name="see-also"></a>Vedi anche

- [Specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Connettersi ai processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Esplorazione del codice con il debugger](../debugger/navigating-through-code-with-the-debugger.md)
- [Debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Eseguire il debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)