---
title: Usare i file di dump nel debugger | Microsoft Docs
ms.custom: seodec18
ms.date: 11/05/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db6d4e8bc5b2f09194e03bbadc8f49b773d24f1e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386953"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>Dump di file nel debugger di Visual Studio

<a name="BKMK_What_is_a_dump_file_"></a> Un *file dump* è uno snapshot che mostra il processo che era in esecuzione e i moduli caricati per un'app in un determinato momento. Un dump con informazioni sull'heap include anche uno snapshot della memoria dell'app in quel momento.

L'apertura di un file dump con un heap in Visual Studio è simile all'arresto in corrispondenza di un punto di interruzione in una sessione di debug. Sebbene non sia possibile continuare l'esecuzione, è possibile esaminare gli stack, i thread e i valori delle variabili dell'app al momento del dump.

I dump vengono utilizzati principalmente per eseguire il debug dei problemi dai computer a cui gli sviluppatori non hanno accesso. È possibile utilizzare un file dump dal computer di un cliente quando non è possibile riprodurre un arresto anomalo o un programma che non risponde nel computer. I tester creano anche dump per salvare l'arresto anomalo o la mancata risposta ai dati del programma da usare per altri test.

Il debugger di Visual Studio può salvare i file dump per il codice gestito o nativo. Consente di eseguire il debug dei file di dump creati da Visual Studio o da altre app che salvano i file nel formato *minidump* .

## <a name="requirements-and-limitations"></a><a name="BKMK_Requirements_and_limitations"></a> Requisiti e limitazioni

- Per eseguire il debug di file dump da computer a 64 bit, è necessario che Visual Studio sia in esecuzione in un computer a 64 bit.

- Visual Studio può eseguire il debug dei file dump delle app native di dispositivi ARM. Consente inoltre di eseguire il debug di dump di app gestite da dispositivi ARM, ma solo nel debugger nativo.

- Per eseguire il debug di file dump in [modalità kernel](/windows-hardware/drivers/debugger/kernel-mode-dump-files) o usare l'estensione di debug [SOS.dll](/dotnet/framework/tools/sos-dll-sos-debugging-extension) in Visual Studio, scaricare gli strumenti di debug per Windows in [Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk).

- Visual Studio non è in grado di eseguire il debug dei file di dump salvati nel formato di dump precedente in [modalità utente completo](/windows/desktop/wer/collecting-user-mode-dumps) . Un dump completo in modalità utente non corrisponde a un dump con heap.

- Il debug di file dump del codice ottimizzato può generare confusione. Ad esempio, l'incorporamento di funzioni del compilatore può comportare stack di chiamate imprevisti e altre ottimizzazioni potrebbero modificare la durata delle variabili.

## <a name="dump-files-with-or-without-heaps"></a><a name="BKMK_Dump_files__with_or_without_heaps"></a> File dump con o senza heap

I file dump possono contenere o meno informazioni sull'heap.

- **I file dump con heap** contengono uno snapshot della memoria dell'app, inclusi i valori delle variabili, al momento del dump. Visual Studio salva inoltre i binari dei moduli nativi caricati in un file dump con un heap, che può semplificare notevolmente il debug. Visual Studio può caricare i simboli da un file dump con un heap, anche se non riesce a trovare un file binario dell'app.

- I **file dump senza heap** sono molto più piccoli dei dump con heap, ma il debugger deve caricare i file binari dell'app per trovare informazioni sui simboli. I file binari caricati devono corrispondere esattamente a quelli in esecuzione durante la creazione del dump. I file dump senza heap salvano solo i valori delle variabili dello stack.

## <a name="create-a-dump-file"></a><a name="BKMK_Create_a_dump_file"></a> Creare un file dump

Durante il debug di un processo in Visual Studio, è possibile salvare un dump quando il debugger è stato interrotto in corrispondenza di un'eccezione o di un punto di interruzione.

Quando è abilitato il [debug](../debugger/just-in-time-debugging-in-visual-studio.md) JIT, è possibile associare il debugger di Visual Studio a un processo arrestato in modo anomalo all'esterno di Visual Studio, quindi salvare un file dump dal debugger. Vedere [Connetti a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Per salvare un file dump:**

1. Quando si è arrestato a un errore o a un punto di interruzione durante il debug, selezionare **debug**  >  **Salva dump con nome**.

1. Nella finestra di dialogo **Salva dump con nome** , **in Salva come digitare**selezionare **minidump** o **minidump con heap** (impostazione predefinita).

1. Individuare un percorso e selezionare un nome per il file dump, quindi selezionare **Salva**.

>[!NOTE]
>È possibile creare file dump con qualsiasi programma che supporta il formato di minidump di Windows. Ad esempio, tramite l'utilità della riga di comando **Procdump** di [Windows Sysinternals](https://technet.microsoft.com/sysinternals/default) è possibile creare file dump dell'arresto anomalo del processo basati su trigger o su richiesta. Per informazioni sull'uso di altri strumenti per la creazione di file di dump, vedere [requisiti e limitazioni](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) .

## <a name="open-a-dump-file"></a><a name="BKMK_Open_a_dump_file"></a> Aprire un file dump

1. In Visual Studio selezionare **file**  >  **Apri**  >  **file**.

1. Nella finestra di dialogo **Apri file** individuare e selezionare il file dump. In genere avrà un'estensione *. dmp* . Selezionare **OK**.

   La finestra **Riepilogo file minidump** Visualizza le informazioni di riepilogo e del modulo per il file dump e le azioni che è possibile eseguire.

   ![Pagina di riepilogo minidump](../debugger/media/dbg_dump_summarypage.png "Pagina di riepilogo minidump")

1. In **azioni**:
   - Per impostare i percorsi di caricamento dei simboli, selezionare **Imposta percorsi simboli**.
   - Per avviare il debug, selezionare **debug con solo gestito**, **Esegui il debug con solo nativo**, **Esegui il debug con misto**oppure Esegui il debug **con la memoria gestita**.

## <a name="find-exe-pdb-and-source-files"></a><a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Trovare file con estensione exe, PDB e di origine

Per usare le funzionalità di debug complete in un file dump, è necessario disporre di Visual Studio:

- Il file con *estensione exe* per cui è stato creato il dump e altri file binari (dll e così via) usati dal processo di dump.
- File di simboli (con*estensione PDB*) per il file con *estensione exe* e altri file binari.
- I file con *estensione exe* e *PDB* che corrispondono esattamente alla versione e alla compilazione dei file durante la creazione del dump.
- File di origine per i moduli pertinenti. È possibile utilizzare il disassembly dei moduli se non è possibile trovare i file di origine.

Se il dump contiene dati di heap, Visual Studio può far fronte ai file binari mancanti per alcuni moduli, ma deve disporre di file binari per un numero sufficiente di moduli per generare stack di chiamate validi.

### <a name="search-paths-for-exe-files"></a>Percorsi di ricerca per i file exe

Visual Studio esegue automaticamente la ricerca di questi percorsi per i file *exe* che non sono inclusi nel file dump:

1. Cartella che contiene il file dump.
2. Il percorso del modulo specificato dal file di dump, ovvero il percorso del modulo nel computer in cui è stato raccolto il dump.
3. I percorsi dei simboli specificati in **strumenti** (o **debug**) > **Opzioni**di  >  **debug**  >  **Symbols**. È inoltre possibile aprire la pagina **simboli** dal riquadro **Azioni** della finestra **Riepilogo file dump** . In questa pagina è possibile aggiungere altri percorsi in cui eseguire la ricerca.

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>Usa le pagine nessun binario, nessun simbolo o nessuna origine trovata

Se Visual Studio non riesce a trovare i file necessari per eseguire il debug di un modulo nel dump, viene visualizzato un file **binario non**trovato, non è stato **trovato alcun simbolo**oppure non è stata trovata alcuna pagina di **origine** . Queste pagine forniscono informazioni dettagliate sulla causa del problema e forniscono collegamenti all'azione che consentono di individuare i file. Vedere [specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="see-also"></a>Vedere anche

- [Debug just-in-Time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)