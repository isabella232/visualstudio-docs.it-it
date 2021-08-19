---
title: Modifica del valore di un'istanza | Microsoft Docs
description: Informazioni sul processo di modifica del valore di un oggetto locale quando viene digitato un nuovo valore nel campo valore della finestra Variabili locali.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ba6ea460d16491d651c52e9dec1ca430c33fefd6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145978"
---
# <a name="change-the-value-of-a-local"></a>Modificare il valore di un oggetto locale
> [!IMPORTANT]
> In Visual Studio 2015 questa modalità di implementazione degli analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni [CLR,](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) vedere Analizzatori di espressioni CLR e Esempio di [analizzatore di espressioni gestite.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Quando viene digitato un nuovo valore  nel campo del valore della finestra Variabili locali, il pacchetto di debug passa la stringa, così come è stata digitata, all'analizzatore di espressioni (edizione Enterprise). Il edizione Enterprise valuta questa stringa, che può contenere un valore semplice o un'espressione e archivia il valore risultante nella variabile locale associata.

 Questa è una panoramica del processo di modifica del valore di un oggetto locale:

1. Dopo che l'utente immette il nuovo valore, Visual Studio [chiama SetValueAsString sull'oggetto](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) associato all'oggetto locale.

2. `IDebugProperty2::SetValueAsString` esegue queste attività:

   1. Valuta la stringa per produrre un valore.

   2. Associa l'oggetto [IDebugField associato](../../extensibility/debugger/reference/idebugfield.md) per ottenere un [oggetto IDebugObject.](../../extensibility/debugger/reference/idebugobject.md)

   3. Converte il valore in una serie di byte.

   4. Chiama [SetValue per](../../extensibility/debugger/reference/idebugobject-setvalue.md) inserire i byte del valore in memoria in modo che il programma in fase di debug possa accedervi.

3. Visual Studio la visualizzazione **Variabili** locali . Per informazioni dettagliate, vedere [Visualizzazione delle variabili](../../extensibility/debugger/displaying-locals.md) locali.

   Questa procedura viene usata anche per modificare  il valore di una variabile nella finestra Espressioni di controllo, ad eccezione del fatto che è l'oggetto associato al valore dell'oggetto locale utilizzato al posto dell'oggetto associato all'oggetto `IDebugProperty2` locale `IDebugProperty2` stesso.

## <a name="in-this-section"></a>Contenuto della sezione
 [Implementazione di esempio della modifica dei valori](../../extensibility/debugger/sample-implementation-of-changing-values.md) Usa l'esempio MyCEE per eseguire il processo di modifica dei valori.

## <a name="see-also"></a>Vedi anche
- [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualizzazione delle variabili locali](../../extensibility/debugger/displaying-locals.md)
