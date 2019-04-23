---
title: La modifica del valore di una variabile locale | Microsoft Docs
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
ms.openlocfilehash: b955d27089d86035f96711c2f8442fec5b34bceb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60113482"
---
# <a name="changing-the-value-of-a-local"></a>Modifica del valore di una variabile locale
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando un nuovo valore viene digitato nel campo del valore di **variabili locali** finestra, il pacchetto di debug passa la stringa, durante la digitazione, per l'analizzatore di espressioni (EE). L'analizzatore di Espressioni valuta questa stringa, che può contenere un semplice valore o un'espressione e archivia il valore risultante in locale associato.  
  
 Questa è una panoramica del processo di modifica del valore di una variabile locale:  
  
1. Dopo che l'utente immette il nuovo valore, Visual Studio chiama [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) nel [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto associato all'oggetto locale.  
  
2. `IDebugProperty2::SetValueAsString` esegue le attività seguenti:  
  
   1. Valuta la stringa per produrre un valore.  
  
   2. Associa l'oggetto associato [IDebugField](../../extensibility/debugger/reference/idebugfield.md) oggetto da cui ottenere un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) oggetto.  
  
   3. Converte il valore in una serie di byte.  
  
   4. Le chiamate [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) inserire byte del valore in memoria in modo che il programma sottoposto a debug può accedervi.  
  
3. Visual Studio aggiorna il **variabili locali** visualizzati (vedere [la visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md) per informazioni dettagliate).  
  
   Questa procedura viene utilizzata anche per modificare il valore di una variabile nel **Watch** finestra con la differenza che è la `IDebugProperty2` oggetto associato al valore della variabile locale che viene usata invece del `IDebugProperty2` oggetto associato all'oggetto locale se stessa.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Implementazione di esempio di modifica dei valori](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Usa l'esempio MyCEE al passo passo il processo di modifica dei valori.  
  
## <a name="see-also"></a>Vedere anche  
 [La scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizzazione di variabili locali](../../extensibility/debugger/displaying-locals.md)
