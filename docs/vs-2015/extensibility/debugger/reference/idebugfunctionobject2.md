---
title: IDebugFunctionObject2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 972cc9af0453668e4d5393a00bb80f34e2594273
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839363"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Rappresenta una funzione e migliora l'interfaccia [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugFunctionObject2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un analizzatore di espressioni (EE) implementa questa interfaccia per rappresentare una funzione.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 I metodi di questa interfaccia rinviano quelli di **IDebugFunctionObject** nei modi seguenti:  
  
- Il metodo **IDebugEvaluate** accetta flag.  
  
- Il metodo **CreateObject** accetta flag e un timeout.  
  
- Il metodo **CreateStringObjectWithLength** richiede una lunghezza.  
  
## <a name="methods"></a>Metodi  
 Questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Crea un oggetto che usa un costruttore, date le impostazioni dei flag di valutazione e un valore di timeout.|  
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Crea un oggetto stringa con la lunghezza specificata.|  
|[Valuta](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Chiama la funzione e restituisce il valore risultante come un oggetto.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: EE. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
