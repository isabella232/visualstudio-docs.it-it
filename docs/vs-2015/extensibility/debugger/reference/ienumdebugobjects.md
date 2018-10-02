---
title: IEnumDebugObjects | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3fdb43790d10ffac3fe081369976fe6ee27e0786
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540867"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IEnumDebugObjects](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugobjects).  
  
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Questa interfaccia rappresenta una raccolta di oggetti che implementano il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugObjects : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 L'analizzatore di espressioni implementa questa interfaccia per fornire i set di oggetti che implementano il [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaccia. Si noti che questo non è un'enumerazione standard COM a causa della presenza del [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) (metodo).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) restituisce questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Questa interfaccia implementa i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Recupera il set successivo di [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetti dall'enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Ignora un determinato numero di voci.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Reimposta l'enumerazione per la prima voce.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Recupera una copia dell'enumerazione corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Recupera il numero di voci nell'enumerazione.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia consente un motore di debug enumerare un set di oggetti in una matrice.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)

