---
description: Questa struttura fornisce informazioni sui processi in esecuzione in un computer.
title: PROVIDER_PROCESS_DATA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6c48c87f92fde487b9a008c5db45f75eb026f83
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079514"
---
# <a name="provider_process_data"></a>PROVIDER_PROCESS_DATA
Questa struttura fornisce informazioni sui processi in esecuzione in un computer.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagPROVIDER_PROCESS_DATA {
   PROVIDER_FIELDS    Fields;
   PROGRAM_NODE_ARRAY ProgramNodes;
   BOOL               fIsDebuggerPresent;
} PROVIDER_PROCESS_DATA;
```

```csharp
public struct PROVIDER_PROCESS_DATA {
   public uint               Fields;
   public PROGRAM_NODE_ARRAY ProgramNodes;
   public int                fIsDebuggerPresent;
}
```

## <a name="members"></a>Members
 `Fields`\
 Combinazione di flag dell'enumerazione [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) , che indica i campi che vengono compilati.

 `ProgramNodes`\
 Struttura [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) contenente una matrice di nodi del programma.

 `fIsDebuggerPresent`\
 Diverso da zero ( `TRUE` ) se il [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugger è in esecuzione, in caso contrario, zero ( `FALSE` ).

## <a name="remarks"></a>Commenti
 Questa struttura viene passata al metodo [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) in cui è compilata.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)
- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
