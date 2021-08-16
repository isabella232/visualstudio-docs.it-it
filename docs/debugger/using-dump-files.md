---
title: Usare i file di dump nel debugger | Microsoft Docs
description: Un file di dump è uno snapshot di un'app in esecuzione e di moduli caricati. Provare a creare un file di dump per situazioni in cui non si ha accesso di debug all'app.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 292d767fd2d64ffc9f95ae92075c692435994bc00563d04c6782e00491d2cc1f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378496"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>File di dump nel debugger Visual Studio

<a name="BKMK_What_is_a_dump_file_"></a> Un *file di dump* è uno snapshot che mostra il processo in esecuzione e i moduli caricati per un'app in un momento nel tempo. Un dump con informazioni sull'heap include anche uno snapshot della memoria dell'app a quel punto.

L'apertura di un file dump con un heap in Visual Studio è simile all'arresto in corrispondenza di un punto di interruzione in una sessione di debug. Anche se non è possibile continuare l'esecuzione, è possibile esaminare gli stack, i thread e i valori delle variabili dell'app al momento del dump.

I dump vengono usati principalmente per eseguire il debug di problemi da computer a cui gli sviluppatori non hanno accesso. È possibile usare un file di dump dal computer di un cliente quando non è possibile riprodurre un arresto anomalo o un programma che non risponde nel proprio computer. I tester creano anche dump per salvare i dati di arresto anomalo o non rispondono al programma da usare per altri test.

Il debugger di Visual Studio può salvare i file dump per il codice gestito o nativo. Può eseguire il debug dei file di dump creati da Visual Studio o da altre app che salvano i file nel *formato minidump.*

## <a name="requirements-and-limitations"></a><a name="BKMK_Requirements_and_limitations"></a> Requisiti e limitazioni

- Per eseguire il debug di file di dump da computer a 64 bit, Visual Studio deve essere in esecuzione in un computer a 64 bit.

::: moniker range=">= vs-2019"
- Visual Studio possibile eseguire il debug di file di dump di app gestite dal sistema operativo Linux. 
::: moniker-end

- Visual Studio può eseguire il debug dei file dump delle app native di dispositivi ARM. Può anche eseguire il debug di dump di app gestite da dispositivi ARM, ma solo nel debugger nativo.

- Per eseguire il debug di file di dump in modalità [kernel](/windows-hardware/drivers/debugger/kernel-mode-dump-files) o usare l'estensione di debug [SOS.dll](/dotnet/framework/tools/sos-dll-sos-debugging-extension) in Visual Studio, scaricare gli strumenti di debug per Windows in Windows Driver [Kit (WDK).](/windows-hardware/drivers/download-the-wdk)

- Visual Studio possibile eseguire il debug dei file di dump salvati nel formato di dump in [modalità](/windows/desktop/wer/collecting-user-mode-dumps) utente precedente e completo. Un dump completo in modalità utente non corrisponde a un dump con heap.

- Il debug di file dump del codice ottimizzato può generare confusione. Ad esempio, l'incorporamento di funzioni del compilatore può comportare stack di chiamate imprevisti e altre ottimizzazioni potrebbero modificare la durata delle variabili.

## <a name="dump-files-with-or-without-heaps"></a><a name="BKMK_Dump_files__with_or_without_heaps"></a> File dump con o senza heap

I file di dump possono contenere o meno informazioni sull'heap.

- **I file di dump con heap** contengono uno snapshot della memoria dell'app, inclusi i valori delle variabili, al momento del dump. Visual Studio salva anche i file binari dei moduli nativi caricati in un file di dump con un heap, che può semplificare molto il debug. Visual Studio caricare simboli da un file di dump con un heap, anche se non è in grado di trovare un file binario dell'app.

- **I file di dump senza heap** sono molto più piccoli dei dump con heap, ma il debugger deve caricare i file binari dell'app per trovare informazioni sui simboli. I file binari caricati devono corrispondere esattamente a quelli in esecuzione durante la creazione del dump. I file di dump senza heap salvano solo i valori delle variabili dello stack.

## <a name="create-a-dump-file"></a><a name="BKMK_Create_a_dump_file"></a> Creare un file dump

Durante il debug di un processo in Visual Studio, è possibile salvare un dump quando il debugger è stato arrestato in corrispondenza di un'eccezione o di un punto di interruzione.

Con [il](../debugger/just-in-time-debugging-in-visual-studio.md) debug JIT abilitato, è possibile collegare il debugger Visual Studio a un processo in arresto anomalo all'esterno di Visual Studio e quindi salvare un file dump dal debugger. Vedere [Connettersi ai processi in esecuzione.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

**Per salvare un file dump:**

1. Durante l'arresto in corrispondenza di un errore o di un punto di interruzione durante il debug, selezionare **Debug**  >  **Salva dump con nome**.

1. Nella finestra **di dialogo Salva dump con** nome, in Tipo **file** selezionare **Minidump** o **Minidump con Heap** (impostazione predefinita).

1. Passare a un percorso e selezionare un nome per il file dump e quindi selezionare **Salva**.

>[!NOTE]
>È possibile creare file dump con qualsiasi programma che supporti il Windows minidump. Ad esempio, tramite l'utilità della riga di comando **Procdump** di [Windows Sysinternals](/sysinternals/) è possibile creare file dump dell'arresto anomalo del processo basati su trigger o su richiesta. Per [informazioni sull'uso](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) di altri strumenti per creare file di dump, vedere Requisiti e limitazioni.

## <a name="open-a-dump-file"></a><a name="BKMK_Open_a_dump_file"></a> Aprire un file dump

1. In Visual Studio selezionare **File**  >  **Apri**  >  **file**.

1. Nella finestra di dialogo **Apri file** individuare e selezionare il file dump. In genere avrà *un'estensione dmp.* Selezionare **OK**.

   La **finestra Riepilogo file minidump** mostra informazioni di riepilogo e modulo per il file di dump e le azioni che è possibile eseguire.

   ![Pagina di riepilogo minidump](../debugger/media/dbg_dump_summarypage.png "Pagina di riepilogo minidump")

1. In **Azioni**:
   - Per impostare i percorsi di caricamento dei simboli, selezionare **Imposta percorsi simboli**.
   - Per avviare il debug, selezionare **Debug con solo** gestito , **Debug** solo nativo , **Debug** con misto o Debug con **memoria gestita**.

## <a name="find-exe-pdb-and-source-files"></a><a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Trovare .exe file di origine, pdb e di origine

Per usare funzionalità di debug complete in un file di dump, Visual Studio necessarie:

- File *.exe* per cui è stato creato il dump e altri file binari (DLL e così via) usati dal processo di dump.
- File di simboli (*con estensione pdb*) per *.exe* e altri file binari.
- I *.exe* file *con estensione pdb* che corrispondono esattamente alla versione e alla build dei file durante la creazione del dump.
- File di origine per i moduli pertinenti. È possibile usare il disassembly dei moduli se non è possibile trovare i file di origine.

Se il dump include dati heap, Visual Studio i file binari mancanti per alcuni moduli, ma devono avere file binari per un numero sufficiente di moduli per generare stack di chiamate validi.

### <a name="search-paths-for-exe-files"></a>Percorsi di ricerca per .exe file

Visual Studio cerca automaticamente questi *percorsi per.exe* file non inclusi nel file dump:

1. Cartella che contiene il file dump.
2. Percorso del modulo specificato dal file di dump, ovvero il percorso del modulo nel computer che ha raccolto il dump.
3. I percorsi dei simboli specificati in **Strumenti** (o **Debug)**> **simboli**  >  **di debug delle**  >  **opzioni**. È anche possibile aprire la **pagina Simboli** dal **riquadro Azioni** della finestra Riepilogo **file dump.** In questa pagina è possibile aggiungere altri percorsi per la ricerca.

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>Usare le pagine Nessun file binario, Nessun simbolo o Nessuna origine trovata

Se Visual Studio trovare i file necessari per eseguire il debug di un modulo nel dump, viene visualizzata la pagina Nessun file binario **trovato,** Nessun simbolo trovato o Nessuna origine **trovata.** Queste pagine forniscono informazioni dettagliate sulla causa del problema e forniscono collegamenti alle azioni che consentono di individuare i file. Vedere [Specificare il simbolo (con estensione pdb) e i file di origine.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="see-also"></a>Vedi anche

- [Come eseguire il debug di managed memory dump con gli analizzatori di diagnostica .NET](../debugger/how-to-debug-managed-memory-dump.md)
- [Debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Specificare il simbolo (con estensione pdb) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)