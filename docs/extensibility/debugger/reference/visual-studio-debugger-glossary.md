---
title: Glossario del debugger di Visual Studio Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 954532311fe6b63fc288877a6d41722e6ea47581
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713351"
---
# <a name="visual-studio-debugger-glossary"></a>Glossario del debugger di Visual Studio
Di seguito sono riportati i termini utilizzati nell'SDK [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] di debug.

## <a name="terms"></a>Termini
 punto di interruzione associato Un'astrazione per un punto di interruzione impostato nel codice. Esiste una relazione uno-a-uno tra un punto di interruzione associato e un'istruzione del punto di interruzione nel flusso di codice. Quando il codice viene scaricato, i punti di interruzione associati possono annullare l'associazione.

 causalità Fornisce la possibilità di tenere traccia di un thread logico di esecuzione tra più thread fisici, processi e computer e di ricostruire lo stack di chiamate di tale thread logico in un determinato punto della durata del thread.

 contesto del codice Fornisce un'astrazione di una posizione nel codice nota al motore di debug. Per la maggior parte delle architetture di runtime, un contesto di codice è un indirizzo nel flusso di istruzioni di un programma. Per i linguaggi non tradizionali, in cui il codice non può essere rappresentato da istruzioni, un contesto di codice può essere rappresentato con altri mezzi.

 percorso di codice Rappresenta un punto di esecuzione nel codice in cui viene eseguita una diramazione o viene effettuata una chiamata di funzione. Una traccia dello stack è essenzialmente un elenco di percorsi di codice di chiamata di funzione.

 motore di debug (DE) Un componente che consente il debug di un'architettura di runtime. Un motore di debug funziona insieme all'interprete o al sistema operativo e fornisce servizi di debug come il controllo dell'esecuzione, i punti di interruzione e la valutazione delle espressioni.

 contesto del documento Fornisce un'astrazione di una posizione in un documento di file di origine noto al motore di debug. Per la maggior parte delle lingue, un contesto di documento è una posizione in un file di origine. Per le lingue non tradizionali, per le quali il file di origine potrebbe non essere testo, un contesto del documento potrebbe essere rappresentato con altri mezzi. Vedere anche *posizione del documento*.

 posizione del documento Fornisce un'astrazione di una posizione in un file di origine noto all'IDE. Per la maggior parte delle lingue, una posizione del documento è una posizione in un file di origine. Per le lingue non tradizionali, una posizione del documento potrebbe essere rappresentata in altri modi. Consultate anche *contesto del documento.*

 punto di interruzione di errore Un'astrazione per la descrizione di un errore in un punto di interruzione in sospeso. Un punto di interruzione di errore può descrivere un errore nella posizione del punto di interruzione in sospeso, l'espressione associata al punto di interruzione in sospeso o altre informazioni che impediscono l'associazione del punto di interruzione in sospeso a un percorso di codice.

 contesto di valutazione Fornisce un'astrazione di un contesto di programmazione per la valutazione delle espressioni. In genere, un contesto di valutazione è un ambito. Quando si esegue la valutazione dell'espressione in un contesto di espressione, il contesto dell'espressione fornisce regole di ambito che corrispondono al punto di creazione. Ad esempio, un contesto di espressione creato in uno stack frame fornirà il contesto per la valutazione di variabili locali, parametri di metodo, membri di classe (se applicabile) e variabili globali.

 eccezione intercettata Un'eccezione intercettata da un motore di debug, anche se nello stack frame corrente non è presente alcun meccanismo di gestione delle eccezioni.

 JustMyCode Il concetto di debug solo del codice che appartiene a un utente e ignora tutto il codice intermedio, ad esempio il codice di sistema, anche se il codice sorgente è disponibile per tale codice di sistema.

 punto di interruzione in sospeso Fornisce un'astrazione per i punti di interruzione prima, durante e dopo il caricamento del codice e un modo per virtualizzare i punti di interruzione. Un punto di interruzione in sospeso:A pending breakpoint:

- Contiene tutte le informazioni necessarie per associare un punto di interruzione al codice in uno o più programmi.

- Può essere associato a più percorsi di codice in uno o più programmi.

- Non si associa mai al codice.

  Ogni volta che il codice viene caricato, tutti i punti di interruzione in sospeso in un programma vengono controllati per verificare se è possibile eseguire l'associazione. Un punto di interruzione in sospeso contiene tutti i punti di interruzione associati.

  processo Un processo Win32 fisico. Un processo può contenere più programmi. Vedere anche *programma*.

  programma Un singolo spazio dei nomi in esecuzione all'interno di una particolare architettura di runtime.Program A single namespace running inside a particular run-time architecture. Vedere anche *elaborare*.

  session debug manager (SDM) Gestisce un numero qualsiasi di motori di debug che eseguono il debug di un numero qualsiasi di programmi in più processi su qualsiasi numero di computer. A livello di base, il sDM è un multiplexer di motori di debug. Inoltre, il modello SDM fornisce una visualizzazione unificata della sessione di debug all'IDE.

  stack frame Rappresenta lo stato di calcolo su un frame specifico e un particolare livello di chiamate di funzione annidate.

  thread La nozione generalizzata di esecuzione di istruzioni basate sullo stack in esecuzione in almeno un programma.

  punto di interruzione di avviso Un'astrazione per descrivere un avviso in un punto di interruzione in sospeso. Un punto di interruzione di avviso descrive un motivo per cui il punto di interruzione in sospeso non è ancora associato a un percorso di codice. È possibile che il codice non sia ancora stato caricato per il percorso descritto dal punto di interruzione in sospeso o per altri motivi.

## <a name="see-also"></a>Vedere anche
- [Estendibilità del debugger di Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
