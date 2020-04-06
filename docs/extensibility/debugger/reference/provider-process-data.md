---
title: proprietà PROVIDER_PROCESS_DATA . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdaf15d09af3199d026155cf7667f063f5bbe858
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713774"
---
# <a name="provider_process_data"></a>PROVIDER_PROCESS_DATA
Questa struttura fornisce informazioni sui processi in esecuzione su una macchina.

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
 `Fields`\
 Combinazione di flag dell'enumerazione [PROVIDER_FIELDS,](../../../extensibility/debugger/reference/provider-fields.md) che indica quali campi vengono compilati.

 `ProgramNodes`\
 Struttura [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) che contiene una matrice di nodi di programma.

 `fIsDebuggerPresent`\
 Diverso da`TRUE`zero [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ( ) se`FALSE`il debugger è in esecuzione, zero ( ) in caso contrario.

## <a name="remarks"></a>Osservazioni
 Questa struttura viene passata al metodo [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) in cui viene compilata.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)
- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
