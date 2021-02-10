---
title: Scrittura di un analizzatore di espressioni di Common Language Runtime | Microsoft Docs
description: Informazioni sulla scrittura di un analizzatore di espressioni per il Common Language Runtime, che valuta le espressioni nel linguaggio di codice sottoposto a debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a7d7e4ab292793da5c4abe04233b027981ba3fff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968489"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Scrittura di un analizzatore di espressioni Common Language Runtime
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L'analizzatore di espressioni (EE) fa parte di un motore di debug (DE) che gestisce la sintassi e la semantica del linguaggio di programmazione che ha prodotto il codice sottoposto a debug. Le espressioni devono essere valutate nel contesto di un linguaggio di programmazione. In alcune lingue, ad esempio, l'espressione "A + B" significa "somma di A e B". In altre lingue, la stessa espressione potrebbe significare "A o B". Pertanto, è necessario scrivere un EE separato per ogni linguaggio di programmazione che genera il codice oggetto di cui eseguire il debug nell'IDE di Visual Studio.

 Alcuni aspetti del pacchetto di debug di Visual Studio devono interpretare il codice nel contesto del linguaggio di programmazione. Ad esempio, quando l'esecuzione si arresta in corrispondenza di un punto di interruzione, è necessario valutare e visualizzare tutte le espressioni digitate dall'utente in una finestra espressioni di **controllo** . L'utente può modificare il valore di una variabile locale digitando un'espressione in una finestra **espressioni di controllo** o nella finestra di **controllo immediato** .

## <a name="in-this-section"></a>Contenuto della sezione
 [Common Language Runtime e valutazione delle espressioni](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) Viene spiegato che quando si integra un linguaggio di programmazione proprietario nell'IDE di Visual Studio, la scrittura di un EE in grado di valutare le espressioni all'interno del contesto del linguaggio proprietario consente di compilare in un linguaggio MSIL (Microsoft Intermediate Language) senza scrivere un motore di debug.

 [Architettura dell'analizzatore di espressioni](../../extensibility/debugger/expression-evaluator-architecture.md) Viene illustrato come implementare le interfacce EE richieste e chiamare le interfacce del provider di simboli Common Language Runtime e del gestore di associazione.

 [Registrare un analizzatore di espressioni](../../extensibility/debugger/registering-an-expression-evaluator.md) Nota che EE deve registrarsi come class factory con gli ambienti di Runtime Common Language Runtime e Visual Studio.

 [Implementare un analizzatore di espressioni](../../extensibility/debugger/implementing-an-expression-evaluator.md) Viene descritto come il processo di valutazione di un'espressione includa il motore di debug (DE), il provider di simboli (SP), l'oggetto Binder e l'analizzatore di espressioni (EE).

 [Visualizza variabili locali](../../extensibility/debugger/displaying-locals.md) Viene descritto come, quando l'esecuzione viene sospesa, il pacchetto di debug chiama il metodo DE per ottenere un elenco di variabili e argomenti locali.

 [Valutare un'espressione della finestra espressioni di controllo](../../extensibility/debugger/evaluating-a-watch-window-expression.md) Documenta il modo in cui il pacchetto di debug di Visual Studio chiama il DE per determinare il valore corrente di ogni espressione nell'elenco di controllo.

 [Modificare il valore di una variabile locale](../../extensibility/debugger/changing-the-value-of-a-local.md) Viene illustrato che nella modifica del valore di un oggetto locale ogni riga della finestra variabili locali dispone di un oggetto associato che fornisce il nome, il tipo e il valore corrente di un oggetto locale.

 [Implementare visualizzatori di tipi e visualizzatori personalizzati](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) Viene illustrata l'interfaccia che deve essere implementata dal componente per supportare i visualizzatori dei tipi e i visualizzatori personalizzati.

## <a name="see-also"></a>Vedi anche
 [Estensibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
