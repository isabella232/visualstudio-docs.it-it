---
title: Visualizzazione di variabili locali | Microsoft Docs
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
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e41e77c819a08e1f0440652e023bc2776ba62934
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721883"
---
# <a name="displaying-locals"></a>Visualizzazione di variabili locali
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Sempre l'esecuzione avviene all'interno del contesto di un metodo, noto anche come metodo contenitore o il metodo corrente. Quando l'esecuzione viene sospesa, Visual Studio chiama il motore di debug (DE) per ottenere un elenco delle variabili locali e gli argomenti, collettivamente denominati variabili locali del metodo. Visual Studio visualizza le variabili locali e i relativi valori nel **variabili locali** finestra.  
  
 Per visualizzare variabili locali, chiama il DE il [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) metodo appartenente all'analizzatore di Espressioni e gli assegna un contesto di valutazione, che è un provider di simboli (SP), l'indirizzo di esecuzione corrente e un oggetto strumento di associazione. Per altre informazioni, vedere [contesto di valutazione](../../extensibility/debugger/evaluation-context.md). Se la chiamata ha esito positivo, il `IDebugExpressionEvaluator::GetMethodProperty` metodo restituisce un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) oggetto che rappresenta il metodo che contiene l'indirizzo di esecuzione corrente.  
  
 Le chiamate DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) per ottenere un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) oggetto, che viene filtrata in modo da restituire soli variabili locali ed enumerata per produrre un elenco di [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)strutture. Ogni struttura contiene il nome, tipo e valore di una variabile locale. Il tipo e il valore vengono archiviati come stringhe formattate, adatte per la visualizzazione. Il nome, tipo e valore sono in genere visualizzati insieme in una sola riga del **variabili locali** finestra.  
  
> [!NOTE]
>  Il **controllo immediato** e **Watch** finestre vengono visualizzate anche le variabili con lo stesso formato di nome, valore e tipo. Tuttavia, tali valori vengono ottenuti chiamando [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) invece di `IDebugProperty2::EnumChildren`.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Implementazione di esempio di variabili locali](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Usa esempi per eseguire passo passo il processo di implementazione di variabili locali.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md)  
 Viene spiegato che quando il motore di debug (DE) chiama l'analizzatore di espressioni (EE), passa di tre argomenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

