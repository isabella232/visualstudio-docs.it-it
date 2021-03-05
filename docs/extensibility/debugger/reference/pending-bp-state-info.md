---
description: Contiene informazioni sullo stato di un punto di interruzione pronto per l'associazione a una posizione di codice.
title: PENDING_BP_STATE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: edd4bbdde1c241d90329343be1fd5570129c675a
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223927"
---
# <a name="pending_bp_state_info"></a>PENDING_BP_STATE_INFO
Contiene informazioni sullo stato di un punto di interruzione pronto per l'associazione a una posizione di codice.

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
 Combinazione di flag dell'enumerazione [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) che specifica se il punto di interruzione è virtualizzato.

## <a name="remarks"></a>Commenti
 Questa struttura viene passata al metodo [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) in cui è compilata.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)
- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)
- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)
