---
title: Common Language Runtime e valutazione delle espressioni Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 013579473189dd9310501b76d2de0d5cf6fa5822
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739119"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime e valutazione delle espressioni
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 I compilatori, ad esempio Visual Basic e C, (pronunciato in C-sharp), destinati a Common Language Runtime (CLR), producono Microsoft Intermediate Language (MSIL), che viene successivamente compilato in codice nativo. CLR fornisce un motore di debug (DE) per eseguire il debug del codice risultante. Se si prevede di integrare il linguaggio di programmazione proprietario nell'IDE di Visual Studio, è possibile scegliere di compilare in MSIL e pertanto non sarà necessario scrivere il proprio DE. Tuttavia, sarà necessario scrivere un analizzatore di espressioni (EE) in grado di valutare le espressioni nel contesto del linguaggio di programmazione.

## <a name="discussion"></a>Discussione
 Le espressioni del linguaggio computer sono in genere analizzate per produrre un set di oggetti dati e un set di operatori utilizzati per modificarli. Ad esempio, è possibile analizzare l'espressione "A" per applicare l'operatore di addizione ( ) agli oggetti dati "A" e "B", eventualmente generando un altro oggetto dati. Il set totale di oggetti dati, gli operatori e le relative associazioni sono più spesso rappresentati in un programma come una struttura ad albero, con gli operatori nei nodi della struttura ad albero e gli oggetti dati nei rami. Un'espressione suddivisa in forma ad albero viene spesso chiamata albero analizzato.

 Una volta analizzata un'espressione, viene chiamato un provider di simboli (SP) per valutare ogni oggetto dati. Ad esempio, se "A" è definito sia in più di un metodo, la domanda "Quale A?" deve essere risposto prima di poter accertare il valore di A. La risposta restituita dal SP è qualcosa come "Il terzo elemento sul quinto stack frame" o "A che è 50 byte oltre l'inizio della memoria statica allocata a questo metodo."

 Oltre a produrre codice MSIL per il programma stesso, i compilatori CLR possono anche produrre informazioni di debug molto descrittive scritte in un file *.pdb*( Program DataBase). Finché un compilatore di linguaggio proprietario produce informazioni di debug nello stesso formato dei compilatori CLR, il SP di CLR è in grado di identificare gli oggetti dati denominati del linguaggio. Una volta identificato un oggetto dati denominato, EE utilizza un oggetto gestore di associazione per associare (o associare) l'oggetto dati all'area di memoria che contiene il valore di tale oggetto. Il DE può quindi ottenere o impostare un nuovo valore per l'oggetto dati.

 Un compilatore proprietario può fornire informazioni `ISymbolWriter` di debug CLR chiamando l'interfaccia `System.Diagnostics.SymbolStore`(definita in .NET Framework nello spazio dei nomi ). Compilando in MSIL e scrivendo informazioni di debug tramite queste interfacce, un compilatore proprietario può utilizzare CLR DE e SP. Ciò semplifica notevolmente l'integrazione di un linguaggio proprietario nell'IDE di Visual Studio.This seimplifies integrating a proprietary language into the Visual Studio IDE.

 Quando CLR DE chiama l'analizzatore di espressioni proprietario per valutare un'espressione, il DE fornisce l'eE con interfacce a un SP e un oggetto binder. Pertanto, la scrittura di un motore di debug basato su CLR significa che è necessario solo implementare le interfacce dell'analizzatore di espressioni appropriate; CLR si occupa dell'associazione e della gestione dei simboli.

## <a name="see-also"></a>Vedere anche
- [Scrivere un analizzatore di espressioni CLRWrite a CLR expression evaluator](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
