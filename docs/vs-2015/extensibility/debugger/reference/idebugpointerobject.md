---
title: IDebugPointerObject | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 976c5bdf2ac0dda702521dcae3646f16dfc4f23b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797624"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia rappresenta un oggetto del puntatore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPointerObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 L'analizzatore di espressioni implementa questa interfaccia per rappresentare un oggetto del puntatore.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia può ottenere questa interfaccia tramite [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) se il `IDebugObject` rappresenta un puntatore.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi ereditati da [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), il `IDebugPointerObject` interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Ottiene l'oggetto a cui punta l'interfaccia.|  
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Ottiene il valore a cui punta l'interfaccia come una serie di byte consecutivi.|  
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Imposta il valore a cui punta l'interfaccia da una serie di byte consecutivi.|  
  
## <a name="remarks"></a>Note  
 Un analizzatore di espressioni usa questa interfaccia per rappresentare un puntatore in un albero di analisi.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di valutazione di espressioni](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

