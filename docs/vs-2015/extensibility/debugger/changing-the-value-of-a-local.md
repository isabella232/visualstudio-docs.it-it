---
title: Modifica del valore di un oggetto locale | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 516725510c5f5bc7baa8bd96d3f7fb969b6589e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839332"
---
# <a name="changing-the-value-of-a-local"></a>Modifica del valore di una variabile locale
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando un nuovo valore viene digitato nel campo del valore della finestra **variabili locali** , il pacchetto di debug passa la stringa, come tipizzata, all'analizzatore di espressioni (EE). L'EE valuta questa stringa, che può contenere un valore semplice o un'espressione e archivia il valore risultante nell'oggetto locale associato.  
  
 Si tratta di una panoramica del processo di modifica del valore di un locale:  
  
1. Dopo che l'utente immette il nuovo valore, Visual Studio chiama [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) sull'oggetto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) associato a local.  
  
2. `IDebugProperty2::SetValueAsString` esegue queste attività:  
  
   1. Valuta la stringa per produrre un valore.  
  
   2. Associa l'oggetto [IDebugField](../../extensibility/debugger/reference/idebugfield.md) associato per ottenere un oggetto [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) .  
  
   3. Converte il valore in una serie di byte.  
  
   4. Chiama [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) per inserire i byte del valore in memoria, in modo che il programma di cui è in corso il debug possa accedervi.  
  
3. Visual Studio aggiorna la visualizzazione delle **variabili locali** . per informazioni dettagliate, vedere [visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md) .  
  
   Questa procedura viene usata anche per modificare il valore di una variabile nella finestra **espressioni di controllo** , ad eccezione del fatto che è l' `IDebugProperty2` oggetto associato al valore del locale usato al posto dell' `IDebugProperty2` oggetto associato al locale stesso.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Implementazione di esempio di modifica dei valori](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Usa l'esempio MyCEE per eseguire il processo di modifica dei valori.  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)
