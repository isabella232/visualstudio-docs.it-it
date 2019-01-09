---
title: Utilizzo di file di dump nel debugger | Microsoft Docs
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d79fdbbb34bdd5794b2b9120c2c24dbf5be71c71
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952420"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>File di dump nel debugger di Visual Studio

<a name="BKMK_What_is_a_dump_file_"></a> Oggetto *file di dump* è uno snapshot che illustra il processo che era in esecuzione e i moduli caricati per un'app in un punto nel tempo. A questo punto un dump con informazioni heap include anche uno snapshot della memoria dell'app. 

Apertura di un file di dump con heap in Visual Studio è simile a interruzione in corrispondenza di un punto di interruzione in una sessione di debug. Anche se è possibile continuare l'esecuzione, è possibile esaminare il stack di thread e i valori delle variabili dell'app al momento del dump.

I dump vengono usati principalmente per il debug dei problemi dai computer che gli sviluppatori non hanno accesso a. È possibile usare un file di dump dal computer di un cliente quando non è possibile riprodurre un arresto anomalo o blocco nel proprio computer. Tester a creare anche i dump per salvare l'arresto anomalo del sistema o un blocco di dati da utilizzare per eseguire altre verifiche. 

Il debugger di Visual Studio può salvare i file dump per il codice gestito o nativo. È possibile eseguire il debug di file dump creati da Visual Studio o da altre App che salvano i file nei *minidump* formato.

##  <a name="BKMK_Requirements_and_limitations"></a> Requisiti e limitazioni

-   Per eseguire il debug di file di dump da computer a 64 bit, è necessario eseguire Visual Studio in un computer a 64 bit.

-   Visual Studio può eseguire il debug dei file dump delle app native di dispositivi ARM. Anche possibile eseguire il debug di dump di App gestite da dispositivi ARM, ma solo nel debugger nativo.

-   Per eseguire il debug [in modalità kernel](/windows-hardware/drivers/debugger/kernel-mode-dump-files) file di dump o utilizzare il [SOS. dll](/dotnet/framework/tools/sos-dll-sos-debugging-extension) debug estensione in Visual Studio, scaricare gli strumenti di debug per Windows nel [Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk).

-   Visual Studio non è possibile eseguire il debug di file dump salvati nel precedente, [dump completi della modalità utente](/windows/desktop/wer/collecting-user-mode-dumps) formato. Un dump completo in modalità utente non è lo stesso come un dump con heap.

-   Il debug di file dump del codice ottimizzato può generare confusione. Ad esempio, l'incorporamento di funzioni del compilatore può comportare stack di chiamate imprevisti e altre ottimizzazioni potrebbero modificare la durata delle variabili.

##  <a name="BKMK_Dump_files__with_or_without_heaps"></a> File dump con o senza heap

I file di dump possono o non abbia le informazioni sull'heap.

-   **File dump con heap** contengono uno snapshot della memoria dell'app, inclusi i valori delle variabili, al momento del dump. Visual Studio salva inoltre i file binari dei moduli nativi caricati in un file di dump con heap, che può semplificare il debug. Visual Studio è possibile caricare i simboli da un file di dump con heap, anche se non è possibile trovare un'app binario. 

-   **File dump senza heap** sono molto più piccoli dei dump con heap, ma il debugger deve caricare i file binari dell'app per trovare le informazioni sui simboli. I file binari caricati devono corrispondere esattamente a quelli in esecuzione durante la creazione del dump. I file di dump senza heap salvare i valori delle variabili dello stack solo.

##  <a name="BKMK_Create_a_dump_file"></a> Creare un file dump

Durante il debug di un processo in Visual Studio, è possibile salvare un dump quando il debugger è interrotto in corrispondenza di un'eccezione o un punto di interruzione. 

Con [debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md) abilitata, è possibile collegare il debugger di Visual Studio a un processo arrestatosi in modo anomalo all'esterno di Visual Studio e quindi salvare un file di dump dal debugger. Visualizzare [Collega a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Per salvare un file dump:**

1. Durante l'arresto in corrispondenza di un errore o un punto di interruzione durante il debug, selezionare **Debug** > **Salva Dump con nome**. 

1. Nel **Salva Dump con nome** nella finestra di dialogo **Salva come tipo**, selezionare **Minidump** oppure **Minidump con Heap** (predefinito).

1. Selezionare un percorso e selezionare un nome per il file di dump, quindi **salvare**. 

>[!NOTE]
>È possibile creare file dump con qualsiasi programma che supporta il formato di minidump di Windows. Ad esempio, tramite l'utilità della riga di comando **Procdump** di [Windows Sysinternals](http://technet.microsoft.com/sysinternals/default) è possibile creare file dump dell'arresto anomalo del processo basati su trigger o su richiesta. Visualizzare [requisiti e limitazioni](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) per informazioni sull'uso di altri strumenti per creare file dump.

##  <a name="BKMK_Open_a_dump_file"></a> Aprire un file dump

1. In Visual Studio, selezionare **File** > **Open** > **File**.

1. Nella finestra di dialogo **Apri file** individuare e selezionare il file dump. Il file dump in genere ha l'estensione *dmp*. Scegliere **OK**.

   Il **riepilogo File Minidump** verrà visualizzato un riepilogo e il modulo informazioni per i file di dump e azioni da compiere.

   ![Pagina di riepilogo minidump](../debugger/media/dbg_dump_summarypage.png "pagina di riepilogo Minidump")

1. Sotto **azioni**:
   - Per impostare il caricamento dei percorsi di simboli, selezionare **imposta percorsi dei simboli**.
   - Per avviare il debug, selezionare **eseguire il Debug con solo gestito**, **eseguire il Debug con solo nativo**, **Esegui Debug con misto**, oppure **eseguire il Debug con memoria gestita**.

##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Trovare .exe, con estensione pdb e i file di origine

Per usare le funzionalità in un file di dump di debug complete Visual Studio sono necessari:

- Il *.exe* della creazione del dump per file e altri file binari (DLL e così via) che utilizza il processo di dump.
- File di simboli (con estensione *pdb*) per il file con estensione *exe* e altri binari.
- Il *.exe* e *PDB* la creazione di file che corrispondono esattamente la versione e la compilazione dei file nel dump.
- File di origine per i moduli pertinenti. Se non è possibile trovare i file di origine, è possibile usare il disassembly dei moduli.

Se il dump contiene i dati di heap, Visual Studio può ovviare alla mancanza dei file binari per alcuni moduli, ma deve avere i file binari per numero sufficiente di moduli generare stack di chiamate validi. 

### <a name="search-paths-for-exe-files"></a>Percorsi di ricerca per i file .exe

Visual Studio cerca automaticamente questi percorsi *.exe* i file che non sono inclusi nel file di dump:

1. La cartella che contiene il file di dump.
2. Il percorso del modulo specifica da file di dump, che è il percorso del modulo nel computer in cui raccolti il dump.
3. I percorsi di simboli specificati nella **degli strumenti** (o **Debug**) > **opzioni** > **debug**  >  **Simboli**. È anche possibile aprire il **simboli** pagina dalle **azioni** riquadro del **riepilogo File Dump** finestra. In questa pagina, è possibile aggiungere più percorsi per la ricerca.

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>Usare le pagine Nessun binario, nessun simbolo o nessuna origine trovata

Se Visual Studio non trova i file è necessario eseguire il debug di un modulo nel dump, viene illustrato un **Nessun file binario trovato**, **Nessun simbolo trovato**, o **Nessuna origine trovata** pagina. Queste pagine forniscono informazioni dettagliate sulla causa del problema e forniscono collegamenti alle azioni che consentono di individuare i file. Vedere [Specificare file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="see-also"></a>Vedere anche

- [Debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)