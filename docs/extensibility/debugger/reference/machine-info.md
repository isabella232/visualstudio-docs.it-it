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
ms.openlocfilehash: b59699c5ec284c2bb1d9534de8960b7706c1804ea95310f1a14b93fd7085d472
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401856"
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
 Combinazione di flag [dell'enumerazione MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) che specificano quali campi della struttura vengono inizializzati.

 `bstrName`\
 Nome del computer. Equivale a chiamare [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md).

 `Flags`\
 Combinazione di flag [dell'enumerazione MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) che descrive gli attributi del computer.

## <a name="remarks"></a>Commenti
 Questa struttura viene restituita da una chiamata [al metodo GetMachineInfo.](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
