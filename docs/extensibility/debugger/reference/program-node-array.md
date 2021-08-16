---
description: Contiene una matrice di oggetti che descrivono i programmi di interesse.
title: PROGRAM_NODE_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROGRAM_NODE_ARRAY
helpviewer_keywords:
- PROGRAM_NODE_ARRAY structure
ms.assetid: 8eeea600-eda5-4b7c-868a-0b86d177b0a5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5902212cdfc879b32c4e547e1505b9c7fc95904a8c56c70711a8110a7ddee91
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377223"
---
# <a name="program_node_array"></a>PROGRAM_NODE_ARRAY
Contiene una matrice di oggetti che descrivono i programmi di interesse.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagPROGRAM_NODE_ARRAY {
   DWORD                dwCount;
   IDebugProgramNode2** Members;
} PROGRAM_NODE_ARRAY;
```

```csharp
public struct tagPROGRAM_NODE_ARRAY {
   public uint                 dwCount;
   public IDebugProgramNode2[] Members;
}
```

## <a name="members"></a>Members
 `dwCount`\
 Numero di oggetti nella `Members` matrice.

 `Members`\
 Matrice di oggetti [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) che descrivono i programmi richiesti.

## <a name="remarks"></a>Commenti
 Questa struttura fa parte della [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) che a sua volta viene compilata da una chiamata al [metodo GetProviderProcessData.](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
