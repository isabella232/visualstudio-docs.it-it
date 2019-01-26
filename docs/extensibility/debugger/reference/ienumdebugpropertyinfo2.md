---
title: IEnumDebugPropertyInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0eecb16ce4eecf4e39163a82c3aed48d35db6af2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933971"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Questa interfaccia enumera [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) strutture.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugPropertyInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare le informazioni per una particolare proprietà.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) per ottenere questa interfaccia che rappresenta gli elementi figlio di una determinata proprietà. Chiamare [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) per ottenere questa interfaccia che rappresenta le proprietà di un determinato stack frame.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugPropertyInfo2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Recupera un numero specificato di [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) strutture in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Ignora un numero specificato di [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) strutture in una sequenza di enumerazione.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Ottiene il numero di [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) strutture nell'enumeratore.|  
  
## <a name="remarks"></a>Note  
 In generale, una proprietà è una gerarchia di informazioni che possono includere un nome, valore, l'indirizzo e tipo, come qualsiasi altra informazione appropriata per il frame dello stack o oggetto proprietà associata. Visualizzare [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) per altri dettagli.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)