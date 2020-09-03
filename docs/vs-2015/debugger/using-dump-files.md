---
title: Uso dei file dump | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
caps.latest.revision: 56
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1a2d6215887512f2e0c1410688b2bc924dc1fe3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387057"
---
# <a name="using-dump-files"></a>Uso di file dump
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

File dump con o senza heap; creare un file dump; aprire un file dump; individuare i file binari, i file pdb e il file di origine di un file dump. 
  
## <a name="contents"></a><a name="BKMK_Contents"></a> Contenuto  
 [Definizione di un file dump](#BKMK_What_is_a_dump_file_)  
  
 [File dump, con o senza heap](#BKMK_Dump_files__with_or_without_heaps)  
  
 [Requisiti e limitazioni](#BKMK_Requirements_and_limitations)  
  
 [Creazione di un file dump](#BKMK_Create_a_dump_file)  
  
 [Aprire un file dump](#BKMK_Open_a_dump_file)  
  
 [Individuare i file binari, i file di simboli (con estensione pdb) e i file di origine](#BKMK_Find_binaries__symbol___pdb__files__and_source_files)  
  
## <a name="what-is-a-dump-file"></a><a name="BKMK_What_is_a_dump_file_"></a> Che cos'è un file dump?  
 Un *file dump* è uno snapshot di un'app nel momento in cui viene eseguito il dump. Indica il processo in esecuzione e i moduli caricati. Se il dump è stato salvato con informazioni heap, contiene uno snapshot delle attività svolte nella memoria dell'app in quel momento. L'apertura di un file dump con un heap in Visual Studio è simile all'arresto in corrispondenza di un punto di interruzione in una sessione di debug. Sebbene non sia possibile continuare l'esecuzione, è possibile esaminare gli stack, i thread e i valori delle variabili dell'app al momento in cui si è verificato il dump.  
  
 I dump vengono utilizzati principalmente per il debug di problemi che si verificano nei computer a cui lo sviluppatore non ha accesso. Ad esempio, è possibile utilizzare un file dump dal computer di un cliente quando non è possibile riprodurre il programma di arresto anomalo o non risponde del cliente nel computer. I dump vengono inoltre creati dai tester per salvare l'arresto anomalo o i dati del programma che non rispondono, in modo che il computer di test possa essere utilizzato per altri test. Il debugger di Visual Studio può salvare i file dump per il codice gestito o nativo. Il debugger può caricare i file dump creati da Visual Studio o da altri programmi che salvano i file nel formato *minidump* .  
  
 ![Torna al](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [contenuto](#BKMK_Contents) principale  
  
## <a name="dump-files-with-or-without-heaps"></a><a name="BKMK_Dump_files__with_or_without_heaps"></a> File dump, con o senza heap  
 È possibile creare file dump con o senza informazioni heap.  
  
- **I file dump con heap** contengono uno snapshot della memoria dell'app. Sono inclusi i valori delle variabili al momento della creazione del dump. Se si carica un file dump salvato con un heap, Visual Studio potrà caricare i simboli anche se il file binario dell'applicazione non è disponibile. Visual Studio salva inoltre i file binari dei moduli nativi caricati nel file dump, che possono semplificare il debug.  
  
- **I file dump senza heap** sono molto più piccoli dei dump con informazioni sull'heap. Il debugger deve tuttavia caricare i file binari dell'app per trovare informazioni sui simboli. I file binari devono corrispondere esattamente ai file binari utilizzati alla creazione del dump. Solo i valori delle variabili dello stack vengono salvati nei file dump senza dati dell'heap.  
  
  ![Torna al](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [contenuto](#BKMK_Contents) principale  
  
## <a name="requirements-and-limitations"></a><a name="BKMK_Requirements_and_limitations"></a> Requisiti e limitazioni  
  
- Il debug di file dump del codice ottimizzato può generare confusione. Ad esempio, l'incorporamento di funzioni del compilatore può comportare stack di chiamate imprevisti e altre ottimizzazioni potrebbero modificare la durata delle variabili.  
  
- Il debug dei file dump di computer a 64 bit deve essere eseguito in un'istanza di Visual Studio in esecuzione in un computer a 64 bit.  
  
- Nelle versioni di Visual Studio precedenti a VS 2013, i dump delle app a 32 bit eseguite in computer a 64 bit raccolti da alcuni strumenti (ad esempio Gestione attività e WinDbg a 64 bit) potrebbero non essere aperti in Visual Studio. In VS 2013 questa limitazione è stata eliminata.  
  
- Visual Studio può eseguire il debug dei file dump delle app native di dispositivi ARM. Visual Studio può inoltre eseguire il debug dei file dump di app gestite di dispositivi ARM, ma solo nel debugger nativo.  
  
- Per eseguire il debug dei file dump in [modalità kernel](https://msdn.microsoft.com/library/windows/hardware/ff551880.aspx) in Visual Studio 2013, scaricare la [versione Windows 8.1 degli strumenti di debug per Windows](https://msdn.microsoft.com/windows/hardware/gg463009). Vedere [debug del kernel in Visual Studio](https://msdn.microsoft.com/library/windows/hardware/jj149675.aspx).  
  
- Visual Studio non è in grado di eseguire il debug dei file di dump salvati nel formato dump precedente noto come [dump completo in modalità utente](/windows-hardware/drivers/debugger/user-mode-dump-files#full). Si noti che un dump completo in modalità utente non corrisponde a un dump con heap.  
  
- Per eseguire il debug con il [SOS.dll (estensione del debugger SOS)](https://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498) in Visual Studio, è necessario installare gli strumenti di debug per Windows che fanno parte del Windows Driver Kit (WDK). Vedere [Windows 8.1 Preview: scaricare Kit, bit e strumenti](https://msdn.microsoft.com/library/windows/hardware/bg127147.aspx).  
  
  ![Torna al](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [contenuto](#BKMK_Contents) principale  
  
## <a name="create-a-dump-file"></a><a name="BKMK_Create_a_dump_file"></a> Creare un file dump  
 Per creare un file dump con Visual Studio:  
  
- Durante il debug di un processo in Visual Studio, è possibile salvare un file dump quando il debugger è stato arrestato in corrispondenza di un'eccezione o di un punto di interruzione. Scegliere **Salva dump con nome**, **debug**. Nella finestra di dialogo **Salva dump con nome** , nell' **elenco Salva come digitare** , è possibile selezionare **minidump** o **minidump con heap** (impostazione predefinita).  
  
- Quando è abilitato il [debug](../debugger/just-in-time-debugging-in-visual-studio.md) JIT, è possibile associare il debugger a un processo arrestato in modo anomalo in esecuzione all'esterno del debugger e quindi salvare un file dump. Vedere [Connetti a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
  È inoltre possibile creare file dump con qualsiasi programma che supporta il formato di minidump di Windows. Ad esempio, l'utilità da riga di comando **ProcDump** di [Windows Sysinternals](https://technet.microsoft.com/sysinternals/default) può creare file di dump di arresto anomalo del processo basati su trigger o su richiesta. Per ulteriori informazioni sull'utilizzo di altri strumenti per la creazione di file di dump, vedere [requisiti e limitazioni](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) in questo argomento.  
  
  ![Torna al](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [contenuto](#BKMK_Contents) principale  
  
## <a name="open-a-dump-file"></a><a name="BKMK_Open_a_dump_file"></a> Aprire un file dump  
  
1. In Visual Studio scegliere **file**, **Apri**, **file**.  
  
2. Nella finestra di dialogo **Apri file** individuare e selezionare il file dump. Il file dump in genere ha l'estensione dmp. Scegliere quindi **OK**.  
  
3. Viene visualizzata la finestra **Riepilogo file dump** . In questa finestra è possibile visualizzare informazioni di riepilogo sul debug del file dump, impostare il percorso dei simboli, avviare il debug e copiare le informazioni di riepilogo negli Appunti.  
  
     ![Pagina di riepilogo minidump](../debugger/media/dbg-dump-summarypage.png "DBG_DUMP_SummaryPage")  
  
4. Per avviare il debug, andare alla sezione **azioni** e scegliere **Esegui debug con solo nativo** o **Esegui debug con misto**.  
  
## <a name="find-binaries-symbol-pdb-files-and-source-files"></a><a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Trovare i file binari, i file di simboli (con estensione pdb) e i file di origine  
 Per utilizzare le funzionalità complete di Visual Studio per eseguire il debug di un file dump, è necessario accedere a:  
  
- File exe per cui il dump è stato creato e altri file binari (DLL e così via) utilizzati nel processo del dump.  
  
   Se si esegue il debug di un dump con dati dell'heap, Visual Studio può ovviare alla mancanza dei file binari per alcuni moduli, ma deve disporre dei file binari per un numero sufficiente di moduli per generare stack di chiamate validi. Visual Studio include i moduli nativi in un file dump con heap.  
  
- File di simboli (con estensione pdb) per il file con estensione exe e altri binari.  
  
- File di origine dei moduli a cui si è interessati.  
  
   I file eseguibili e i file con estensione pdb devono corrispondere esattamente alla versione e alla compilazione dei file utilizzati alla creazione del dump.  
  
   È possibile eseguire il debug utilizzando il disassembly dei moduli se non è possibile trovare i file di origine.  
  
  **Percorsi di ricerca predefiniti per i file eseguibili**  
  
  Visual Studio esegue automaticamente la ricerca di questi percorsi per i file eseguibili che non sono inclusi nel file dump:  
  
1. Directory che contiene il file dump.  
  
2. Il percorso del modulo specificato nel file dump. Si tratta del percorso del modulo nel computer in cui è stato recuperato il dump.  
  
3. Percorsi di simboli specificati nella pagina **debug**, **Opzioni**, **simboli** della finestra di dialogo **strumenti**di Visual Studio, **Opzioni** . È possibile aggiungere più posizioni per effettuare la ricerca in questa pagina.  
  
   **Utilizzo delle pagine Nessun binario / Nessun simbolo / Nessuna origine**  
  
   Se Visual Studio non riesce a trovare i file necessari per eseguire il debug di un modulo nel dump, viene visualizzata una pagina appropriata (**nessun binario trovato**, **Nessun simbolo trovato**o **Nessuna origine trovata**). Queste pagine forniscono informazioni dettagliate sulla causa del problema e vengono forniti collegamenti ad azioni che consentono di identificare il percorso corretto dei file. Vedere [specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
   ![Torna al](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [contenuto](#BKMK_Contents) principale  
  
## <a name="see-also"></a>Vedere anche  
 [Debug just-in-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [IntelliTrace](../debugger/intellitrace.md)
