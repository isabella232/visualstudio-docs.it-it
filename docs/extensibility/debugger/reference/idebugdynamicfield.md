---
title: IDebugDynamicField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 53e4bd31833ad5cf3441638c3735230b89a16cf7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938454"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Questa interfaccia rappresenta un tipo di una variabile.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata dai provider di simboli come classe di base per qualsiasi tipo che può essere determinato in fase di esecuzione. Si tratta di solo codice gestito.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia rappresenta una classe di base da cui possono essere derivate le interfacce più specializzate.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Questa interfaccia non fornisce alcun metodo diverso da quelli ereditati da `IDebugField`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)