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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e230937de42ebda2697fe4cc43fc77bbee340cfb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125374"
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
 Combinazione di flag [dell'MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) che specificano i campi della struttura inizializzati.

 `bstrName`\
 Nome del computer. Equivale a chiamare [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md).

 `Flags`\
 Combinazione di flag [dell'enumerazione MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) che descrivono gli attributi del computer.

## <a name="remarks"></a>Commenti
 Questa struttura viene restituita da una chiamata al [metodo GetMachineInfo.](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
