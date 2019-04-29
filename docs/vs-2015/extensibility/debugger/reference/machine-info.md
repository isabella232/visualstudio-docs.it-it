---
title: MACHINE_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac571a1e1c7a9d6cff1caaca40f1c6568f99adf1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546788"
---
# <a name="machineinfo"></a>MACHINE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Descrive un particolare computer.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
typedef struct tagMACHINE_INFO {   
   MACHINE_INFO_FIELDS Fields;  
   BSTR                bstrName;  
   MACHINE_INFO_FLAGS  Flags;  
} MACHINE_INFO;  
```  
  
```csharp  
public struct MACHINE_INFO {   
   public uint   Fields;  
   public string bstrName;  
   public uint   Flags;  
};  
```  
  
## <a name="members"></a>Membri  
 `Fields`  
 Una combinazione di flag dal [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) enumerazione che specificano quali campi della struttura vengono inizializzati.  
  
 `bstrName`  
 Nome del computer. Equivalente alla chiamata [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md).  
  
 `Flags`  
 Una combinazione di flag dal [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) enumerazione che descrive gli attributi di computer.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene restituita da una chiamata per il [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
