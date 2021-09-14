---
title: Common Language Runtime e valutazione delle espressioni | Microsoft Docs
description: Informazioni su come Common Language Runtime interagisce con il motore di debug e su come integrare un linguaggio di programmazione proprietario nell Visual Studio IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 2c3c0566acf6a0216e5301cefceca061aae9d974
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627671"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime e valutazione delle espressioni
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 I compilatori, ad esempio Visual Basic e C# (pronunciato C-sharp), che hanno come destinazione Common Language Runtime (CLR), producono Microsoft Intermediate Language (MSIL), che viene successivamente compilato in codice nativo. CLR fornisce un motore di debug (DE) per eseguire il debug del codice risultante. Se si prevede di integrare il linguaggio di programmazione proprietario nell'IDE di Visual Studio, è possibile scegliere di eseguire la compilazione in MSIL e pertanto non sarà necessario scrivere codice DE personalizzato. Sarà tuttavia necessario scrivere un analizzatore di espressioni (edizione Enterprise) in grado di valutare le espressioni all'interno del contesto del linguaggio di programmazione.

## <a name="discussion"></a>Discussione
 Le espressioni del linguaggio informatico vengono in genere analizzate per produrre un set di oggetti dati e un set di operatori usati per modificarli. Ad esempio, l'espressione "A+B" potrebbe essere analizzata per applicare l'operatore di addizione (+) agli oggetti dati "A" e "B", con possibile risultato in un altro oggetto dati. Il set totale di oggetti dati, operatori e relative associazioni è rappresentato più spesso in un programma come albero, con gli operatori nei nodi dell'albero e gli oggetti dati nei rami. Un'espressione suddivisa in forma di albero viene spesso definita albero analizzato.

 Dopo l'analisi di un'espressione, viene chiamato un provider di simboli (SP) per valutare ogni oggetto dati. Ad esempio, se "A" è definito sia in più di un metodo, la domanda "Quale A?" deve essere risolta prima che sia possibile determinare il valore di A. La risposta restituita da SP è simile a "The third item on the fifth stack frame" o "The A that is 50 bytes beyond the start of the static memory allocated to this method".

 Oltre a produrre codice MSIL per il programma stesso, i compilatori CLR possono anche produrre informazioni di debug molto descrittive scritte in un file Program DataBase *(pdb).* Purché un compilatore di linguaggio proprietario produca informazioni di debug nello stesso formato dei compilatori CLR, l'SP di CLR è in grado di identificare gli oggetti dati denominati del linguaggio. Dopo aver identificato un oggetto dati denominato, il edizione Enterprise usa un oggetto binder per associare (o associare) l'oggetto dati all'area di memoria che contiene il valore di tale oggetto. De può quindi ottenere o impostare un nuovo valore per l'oggetto dati.

 Un compilatore proprietario può fornire informazioni di debug CLR chiamando l'interfaccia , definita nel .NET Framework `ISymbolWriter` nello spazio dei nomi `System.Diagnostics.SymbolStore` . Compilando in MSIL e scrivendo informazioni di debug tramite queste interfacce, un compilatore proprietario può usare CLR DE e SP. Questo semplifica notevolmente l'integrazione di un linguaggio proprietario nell Visual Studio IDE.

 Quando CLR DE chiama il edizione Enterprise proprietario per valutare un'espressione, il DE fornisce il edizione Enterprise con interfacce a un sp e a un oggetto binder. Pertanto, la scrittura di un motore di debug basato su CLR significa che è necessario implementare solo le interfacce dell'analizzatore di espressioni appropriate. CLR si occupa dell'associazione e della gestione dei simboli.

## <a name="see-also"></a>Vedi anche
- [Scrivere un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
