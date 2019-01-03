---
title: Glossario del Debugger di Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8be2c3d67c0c55a3d6ee2dd7554b681d077d26b7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53901464"
---
# <a name="visual-studio-debugger-glossary"></a>Glossario del debugger di Visual Studio
Di seguito sono termini usati nel [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugging SDK.  
  
## <a name="terms"></a>Termini  
 punto di interruzione associato  
 Un'astrazione per un punto di interruzione impostato nel codice. È presente una relazione uno a uno tra un punto di interruzione associato e un'istruzione di punto di interruzione nel flusso del codice. Quando il codice viene scaricata, i punti di interruzione associate può annullare l'associazione.  
  
 causalità  
 Consente di tenere traccia di un thread di esecuzione logico tra più thread fisici, processi e le macchine di ricostruire lo stack di chiamate di thread logico in qualsiasi momento nel corso della durata di tale thread.  
  
 contesto del codice  
 Fornisce un'astrazione di una posizione nel codice nota al motore di debug. Per la maggior parte delle architetture di runtime, un contesto del codice è un indirizzo nel flusso di istruzioni del programma. Per le lingue non convenzionale, in cui codice non possa essere rappresentato da istruzioni, un contesto del codice può essere rappresentato con altri mezzi.  
  
 percorso del codice  
 Rappresenta un punto di esecuzione nel codice in cui viene eseguito un ramo o viene effettuata una chiamata di funzione. Un'analisi dello stack è essenzialmente un elenco di percorsi di codice della funzione chiamata.  
  
 motore di debug (DE)  
 Un componente che consente il debug di un'architettura di runtime. Un motore di debug funziona in combinazione con il sistema operativo o un interprete e fornisce servizi di debug, ad esempio valutazione dell'espressione di controllo e i punti di interruzione esecuzione.  
  
 contesto del documento  
 Fornisce un'astrazione di una posizione in un documento di file di origine nota al motore di debug. Per la maggior parte delle lingue, un contesto di documento è una posizione in un file di origine. Per le lingue non convenzionale, per cui il file di origine potrebbe non essere text, un contesto di documento può essere rappresentato da un altro modo. Vedere anche *posizione del documento*.  
  
 Posizione di documento  
 Fornisce un'astrazione di una posizione in un file di origine noto all'IDE. Per la maggior parte dei linguaggi, una posizione di documento è una posizione in un file di origine. Per le lingue non convenzionale, una posizione di documento può essere rappresentata in altri modi. Vedere anche *contesto di documento*.  
  
 punto di interruzione di errore  
 Un'astrazione per la descrizione di un errore in un punto di interruzione in sospeso. Un punto di interruzione di errore può descrivere un errore nella posizione del punto di interruzione in sospeso, l'espressione associata al punto di interruzione in sospeso o altre informazioni che impedisce il punto di interruzione in sospeso dall'associazione in un percorso di codice.  
  
 Contesto di valutazione  
 Fornisce un'astrazione di un contesto di programmazione per la valutazione dell'espressione. In genere, un contesto di valutazione è un ambito. Quando si esegue la valutazione di espressioni in un contesto dell'espressione, il contesto di espressioni fornisce le regole di ambito che corrispondono il punto di creazione. Ad esempio, il contesto di un'espressione creato in uno stack frame fornirà il contesto per la valutazione delle variabili locali, parametri del metodo, i membri della classe (se applicabile) e le variabili globali.  
  
 eccezione intercettata  
 Un'eccezione che viene intercettata da un motore di debug, anche se nessun meccanismo di gestione delle eccezioni nel sia lo stack frame corrente.  
  
 JustMyCode  
 Il concetto di debug solo del codice a cui appartiene un utente e ignorare tutto il codice intermedio, ad esempio il codice di sistema, anche se il codice sorgente è disponibile per tale codice di sistema.  
  
 punto di interruzione in sospeso  
 Fornisce un'astrazione per i punti di interruzione prima, durante e dopo il codice viene caricato e un modo per virtualizzare i punti di interruzione. Oggetto in sospeso punto di interruzione:  
  
- Contiene tutte le informazioni necessarie per associare un punto di interruzione al codice in uno o più programmi.  
  
- Può eseguire l'associazione in più posizioni di codice in uno o più programmi.  
  
- Non viene associato al codice.  
  
  Ogni codice in fase di caricamento, tutti i punti di interruzione in sospeso in un programma vengono controllati per verificare se è possibile eseguire l'associazione. Un punto di interruzione in sospeso si dice che contiene tutti i punti di interruzione associati che si esegue l'associazione.  
  
  processo  
  Un processo Win32 fisico. Un processo può contenere più programmi. Vedere anche *programma*.  
  
  programma  
  Un unico spazio dei nomi in esecuzione all'interno di una particolare architettura di runtime. Vedere anche *processo*.  
  
  gestione del debug sessione (SDM)  
  Gestisce un numero qualsiasi di motori di debug, debug di un numero qualsiasi di programmi in più processi in qualsiasi numero di computer. A livello di base, il modello SDM è un multiplexer dei motori di debug. Inoltre, il modello SDM fornisce una visualizzazione unificata della sessione di debug all'IDE.  
  
  stack frame  
  Rappresenta lo stato del calcolo in un frame specifico e un livello particolare di chiamate di funzione annidata.  
  
  thread  
  La nozione generalizzata di esecuzione di istruzioni basate sullo stack in esecuzione in almeno un programma.  
  
  punto di interruzione di avviso  
  Un'astrazione per la descrizione di un avviso in un punto di interruzione in sospeso. Un punto di interruzione di avviso viene descritto il motivo per cui il punto di interruzione in sospeso non ancora associato a un percorso di codice. È possibile che il codice non è ancora caricato per il percorso descritto dal punto di interruzione in sospeso o per altri motivi.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendibilità del debugger di Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)