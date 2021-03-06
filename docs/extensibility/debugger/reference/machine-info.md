---
description: Descrive un computer specifico.
title: MACHINE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 796b6c95016708d3c179a8428b7f32aff9ccfe88
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224083"
---
# <a name="machine_info"></a>MACHINE_INFO
Descrive un computer specifico.

## <a name="syntax"></a>Sintassi

```cpp
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

## <a name="members"></a>Members
 `Fields`\
 Combinazione di flag dell'enumerazione [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) che specificano i campi della struttura inizializzati.

 `bstrName`\
 Nome del computer. Equivale a chiamare [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md).

 `Flags`\
 Combinazione di flag dell'enumerazione [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) che descrive gli attributi del computer.

## <a name="remarks"></a>Commenti
 Questa struttura viene restituita da una chiamata al metodo [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
