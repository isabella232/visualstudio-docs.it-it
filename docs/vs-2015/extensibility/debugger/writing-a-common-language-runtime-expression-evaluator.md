---
title: La scrittura di un analizzatore di espressioni di Common Language Runtime | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cfd368bb0302fec1fcf9fdd1f6e6e069377846ab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783012"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Scrittura di un analizzatore di espressioni di Common Language Runtime
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L'analizzatore di espressioni (EE) è la parte di un motore di debug (DE) che gestisce la sintassi e semantica del linguaggio di programmazione che ha generato il codice in fase di debug. Le espressioni devono essere valutate nel contesto di un linguaggio di programmazione. In alcuni linguaggi, ad esempio, l'espressione "A + B" significa "la somma di A e b." In altre lingue, la stessa espressione potrebbe significare "A o B." Di conseguenza, un oggetto separato EE deve essere scritta per ogni linguaggio di programmazione che genera il codice oggetto da sottoporre a debug nell'IDE di Visual Studio.  
  
 Alcuni aspetti del pacchetto di debug di Visual Studio devono interpretare il codice nel contesto del linguaggio di programmazione. Ad esempio, quando si interrompe l'esecuzione in un punto di interruzione, tutte le espressioni che l'utente ha digitato in un **Watch** finestra deve essere valutata e visualizzata. Inoltre, l'utente può modificare il valore di una variabile locale, digitare un'espressione in una **Watch** finestra o nel **immediato** finestra.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Common Language Runtime e valutazione delle espressioni](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Viene spiegato che quando si sta integrando il linguaggio di programmazione proprietario nell'IDE di Visual Studio, la scrittura di un EE in grado di valutazione di espressioni all'interno del contesto del linguaggio proprietaria consente di compilare in Microsoft intermediate language (MSIL) senza dover scrivere un motore di debug.  
  
 [Architettura dell'analizzatore di espressioni](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Viene illustrato come implementare le interfacce necessarie EE e chiamare il provider di simboli di common language runtime (SP) e le interfacce dello strumento di associazione.  
  
 [Registrazione di un analizzatore di espressioni](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Indica che l'analizzatore di Espressioni deve registrarsi come una class factory con sia il common language runtime e gli ambienti di runtime di Visual Studio.  
  
 [Implementazione di un analizzatore di espressioni](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Viene descritto come il processo di valutazione di un'espressione include il motore di debug (DE), il provider di simboli (SP), l'oggetto strumento di associazione e l'analizzatore di espressioni (EE).  
  
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)  
 Viene descritto come, quando l'esecuzione viene sospesa, il pacchetto di debug chiama il DE per ottenere un elenco di argomenti e variabili locali.  
  
 [Valutazione di un'espressione della finestra Espressioni di controllo](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Illustra come il pacchetto di debug di Visual Studio chiama il DE per determinare il valore corrente di ogni espressione nel proprio elenco di espressioni di controllo.  
  
 [Modifica del valore di una variabile locale](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Viene illustrato che modifica il valore di una variabile locale, ogni riga della finestra variabili locali è associato un oggetto che fornisce il nome, tipo e il valore corrente di una variabile locale.  
  
 [Implementazione di visualizzatori di tipi e visualizzatori personalizzati](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Viene illustrato quale interfaccia deve essere implementata da quale componente per supportare i visualizzatori di tipi e visualizzatori personalizzati.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

