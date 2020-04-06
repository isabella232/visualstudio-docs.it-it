---
title: Modifica del valore di un locale Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98e40e4b6ea10bb6ff1242f23f1b6dd83ce0c0cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739143"
---
# <a name="change-the-value-of-a-local"></a>Modificare il valore di un
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Quando viene digitato un nuovo valore nel campo value della finestra **Variabili locali,** il pacchetto di debug passa la stringa, come digitato, all'analizzatore di espressioni (EE). L'analizzatore di Espressioni valuta questa stringa, che può contenere un valore semplice o un'espressione e archivia il valore risultante nella stringa locale associata.

 Questa è una panoramica del processo di modifica del valore di un locale:

1. Dopo che l'utente immette il nuovo valore, Visual Studio chiama [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) sul [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto associato alla locale.

2. `IDebugProperty2::SetValueAsString` esegue queste attività:

   1. Valuta la stringa per produrre un valore.

   2. Associa l'oggetto associato [IDebugField](../../extensibility/debugger/reference/idebugfield.md) oggetto per ottenere un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) oggetto.

   3. Converte il valore in una serie di byte.

   4. Chiama [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) per inserire i byte del valore in memoria in modo che il programma in fase di debug possa accedervi.

3. Visual Studio aggiorna la visualizzazione **Variabili locali** (vedere Visualizzazione delle variabili [locali](../../extensibility/debugger/displaying-locals.md) per i dettagli).

   Questa procedura viene utilizzata anche per modificare il valore di una variabile nella finestra **Espressioni di** controllo, ad eccezione del fatto che è l'oggetto `IDebugProperty2` associato al valore della variabile locale utilizzato al posto dell'oggetto `IDebugProperty2` associato alla variabile locale.

## <a name="in-this-section"></a>Contenuto della sezione
 [Esempio di implementazione della modifica dei valori](../../extensibility/debugger/sample-implementation-of-changing-values.md) Utilizza l'esempio MyCEE per eseguire il processo di modifica dei valori.

## <a name="see-also"></a>Vedere anche
- [Scrittura di un analizzatore di espressioni CLRWriting a CLR expression evaluator](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualizzazione di gente del posto](../../extensibility/debugger/displaying-locals.md)
