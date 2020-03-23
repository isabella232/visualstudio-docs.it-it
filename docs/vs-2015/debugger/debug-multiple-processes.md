---
title: Eseguire il debug di più processi . Documenti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a2679825d41a6360dde05e7511d607f8be69dfa
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302553"
---
# <a name="debug-multiple-processes"></a>Eseguire il debug di più processi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Viene illustrato come avviare i processi di debug, passare da un processo all'altro, interrompere e continuare l'esecuzione, eseguire l'origine un'istruzione alla volta, interrompere il debug e terminare o disconnettersi dai processi.  
  
## <a name="contents"></a><a name="BKMK_Contents"></a>Contenuto  
 [Configurare il comportamento di esecuzione di più processi](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Trovare i file di origine e di simbolo (con estensione pdb)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Avviare più processi in una soluzione VS, connettersi a un processo, avviare automaticamente un processo nel debugger](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Cambia processo, interrompi e continua l'esecuzione, passa attraverso l'origine](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Interrompere il debug, terminare o disconnettersi dai processi](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
## <a name="configure-the-execution-behavior-of-multiple-processes"></a><a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>Configurare il comportamento di esecuzione di più processi  
 Per impostazione predefinita, quando più processi sono in esecuzione nel debugger, i comandi del debugger di interruzione, esecuzione delle istruzioni e arresto di solito interessano tutti i processi. Ad esempio, quando un processo viene sospeso in corrispondenza di un punto di interruzione, viene sospesa anche l'esecuzione di tutti gli altri processi. È possibile modificare questo comportamento predefinito per ottenere un maggiore controllo sulle destinazioni dei comandi di esecuzione.  
  
1. Scegliere **Opzioni e impostazioni** dal menu **Debug**.  
  
2. Nella **Debugging**pagina **Debug , Generale** deselezionare la casella di controllo Interrompi tutti i processi in caso di interruzione di **un processo.**  
  
   ![Torna al contenuto superiore](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Individuare i file di origine e di simboli (con estensione pdb)  
 Per esplorare il codice sorgente di un processo, il debugger deve accedere ai file di origine e di simboli del processo. Consultate [Specificare i file di simboli (con estensione pdb) e di origine.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
 Se non è possibile accedere ai file per un processo, è possibile spostarsi utilizzando la finestra Disassembly. Vedere [Procedura: utilizzare la finestra Disassembly](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Torna al contenuto superiore](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="start-multiple-processes-in-a-vs-solution-attach-to-a-process-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a>Avviare più processi in una soluzione VS, connettersi a un processo, avviare automaticamente un processo nel debuggerStart multiple processes in a VS solution, attach to a process, automatically start a process in the debugger  
  
- [Avviare il debug di più processi in una soluzione](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) di Visual Studio - Modificare il progetto di [avvio](#BKMK_Change_the_startup_project) - [Avviare un progetto specifico in una soluzione](#BKMK_Start_a_specific_project_in_a_solution) - [Avviare più progetti in una soluzione](#BKMK_Start_multiple_projects_in_a_solution) - [Connettersi a un processo](#BKMK_Attach_to_a_process) - [Avviare automaticamente un processo nel debugger](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
> Il debugger non si connette automaticamente a un processo figlio che viene avviato da un processo sottoposto a debug, anche se il progetto figlio si trova nella stessa soluzione. Per eseguire il debug di un processo figlio:  
> 
> - Connettersi al processo figlio dopo averlo avviato.  
> 
>   -oppure-  
>   - Configurare Windows per avviare automaticamente il processo figlio in una nuova istanza del debugger.  
  
### <a name="start-debugging-multiple-processes-in-a-visual-studio-solution"></a><a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a>Avviare il debug di più processi in una soluzione di Visual StudioStart debugging multiple processes in a Visual Studio solution  
 Quando sono presenti più progetti in una soluzione Visual Studio che è possibile eseguire in modo indipendente (progetti eseguiti in processi distinti), è possibile selezionare quali progetti vengono avviati dal debugger.  
  
 ![Modifica del tipo di avvio per un progetto](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
#### <a name="change-the-startup-project"></a><a name="BKMK_Change_the_startup_project"></a>Modificare il progetto di avvio  
 Per modificare il progetto di avvio per una soluzione, selezionare il progetto in Esplora soluzioni, quindi scegliere Imposta come progetto di **avvio** dal menu di scelta rapida.  
  
#### <a name="start-a-specific-project-in-a-solution"></a><a name="BKMK_Start_a_specific_project_in_a_solution"></a>Avviare un progetto specifico in una soluzioneStart a specific project in a solution  
 Per avviare un progetto per una soluzione senza modificare il progetto di avvio predefinito, selezionare il progetto in Esplora soluzioni, quindi scegliere **Debug** dal menu di scelta rapida. È quindi possibile scegliere **Avvia nuova istanza** o Esegui istruzione nuova **istanza**.  
  
 ![Torna all'inizio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Avviare più processi in una soluzione VS, connettersi a un processo, avviare automaticamente un processo nel debugger](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Torna al contenuto superiore](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
#### <a name="start-multiple-projects-in-a-solution"></a><a name="BKMK_Start_multiple_projects_in_a_solution"></a>Avviare più progetti in una soluzioneStart multiple projects in a solution  
  
1. Selezionare la soluzione in Esplora soluzioni, quindi scegliere **Proprietà** dal menu di scelta rapida.  
  
2. Selezionare **Proprietà comuni**, **Progetto di avvio** nella finestra di dialogo **Proprietà** .  
  
3. Per ogni progetto che si desidera modificare, scegliere **Avvia**, **Avvia senza eseguire debug**o **Nessuno**.  
  
   ![Torna all'inizio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Avviare più processi in una soluzione VS, connettersi a un processo, avviare automaticamente un processo nel debugger](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![Torna al contenuto superiore](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> Connettersi a un processo  
 Il debugger può anche *connettersi* a programmi in esecuzione in processi esterni a Visual Studio, inclusi i programmi in esecuzione in un dispositivo remoto. Dopo essersi connessi a un programma, è possibile usare i comandi di esecuzione del debugger, analizzare lo stato del programma e così via. La possibilità di analisi del programma dipende dall'eventualità che il programma sia stato generato con informazioni di debug, che si disponga dell'accesso al relativo codice sorgente e che il compilatore JIT di Common Language Runtime stia registrando informazioni di debug.  
  
 Per ulteriori informazioni, vedere [Connettersi a processi in esecuzione.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
 **Connettersi a un processo in esecuzione nel computer locale**  
  
 Scegliere **Debug**, **Connetti a processo**. Nella finestra di dialogo **Connetti a processo** selezionare il processo dall'elenco Processi **disponibili** e quindi scegliere **Connetti**.  
  
 ![Finestra di dialogo Connetti a processo](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Torna al contenuto superiore](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
### <a name="automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Avvia automaticamente un processo nel debuggerAutomatically start a process in the debugger  
 In alcuni casi potrebbe essere necessario eseguire il debug del codice di avvio di un programma avviato da un altro processo. Può ad esempio trattarsi di servizi o operazioni di installazione personalizzate. In questi scenari è possibile avviare e connettere il debugger automaticamente all'avvio dell'applicazione.  
  
1. Avviare l'Editor del Registro di sistema (**regedit.exe**).  
  
2. Spostarsi nella cartella HKEY_LOCAL_MACHINE , Software , **Microsoft Windows NT , CurrentVersion , Image File Execution Options** .  
  
3. Selezionare la cartella dell'app da avviare nel debugger.  
  
    Se il nome dell'app non è elencato come cartella figlio, selezionare Opzioni di esecuzione file di **immagine,** quindi scegliere **Nuovo**, **Chiave** dal menu di scelta rapida. Selezionare la nuova chiave, scegliere **Rinomina** dal menu di scelta rapida, quindi immettere il nome dell'app.  
  
4. Nel menu di scelta rapida della cartella dell'app scegliere **Nuovo**, **Valore stringa**.  
  
5. Modificare il nome del nuovo valore `debugger`da Nuovo **valore** a .  
  
6. Nel menu di scelta rapida della voce del debugger scegliere **Modifica**.  
  
7. Nella finestra di dialogo `vsjitdebugger.exe` Modifica stringa digitare la casella **Dati valore.**  
  
    ![Finestra di dialogo Modifica stringa](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Voce di avvio automatico del debug in regedit.exe](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![Torna al contenuto superiore](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="switch-processes-break-and-continue-execution-step-through-source"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Cambia processo, interrompi e continua l'esecuzione, passa attraverso l'origine  
  
- [Passare da un processo all'altro:](#BKMK_Switch_between_processes) [interrompere, eseguire il passaggio e continuare](#BKMK_Break__step__and_continue_commands) i comandi  
  
### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Passaggio tra processi  
 Nonostante durante il debug sia possibile connettersi a più processi, nel debugger è sempre attivo un solo processo in un dato momento. È possibile impostare il processo attivo o *corrente* nella barra degli strumenti Posizione di debug o nella finestra **Processi.** Per passare da un processo all'altro, entrambi i processi devono essere in modalità di interruzione.  
  
 **Per impostare il processo corrente**  
  
- Nella barra degli strumenti Posizione di debug scegliere **Processo** per visualizzare la casella di riepilogo **Processo.** Selezionare il processo da designare come processo corrente.  
  
   ![Passare da un processo all'altro](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   Se la barra degli strumenti **Posizione di debug** non è visibile, scegliere **Strumenti**, **Personalizza**. Nella scheda **Barre degli strumenti** scegliere Percorso di **debug**.  
  
- Aprire la finestra **Processi** (tasto di scelta rapida **Ctrl - Alt )** individuare il processo che si desidera impostare come processo corrente e fare doppio clic su di esso.  
  
   ![Finestra Processi](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   Il processo corrente è contrassegnato da una freccia gialla.  
  
  Quando si passa a un progetto esso viene impostato per il debug. In tutte le finestre del debugger visualizzate è mostrato lo stato del processo corrente e tutti i comandi per l'esecuzione di istruzioni interessano solo il processo corrente.  
  
  ![Torna all'inizio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Switch processi, interrompere e continuare l'esecuzione, passo attraverso l'origine](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![Torna al contenuto superiore](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Comandi per interrompere, eseguire le istruzioni e continuare  
  
> [!NOTE]
> Per impostazione predefinita, i comandi del debugger per interrompere, continuare ed eseguire le istruzioni interessano tutti i processi sottoposti a debug. Per modificare questo comportamento, vedere [Configurare il comportamento di esecuzione di più processiTo](#BKMK_Configure_the_execution_behavior_of_multiple_processes) change this behavior, see Configure the execution behavior of multiple processes  
  
||||  
|-|-|-|  
|**Comando**|**Interrompi tutti i processi in caso di interruzione di un processo**<br /><br /> Selezionato (impostazione predefinita)|**Interrompi tutti i processi in caso di interruzione di un processo**<br /><br /> Cancellato|  
|**Menu Debug:**<br /><br /> -   **Interrompi tutto**|Interruzione di tutti i processi.|Interruzione di tutti i processi.|  
|**Menu Debug:**<br /><br /> -   **Continuare**|Ripresa di tutti i processi.|Ripresa di tutti i processi sospesi.|  
|**Menu Debug:**<br /><br /> -   **Entra in**<br />-   **Passo oltre**<br />-   **Esci**|Esecuzione di tutti i processi durante l'esecuzione delle istruzioni del processo corrente.<br /><br /> Successiva interruzione di tutti i processi.|Esecuzione delle istruzioni del processo corrente.<br /><br /> Ripresa dei processi sospesi.<br /><br /> Continuazione dei processi in esecuzione.|  
|**Menu Debug:**<br /><br /> -   **Entra nel processo corrente**<br />-   **Passo oltre il processo corrente**<br />-   **Estrai processo corrente**|N/D|Esecuzione delle istruzioni del processo corrente.<br /><br /> Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|  
|Finestra di origine<br /><br /> -   **Interruzione**|Interruzione di tutti i processi.|Interruzione solo del processo della finestra di origine.|  
|Menu di scelta rapida della finestra di origine:<br /><br /> -   **Esegui fino al cursore**<br /><br /> La finestra di origine deve essere nel processo corrente.|Esecuzione di tutti i processi mentre il processo della finestra di origine viene eseguito fino al cursore e quindi interrotto.<br /><br /> Successiva interruzione di tutti gli altri processi.|Esecuzione del processo della finestra di origine fino al cursore.<br /><br /> Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|  
|Menu di scelta rapida della finestra **Processi:**<br /><br /> -   **Interrompi processo**|N/D|Interruzione del processo selezionato.<br /><br /> Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|  
|Menu di scelta rapida della finestra **Processi:**<br /><br /> -   **Continua processo**|N/D|Ripresa del processo selezionato.<br /><br /> Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|  
  
 ![Torna all'inizio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Switch processi, interrompere e continuare l'esecuzione, passo attraverso l'origine](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Torna al contenuto superiore](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="stop-debugging-terminate-or-detach-from-processes"></a><a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a>Interrompere il debug, terminare o disconnettersi dai processi  
  
- [Interrompere, terminare e disconnettere i comandi](#BKMK_Stop__terminate__and_detach_commands)  
  
  Per impostazione predefinita, quando si sceglie **Debug**, **Interrompi debug** quando più processi sono aperti nel debugger, il debugger termina o si disconnette da tutti i processi a seconda di come il processo è stato aperto nel debugger:  
  
- Se il processo corrente è stato avviato nel debugger, esso viene terminato.  
  
- Se il debugger è stato connesso al processo corrente, viene disconnesso e il processo rimane in esecuzione.  
  
  Ad esempio, se si avvia il debug di un processo da una soluzione di Visual Studio, ci si connette a un altro processo già in esecuzione e quindi si sceglie **Interrompi debug**, la sessione di debug termina, il processo avviato in Visual Studio viene terminato, mentre il processo collegato viene lasciato in esecuzione. È possibile utilizzare le procedure seguenti per controllare la modalità di interruzione del debug.  
  
> [!NOTE]
> L'opzione **Interrompi tutti i processi quando si interrompe un processo** non influisce sull'interruzione del debug o della terminazione e della disconnessione dai processi.  
  
 **Per modificare gli effetti dell'interruzione del debug su un singolo processo**  
  
- Aprire la finestra **Processi** (tasto di scelta rapida **Ctrl .**. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . Selezionare un processo e quindi selezionare o deselezionare la casella di controllo Scollega quando il **debug è stato interrotto.**  
  
### <a name="stop-terminate-and-detach-commands"></a><a name="BKMK_Stop__terminate__and_detach_commands"></a>Interrompere, terminare e scollegare i comandi  
  
|||  
|-|-|  
|**Comando**|**Descrizione**|  
|**Menu Debug:**<br /><br /> -   **Interrompi debug**|A meno che il comportamento non venga modificato dall'opzione Disconnessione finestra **Processi** **durante l'arresto del debug:**<br /><br /> 1. I processi avviati dal debugger vengono terminati.<br />2. I processi collegati vengono scollegati dal debugger.|  
|**Menu Debug:**<br /><br /> -   **Termina tutto**|Tutti i processi vengono terminati.|  
|**Menu Debug:**<br /><br /> -   **Scollega tutto**|Il debugger si disconnette da tutti i processi.|  
|Menu di scelta rapida della finestra **Processi:**<br /><br /> -   **Scollega processo**|Il debugger si disconnette da tutti i processi selezionati.<br /><br /> Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|  
|Menu di scelta rapida della finestra **Processi:**<br /><br /> -   **Termina processo**|Il processo selezionato viene terminato.<br /><br /> Mantenimento dello stato esistente (sospeso o in esecuzione) degli altri processi.|  
|Menu di scelta rapida della finestra **Processi:**<br /><br /> -   **Scollega quando il debug si interrompe**|Attiva o disattiva il comportamento di **Debug**, **Interrompi debug** per il processo selezionato:<br /><br /> - Checked: il debugger si disconnette dal processo.- Checked: The debugger detaches from the process.<br />- Cancellato: il processo è terminato.|  
  
 ![Torna all'inizio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Interrompere il debug, terminare o disconnettersi dai processi](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Torna al contenuto superiore](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="see-also"></a>Vedere anche  
 [Specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Connetti a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Spostamento all'interno del codice con il debugger](../debugger/navigating-through-code-with-the-debugger.md)   
 [Debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Debug Multithreaded Applications](../debugger/debug-multithreaded-applications-in-visual-studio.md)
