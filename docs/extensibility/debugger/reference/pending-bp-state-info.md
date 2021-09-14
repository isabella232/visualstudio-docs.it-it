---
description: Contiene informazioni sullo stato di un punto di interruzione pronto per l'associazione a una posizione del codice.
title: PENDING_BP_STATE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16d73973b9d6170023f605dd42e7d451b32fd6bb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711854"
---
# <a name="pending_bp_state_info"></a>PENDING_BP_STATE_INFO
Contiene informazioni sullo stato di un punto di interruzione pronto per l'associazione a una posizione del codice.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagPENDING_BP_STATE_INFO { 
   PENDING_BP_STATE       state;
   PENDING_BP_STATE_FLAGS flags;
} PENDING_BP_STATE_INFO;
```

```csharp
public struct PENDING_BP_STATE_INFO { 
   public uint state;
   public uint flags;
};
```

## <a name="members"></a>Members
 `state`\
 Valore dell'enumerazione [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) che specifica lo stato del punto di interruzione in sospeso.

 `flags`\
 Combinazione di flag [dell'enumerazione PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) che specifica se il punto di interruzione è virtualizzato.

## <a name="remarks"></a>Commenti
 Questa struttura viene passata al [metodo GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) in cui viene compilata.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)
- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)
- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)
