---
title: Common Language Runtime e valutazione delle espressioni | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739119"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime e valutazione delle espressioni
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 I compilatori, ad esempio Visual Basic e C# (pronunciato C-Sharp), destinati a Common Language Runtime (CLR), producono Microsoft Intermediate Language (MSIL), che in seguito viene compilato in codice nativo. CLR fornisce un motore di debug (DE) per eseguire il debug del codice risultante. Se si prevede di integrare il linguaggio di programmazione proprietario nell'IDE di Visual Studio, è possibile scegliere di eseguire la compilazione in MSIL e pertanto non sarà necessario scrivere il proprio DE. Tuttavia, sarà necessario scrivere un analizzatore di espressioni in grado di valutare le espressioni all'interno del contesto del linguaggio di programmazione.

## <a name="discussion"></a>Discussione
 Le espressioni della lingua del computer vengono in genere analizzate per produrre un set di oggetti dati e un set di operatori utilizzati per modificarli. Ad esempio, l'espressione "A + B" può essere analizzata per applicare l'operatore di addizione (+) agli oggetti dati "A" e "B", causando probabilmente un altro oggetto dati. Il set totale di oggetti dati, gli operatori e le relative associazioni sono spesso rappresentati in un programma come albero, con gli operatori nei nodi dell'albero e gli oggetti dati nei rami. Un'espressione che è stata suddivisa in forma di albero viene spesso definita albero analizzato.

 Una volta che un'espressione è stata analizzata, viene chiamato un provider di simboli (SP) per valutare ogni oggetto dati. Se, ad esempio, "A" è definito in più di un metodo, la domanda "quale A?" è necessario rispondere prima che il valore di un oggetto possa essere verificato. La risposta restituita da SP è simile a "il terzo elemento del quinto stack frame" o "A 50 byte oltre l'inizio della memoria statica allocata a questo metodo".

 Oltre a produrre codice MSIL per il programma stesso, i compilatori CLR possono anche produrre informazioni di debug molto descrittive scritte in un file di DataBase di programma (con*estensione PDB*). Fino a quando un compilatore del linguaggio proprietario genera informazioni di debug nello stesso formato dei compilatori CLR, SP di CLR è in grado di identificare gli oggetti dati denominati di tale lingua. Una volta identificato un oggetto dati denominato, EE utilizza un oggetto Binder per associare o associare l'oggetto dati all'area di memoria che contiene il valore di tale oggetto. Il DE può quindi ottenere o impostare un nuovo valore per l'oggetto dati.

 Un compilatore proprietario può fornire informazioni di debug CLR chiamando l' `ISymbolWriter` interfaccia (definita nel .NET Framework nello spazio dei nomi `System.Diagnostics.SymbolStore` ). Tramite la compilazione in MSIL e la scrittura di informazioni di debug tramite queste interfacce, un compilatore proprietario può utilizzare CLR DE e SP. Questo semplifica notevolmente l'integrazione di un linguaggio proprietario nell'IDE di Visual Studio.

 Quando CLR DE chiama il proprietario EE per valutare un'espressione, il DE fornisce l'EE con le interfacce a un SP e a un oggetto Binder. Pertanto, la scrittura di un motore di debug basato su CLR significa che è necessario implementare solo le interfacce dell'analizzatore di espressioni appropriate; CLR si occupa dell'associazione e della gestione dei simboli.

## <a name="see-also"></a>Vedere anche
- [Scrivere un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
