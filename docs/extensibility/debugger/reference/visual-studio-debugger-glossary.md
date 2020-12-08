---
title: Glossario del debugger di Visual Studio | Microsoft Docs
description: Questo articolo illustra diversi termini usati nell'SDK per il debug di Visual Studio, ad esempio il punto di interruzione associato, la causalità e il contesto del codice.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: a01a6ad0e23af04001e9b0990be57d78e84c7241
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847065"
---
# <a name="visual-studio-debugger-glossary"></a>Glossario del debugger di Visual Studio
Di seguito sono riportati i termini usati nell' [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] SDK di debug.

## <a name="terms"></a>Termini
 Punto di interruzione associato un'astrazione per un punto di interruzione impostato nel codice. Esiste una relazione uno-a-uno tra un punto di interruzione associato e un'istruzione del punto di interruzione nel flusso di codice. Quando il codice viene scaricato, i punti di interruzione associati possono essere disassociati.

 la causalità consente di tenere traccia di un thread logico di esecuzione tra più thread, processi e computer fisici e di ricostruire lo stack di chiamate del thread logico in un determinato punto della durata del thread.

 il contesto del codice fornisce un'astrazione di una posizione nel codice noto al motore di debug. Per la maggior parte delle architetture in fase di esecuzione, un contesto di codice è un indirizzo nel flusso di istruzioni di un programma. Per le lingue non tradizionali, in cui il codice non può essere rappresentato dalle istruzioni, un contesto di codice può essere rappresentato da altri mezzi.

 il percorso del codice rappresenta un punto di esecuzione nel codice in cui viene eseguito un ramo o viene eseguita una chiamata di funzione. Una traccia dello stack è essenzialmente un elenco di percorsi di codice di chiamata di funzione.

 motore di debug (DE) un componente che consente il debug di un'architettura in fase di esecuzione. Un motore di debug funziona in combinazione con l'interprete o il sistema operativo e fornisce servizi di debug quali il controllo dell'esecuzione, i punti di interruzione e la valutazione delle espressioni.

 il contesto del documento fornisce un'astrazione di una posizione in un documento del file di origine noto al motore di debug. Per la maggior parte delle lingue, un contesto di documento è una posizione in un file di origine. Per i linguaggi non tradizionali, per i quali il file di origine non può essere testo, un contesto di documento potrebbe essere rappresentato da altri mezzi. Vedere anche *posizione del documento*.

 la posizione del documento fornisce un'astrazione di una posizione in un file di origine noto all'IDE. Per la maggior parte delle lingue, una posizione del documento è una posizione in un file di origine. Per i linguaggi non tradizionali, la posizione di un documento potrebbe essere rappresentata in altri modi. Vedere anche *contesto del documento*.

 errore punto di interruzione di un'astrazione per la descrizione di un errore in un punto di interruzione in sospeso. Un punto di interruzione di errore può descrivere un errore nella posizione del punto di interruzione in sospeso, l'espressione associata al punto di interruzione in sospeso o altre informazioni che impediscono l'associazione del punto di interruzione in sospeso a una posizione di codice.

 il contesto di valutazione fornisce un'astrazione di un contesto di programmazione per la valutazione dell'espressione. In genere, un contesto di valutazione è un ambito. Quando si esegue la valutazione dell'espressione in un contesto dell'espressione, il contesto dell'espressione fornisce regole di ambito che corrispondono al punto di creazione. Ad esempio, un contesto di espressione creato in un stack frame fornirà il contesto per la valutazione di variabili locali, parametri di metodo, membri di classe (se applicabile) e variabili globali.

 eccezione intercettata un'eccezione intercettata da un motore di debug, anche se non è presente alcun meccanismo di gestione delle eccezioni nel stack frame corrente.

 JustMyCode il concetto di debug solo del codice che appartiene a un utente e ignorando tutto il codice intermedio, ad esempio il codice di sistema, anche se il codice sorgente è disponibile per il codice di sistema.

 il punto di interruzione in sospeso fornisce un'astrazione per i punti di interruzione prima, durante e dopo il caricamento del codice e per la virtualizzazione dei punti di interruzione. Un punto di interruzione in sospeso:

- Contiene tutte le informazioni necessarie per associare un punto di interruzione al codice in uno o più programmi.

- Può essere associato a più posizioni di codice in uno o più programmi.

- Non viene mai associato al codice.

  Ogni volta che il codice viene caricato, vengono controllati tutti i punti di interruzione in sospeso in un programma per verificare se è possibile eseguire l'associazione. Un punto di interruzione in sospeso si afferma che contiene tutti i punti di interruzione associati.

  elaborare un processo Win32 fisico. Un processo può contenere più programmi. Vedere anche *Program*.

  programmare un singolo spazio dei nomi in esecuzione all'interno di un'architettura di runtime particolare. Vedere anche *Process*.

  gestione debug sessione (SDM) gestisce un numero qualsiasi di motori di debug che esegue il debug di un numero qualsiasi di programmi in più processi in un numero qualsiasi di computer. A livello di base, SDM è un multiplexer di motori di debug. Inoltre, l'SDM fornisce una visualizzazione unificata della sessione di debug all'IDE.

  stack frame rappresenta lo stato del calcolo in un particolare frame e un particolare livello di chiamate di funzione nidificate.

  thread la nozione generalizzata di esecuzione di istruzioni basate su stack in esecuzione in almeno un programma.

  avviso punto di interruzione un'astrazione per la descrizione di un avviso in un punto di interruzione in sospeso. Un punto di interruzione di avviso descrive il motivo per cui il punto di interruzione in sospeso non è ancora stato associato a una posizione del codice. Questo potrebbe essere dovuto al fatto che il codice non è ancora stato caricato per la posizione descritta dal punto di interruzione in sospeso o per altri motivi.

## <a name="see-also"></a>Vedi anche
- [Estendibilità del debugger di Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
