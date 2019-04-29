---
title: PROVIDER_PROCESS_DATA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d021efe197fcc15c99a1138d75e1343fc092efde
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62865065"
---
# <a name="providerprocessdata"></a>PROVIDER_PROCESS_DATA
Questa struttura fornisce informazioni sui processi in esecuzione in un computer.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagPROVIDER_PROCESS_DATA {
   PROVIDER_FIELDS    Fields;
   PROGRAM_NODE_ARRAY ProgramNodes;
   BOOL               fIsDebuggerPresent;
} PROVIDER_PROCESS_DATA;
```

```csharp
public struct PROVIDER_PROCESS_DATA {
   public uint               Fields;
   public PROGRAM_NODE_ARRAY ProgramNodes;
   public int                fIsDebuggerPresent;
}
```

## <a name="members"></a>Membri
 I campi di una combinazione di flag dal [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) enumerazione, che indica quali campi vengono compilati.

 A ProgramNodes [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) struttura che contiene una matrice di nodi di programma.

 fIsDebuggerPresent diverso da zero (`TRUE`) se il [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugger è in esecuzione, zero (`FALSE`) in caso contrario.

## <a name="remarks"></a>Note
 Questa struttura viene passata per il [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) in cui viene compilato nel metodo.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)
- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)