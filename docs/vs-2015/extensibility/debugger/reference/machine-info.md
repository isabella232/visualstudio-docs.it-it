---
title: MACHINE_INFO | Microsoft Docs
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
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4408f5c5c576f6293df16b47224000a75522dc5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49821630"
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
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)

