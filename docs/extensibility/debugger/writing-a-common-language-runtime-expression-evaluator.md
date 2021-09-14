---
title: Scrittura di un analizzatore di espressioni di Common Language Runtime | Microsoft Docs
description: Informazioni sulla scrittura di un analizzatore di espressioni per Common Language Runtime, che valuta le espressioni nel linguaggio del codice in fase di debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: f7121e28284044ce54d6aa8ffbde7f87edd60e97
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626316"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Scrittura di un analizzatore di espressioni di Common Language Runtime
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L'analizzatore di espressioni (edizione Enterprise) è la parte di un motore di debug (DE) che gestisce la sintassi e la semantica del linguaggio di programmazione che ha prodotto il codice in fase di debug. Le espressioni devono essere valutate nel contesto di un linguaggio di programmazione. In alcuni linguaggi, ad esempio, l'espressione "A+B" indica "somma di A e B". In altri linguaggi, la stessa espressione potrebbe significare "A o B". Pertanto, è necessario scrivere edizione Enterprise per ogni linguaggio di programmazione che genera codice oggetto da eseguire nel Visual Studio IDE.

 Alcuni aspetti del pacchetto Visual Studio debug devono interpretare il codice nel contesto del linguaggio di programmazione. Ad esempio, quando l'esecuzione si arresta in corrispondenza di  un punto di interruzione, tutte le espressioni digitate dall'utente in una finestra Espressione di controllo devono essere valutate e visualizzate. L'utente può modificare il valore di una variabile locale digitando un'espressione in una finestra **Espressioni** di controllo o nella **finestra Controllo** immediato.

## <a name="in-this-section"></a>Contenuto della sezione
 [Common Language Runtime e valutazione delle espressioni](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) Spiega che quando si integra un linguaggio di programmazione proprietario nell'IDE di Visual Studio, la scrittura di un edizione Enterprise in grado di valutare le espressioni nel contesto del linguaggio proprietario consente di compilare in un linguaggio MSIL (Microsoft Intermediate Language) senza scrivere un motore di debug.

 [Architettura dell'analizzatore di espressioni](../../extensibility/debugger/expression-evaluator-architecture.md) Viene illustrato come implementare le interfacce edizione Enterprise e chiamare il provider di simboli di Common Language Runtime (SP) e le interfacce del binder.

 [Registrare un analizzatore di espressioni](../../extensibility/debugger/registering-an-expression-evaluator.md) Si noti che edizione Enterprise deve registrarsi come class factory con common language runtime e Visual Studio runtime.

 [Implementare un analizzatore di espressioni](../../extensibility/debugger/implementing-an-expression-evaluator.md) Descrive il modo in cui il processo di valutazione di un'espressione include il motore di debug (DE), il provider di simboli (SP), l'oggetto binder e l'analizzatore di espressioni (edizione Enterprise).

 [Visualizzare le variabili locali](../../extensibility/debugger/displaying-locals.md) Viene descritto come, quando l'esecuzione viene sospesa, il pacchetto di debug chiama il de per ottenere un elenco di variabili e argomenti locali.

 [Valutare un'espressione di finestra espressioni di controllo](../../extensibility/debugger/evaluating-a-watch-window-expression.md) Illustra come il Visual Studio di debug chiama il de per determinare il valore corrente di ogni espressione nel relativo elenco di controllo.

 [Modificare il valore di un oggetto locale](../../extensibility/debugger/changing-the-value-of-a-local.md) Spiega che nella modifica del valore di un oggetto locale, a ogni riga della finestra Variabili locali è associato un oggetto che fornisce il nome, il tipo e il valore corrente di un oggetto locale.

 [Implementare visualizzatori di tipi e visualizzatori personalizzati](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) Viene illustrata l'interfaccia che deve essere implementata da quale componente supportare i visualizzatori di tipi e i visualizzatori personalizzati.

## <a name="see-also"></a>Vedi anche
 [Visual Studio estendibilità del debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
