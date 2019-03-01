---
title: Eseguire il debug di più processi | Microsoft Docs
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
ms.openlocfilehash: 5d9c592663e32b8050644d459b8db45f3f0f5307
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630743"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Eseguire il debug di più processi (C#, Visual Basic, C++)

Visual Studio può eseguire il debug di una soluzione con più processi. È possibile avviare e passare tra processi, interrompere, continuare e passaggio origine, arrestare il debug e la fine o disconnettersi dai singoli processi.

## <a name="start-debugging-with-multiple-processes"></a>Avviare il debug con più processi

Quando più di un progetto in una soluzione di Visual Studio è possibile eseguire in modo indipendente, è possibile selezionare il progetto di avvio del debugger. Il progetto di avvio corrente viene visualizzato grassetto nel **Esplora soluzioni**.

Per modificare il progetto di avvio, in **Esplora soluzioni**, fare doppio clic su un altro progetto e selezionare **imposta come progetto di avvio**.

Per avviare il debug di un progetto dal **Esplora soluzioni** senza rendere il progetto di avvio, fare clic sul progetto e selezionare **Debug** > **Avvia nuova istanza** oppure **Esegui istruzione nuova istanza**.

**Per impostare il progetto di avvio o più progetti dalla soluzione proprietà:**

1. Selezionare la soluzione in **Esplora soluzioni** e quindi selezionare la **delle proprietà** icona nella barra degli strumenti o scelta la soluzione e selezionare **proprietà**.

1. Nel **delle proprietà** pagina, selezionare **proprietà comuni** > **progetto di avvio**.

   ![Modifica del tipo di avvio per un progetto](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. Selezionare **selezione corrente**, **progetto di avvio singolo** e un file di progetto, o **progetti di avvio multipli**.

   Se si seleziona **progetti di avvio multipli**, è possibile modificare l'ordine di avvio e l'azione da intraprendere per ogni progetto: **avviare**, **Avvia senza eseguire debug**, oppure **Nessuno**.

1. Selezionare **Apply**, o **OK** per applicare e chiudere la finestra di dialogo.

###  <a name="BKMK_Attach_to_a_process"></a> Connettersi a un processo

Il debugger può inoltre *collegare* alle App in esecuzione in processi esterni a Visual Studio, tra cui su dispositivi remoti. Dopo aver collegato a un'app, è possibile usare il debugger di Visual Studio. Le funzionalità di debug potrebbero essere limitata. Dipende se l'app è stata compilata con le informazioni di debug, se si ha accesso al codice sorgente dell'app e che il compilatore JIT stia registrando informazioni di debug.

Per altre informazioni, vedere [Collega a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Per connettersi a un processo in esecuzione:**

1. Con l'app in esecuzione, selezionare **Debug** > **Connetti a processo**.

   ![Collegamento alla finestra di dialogo di processo](../debugger/media/dbg_attachtoprocessdlg.png "associare alla finestra di dialogo di processo")

1. Nel **Connetti a processo** finestra di dialogo, selezionare il processo dalle **processi disponibili** elenco e quindi selezionare **Attach**.

>[!NOTE]
>Il debugger non si connette automaticamente a un processo figlio che viene avviato da un processo sottoposto a debug, anche se il progetto figlio si trova nella stessa soluzione. Per eseguire il debug di un processo figlio, connettersi al processo figlio dopo l'avvio o configurare l'Editor del Registro di sistema di Windows per avviare il processo figlio in una nuova istanza del debugger.

###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Usare l'Editor del Registro di sistema per avviare automaticamente un processo nel debugger

In alcuni casi, potrebbe essere necessario eseguire il debug di codice di avvio di un'app che viene avviata da un altro processo. Può ad esempio trattarsi di servizi o operazioni di installazione personalizzate. Il debugger è possibile avviare e allegare automaticamente all'app.

1. Avviare l'Editor del Registro di sistema di Windows eseguendo *regedit.exe*.

1. Nell'Editor del Registro di sistema passare a **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options**.

1. Selezionare la cartella dell'app da avviare nel debugger.

   Se l'app non è elencato come cartella figlio, fare doppio clic su **Image File Execution Options**, selezionare **New** > **chiave**e digitare il nome dell'app. In alternativa, fare doppio clic la nuova chiave nell'albero della selezione **Rinomina**, quindi immettere il nome dell'app.

1. Fare doppio clic la nuova chiave nella struttura ad albero e selezionare **New** > **valore stringa**.

1. Modificare il nome del nuovo valore da **nuovo valore #1** a `debugger`.

1. Fare doppio clic su **debugger** e selezionare **Modify**.

   ![Dialogo Modifica stringa](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "nella finestra di dialogo Modifica stringa")

1. Nel **Modifica stringa** finestra di dialogo, digitare `vsjitdebugger.exe` nel **dati valore** e quindi selezionare **OK**.

   ![Voce di avvio automatico del debug Regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "voce di avvio automatico del debug Regedit.exe")

##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Eseguire il debug con più processi
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Durante il debug di un'app con più processi, i comandi del debugger di interruzione, debug passo a passo e continui interessano tutti i processi per impostazione predefinita. Ad esempio, quando un processo viene sospeso in corrispondenza di un punto di interruzione, viene sospesa anche l'esecuzione di tutti gli altri processi. È possibile modificare questo comportamento predefinito per ottenere un maggiore controllo sulle destinazioni dei comandi di esecuzione.

**Per modificare la modalità di tutti i processi vengono sospese quando si interrompe un processo:**

- Sotto **degli strumenti** (o **Debug**) > **opzioni** > **debug** > **generale**, selezionare o deselezionare le **quando si interrompe un processo, interrompi tutti i processi** casella di controllo.

###  <a name="BKMK_Break__step__and_continue_commands"></a> Comandi per interrompere, eseguire le istruzioni e continuare

Nella tabella seguente vengono descritti i comportamenti del debug comandi quando il **quando si interrompe un processo, interrompi tutti i processi** casella di controllo viene selezionata o deselezionata:

|**Comando**|Selezionato|Deselezionato|
|-|-|-|
|**Eseguire il debug**  > **Interrompi tutto**|Interruzione di tutti i processi.|Interruzione di tutti i processi.|
|**Eseguire il debug** > **continuare**|Ripresa di tutti i processi.|Ripresa di tutti i processi sospesi.|
|**Eseguire il debug** > **eseguire l'istruzione**, **Esegui istruzione/routine**, o **Esci da istruzione**|Esecuzione di tutti i processi durante l'esecuzione delle istruzioni del processo corrente. <br />Successiva interruzione di tutti i processi.|Esecuzione delle istruzioni del processo corrente. <br />Ripresa dei processi sospesi. <br />Continuazione dei processi in esecuzione.|
|**Eseguire il debug** > **Esegui istruzione processo corrente**, **Esegui istruzione/routine processo corrente**, o **Esci da processo corrente**|N/D|Esecuzione delle istruzioni del processo corrente.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|Finestra di dialogo origine **punto di interruzione**|Interruzione di tutti i processi.|Interruzione solo del processo della finestra di origine.|
|Finestra di dialogo origine **Esegui fino al cursore**<br />La finestra di origine deve essere nel processo corrente.|Esecuzione di tutti i processi mentre il processo della finestra di origine viene eseguito fino al cursore e quindi interrotto.<br />Successiva interruzione di tutti gli altri processi.|Esecuzione del processo della finestra di origine fino al cursore.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|**I processi** finestra > **Interrompi processo**|N/D|Interruzione del processo selezionato.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|**I processi** finestra > **Continua processo**|N/D|Ripresa del processo selezionato.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|

###  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Individuare i file di origine e di simboli (con estensione pdb)
Per esplorare il codice sorgente di un processo, il debugger deve accedere ai relativi file di origine e i file di simboli. Per altre informazioni, vedere [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Se è Impossibile accedere ai file per un processo, è possibile spostarsi usando il **Disassembly** finestra. Per altre informazioni, vedere [procedura: utilizzare la finestra Disassembly](../debugger/how-to-use-the-disassembly-window.md).

###  <a name="BKMK_Switch_between_processes"></a> Passaggio tra processi

È possibile connettersi a più processi quando si esegue il debug, ma è attivo nel debugger di un solo processo in qualsiasi momento. È possibile impostare il processo attivo o *corrente* nella barra degli strumenti **Posizione di debug** o nella finestra **Processi**. Per passare da un processo all'altro, entrambi i processi devono essere in modalità di interruzione.

**Per impostare il processo corrente nella barra degli strumenti posizione di Debug:**

1. Per aprire la **posizione di Debug** sulla barra degli strumenti, seleziona **View** > **barre degli strumenti** > **posizione di Debug**.

1. Durante il debug, scegliere il **posizione di Debug** sulla barra degli strumenti, selezionare il processo di cui si desidera impostare come corrente dalle **processo** elenco a discesa.

   ![Spostarsi tra i processi](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**Per impostare il processo corrente dalla finestra processi:**

1. Per aprire la **processi** finestra durante il debug, selezionare **Debug** > **Windows** > **processi**.

1. Nel **processi** finestra, il processo corrente è contrassegnata da una freccia gialla. Fare doppio clic il processo di cui che si desidera impostare come corrente.

   ![Finestra processi](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Il passaggio a un processo, lo imposta come processo corrente a scopo di debug. Finestre del debugger mostrano lo stato del processo corrente e i comandi di esecuzione di istruzioni interessano solo processo corrente.

## <a name="stop-debugging-with-multiple-processes"></a>Arrestare il debug con più processi

Per impostazione predefinita, quando si seleziona **Debug** > **arresta debug**, il debugger termina o disconnette tutti i processi.

- Se il processo corrente è stato avviato nel debugger, il processo viene terminato.

- Se il debugger è stato connesso al processo corrente, viene disconnesso e il processo rimane in esecuzione.

Se si avvia il debug di un processo da una soluzione di Visual Studio, quindi collegare a un altro processo che è già in esecuzione e quindi scegliere **arresta debug**, il termine della sessione di debug. Termina il processo che è stato avviato in Visual Studio, mentre il processo a che sono stati collegati rimane in esecuzione.

Per controllare la modalità che **Termina debug** influisce su un singolo processo, il **processi** finestra, fare doppio clic su un processo e quindi selezionare o deselezionare il **Disconnetti al termine del debug arrestato** casella di controllo.

>[!NOTE]
>Il **quando si interrompe un processo, interrompi tutti i processi** debugger opzione non riguarda l'arresto, interruzione o disconnessione dai processi.

### <a name="stop-terminate-and-detach-commands"></a>Interrompere, terminare e disconnettere i comandi

Nella tabella seguente vengono descritti i comportamenti dell'interruzione del debugger, terminare e disconnettere i comandi con più processi:

|**Comando**|**Descrizione**|
|-|-|
|**Eseguire il debug** > **interrompere il debug**|A meno che non viene modificato il comportamento nel **processi** finestra processi avviati dal debugger vengono terminati e processi connessi vengono disconnessi.|
|**Eseguire il debug** > **Termina tutto**|Tutti i processi vengono terminati.|
|**Eseguire il debug** > **Disconnetti tutto**|Il debugger si disconnette da tutti i processi.|
|**I processi** finestra > **Disconnetti processo**|Il debugger si disconnette da tutti i processi selezionati.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|**I processi** finestra > **Termina processo**|Il processo selezionato viene terminato.<br />Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|
|**I processi** finestra > **Disconnetti al termine del debug**|Se selezionato, **Debug** > **arresta debug** si disconnette dal processo selezionato. <br />Se non è selezionata **Debug** > **arresta debug** termina il processo selezionato. |

## <a name="see-also"></a>Vedere anche

- [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Spostarsi nel codice con il debugger](../debugger/navigating-through-code-with-the-debugger.md)
- [Debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Eseguire il debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)