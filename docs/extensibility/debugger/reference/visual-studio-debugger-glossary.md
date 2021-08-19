---
title: Visual Studio Glossario del debugger | Microsoft Docs
description: Questo articolo illustra diversi termini usati nell'SDK di debug Visual Studio, ad esempio punto di interruzione associato, causalità e contesto del codice.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: bcbe68b0e8fd68d966bd1ed03d1b90aade9e579b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132324"
---
# <a name="visual-studio-debugger-glossary"></a>Glossario del debugger di Visual Studio
Di seguito sono riportati i termini usati [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] nell'SDK di debug.

## <a name="terms"></a>Termini
 punto di interruzione associato Astrazione per un punto di interruzione impostato nel codice. Esiste una relazione uno-a-uno tra un punto di interruzione associato e un'istruzione del punto di interruzione nel flusso di codice. Quando il codice viene scaricato, i punti di interruzione associati possono essere disassociati.

 causalità Consente di tenere traccia di un thread logico di esecuzione tra più thread, processi e computer fisici e di ricostruire lo stack di chiamate di tale thread logico in qualsiasi punto della durata del thread.

 contesto del codice Fornisce un'astrazione di una posizione nel codice nota al motore di debug. Per la maggior parte delle architetture di run-time, un contesto di codice è un indirizzo nel flusso di istruzioni di un programma. Per i linguaggi non differenziali, in cui il codice potrebbe non essere rappresentato da istruzioni, un contesto di codice può essere rappresentato in altri mezzi.

 percorso del codice Rappresenta un punto di esecuzione nel codice in cui viene creato un ramo o viene eseguita una chiamata di funzione. Un'analisi dello stack è essenzialmente un elenco di percorsi del codice di chiamata di funzione.

 motore di debug (DE) Componente che consente il debug di un'architettura di runtime. Un motore di debug funziona insieme all'interprete o al sistema operativo e fornisce servizi di debug, ad esempio controllo dell'esecuzione, punti di interruzione e valutazione delle espressioni.

 contesto documento Fornisce un'astrazione di una posizione in un documento di file di origine noto al motore di debug. Per la maggior parte delle lingue, un contesto di documento è una posizione in un file di origine. Per le lingue non differenziali, per le quali il file di origine potrebbe non essere testo, un contesto di documento potrebbe essere rappresentato in altri mezzi. Vedere anche *posizione del documento.*

 posizione documento Fornisce un'astrazione di una posizione in un file di origine noto all'IDE. Per la maggior parte delle lingue, una posizione del documento è una posizione in un file di origine. Per le lingue non differenziali, una posizione del documento può essere rappresentata in altri modi. Vedere anche *contesto del documento.*

 punto di interruzione dell'errore Astrazione per descrivere un errore in un punto di interruzione in sospeso. Un punto di interruzione di errore può descrivere un errore nella posizione del punto di interruzione in sospeso, nell'espressione associata al punto di interruzione in sospeso o in altre informazioni che impediscono l'associazione del punto di interruzione in sospeso a una posizione del codice.

 contesto di valutazione Fornisce un'astrazione di un contesto di programmazione per la valutazione delle espressioni. In genere, un contesto di valutazione è un ambito. Quando si esegue la valutazione delle espressioni in un contesto di espressione, il contesto dell'espressione fornisce regole di ambito corrispondenti al relativo punto di creazione. Ad esempio, un contesto di espressione creato in un stack frame fornirà il contesto per la valutazione di variabili locali, parametri di metodo, membri di classe (se applicabile) e variabili globali.

 eccezione intercettata Eccezione intercettata da un motore di debug, anche se non è presente alcun meccanismo di gestione delle eccezioni nel stack frame.

 JustMyCode Il concetto di debug solo del codice appartenente a un utente e di ignorare tutto il codice intermedio, ad esempio il codice di sistema, anche se il codice sorgente è disponibile per tale codice di sistema.

 punto di interruzione in sospeso Fornisce un'astrazione per i punti di interruzione prima, durante e dopo il caricamento del codice e un modo per virtualizzare i punti di interruzione. Un punto di interruzione in sospeso:

- Contiene tutte le informazioni necessarie per associare un punto di interruzione al codice in uno o più programmi.

- Può essere associato a più percorsi di codice in uno o più programmi.

- Non si associa mai al codice.

  Ogni time code viene caricato, tutti i punti di interruzione in sospeso in un programma vengono controllati per verificare se è possibile eseguire l'associazione. Un punto di interruzione in sospeso contiene tutti i punti di interruzione associati.

  process Processo Win32 fisico. Un processo può contenere più programmi. Vedere anche *programmare*.

  program Un singolo spazio dei nomi in esecuzione all'interno di una particolare architettura di run-time. Vedere anche *elaborare*.

  session debug manager (SDM) Gestisce un numero qualsiasi di motori di debug che ese tracciano un numero qualsiasi di programmi in più processi in un numero qualsiasi di computer. A livello di base, SDM è un multiplexer di motori di debug. Inoltre, SDM offre una visualizzazione unificata della sessione di debug all'IDE.

  stack frame rappresenta lo stato di calcolo su un frame specifico e un particolare livello di chiamate di funzione annidate.

  thread Nozione generalizzata di esecuzione di istruzioni basate su stack in esecuzione in almeno un programma.

  avviso punto di interruzione Un'astrazione per descrivere un avviso in un punto di interruzione in sospeso. Un punto di interruzione di avviso descrive un motivo per cui il punto di interruzione in sospeso non è ancora stato associato a una posizione del codice. È possibile che il codice non sia stato ancora caricato per la posizione descritta dal punto di interruzione in sospeso o per altri motivi.

## <a name="see-also"></a>Vedi anche
- [Estendibilità del debugger di Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
