---
title: IDebugMemoryContext2::GetInfo . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugMemoryContext2::GetInfo method
ms.assetid: 08c7f091-1816-4d64-8834-f9ecaac5c58d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c190710afc9231662fa12c5552d6f73e0268b643
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727472"
---
# <a name="idebugmemorycontext2getinfo"></a>IDebugMemoryContext2::GetInfo
Recupera una [struttura CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) che descrive il contesto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetInfo( 
   CONTEXT_INFO_FIELDS dwFields,
   CONTEXT_INFO*       pInfo
);
```

```csharp
int GetInfo(
   enum_CONTEXT_INFO_FIELDS dwFields,
   CONTEXT_INFO[]           pinfo
);
```

## <a name="parameters"></a>Parametri
`dwFields`\
[in] Combinazione di flag dell'enumerazione [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) che indicano i campi della struttura [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) da compilare.

`pInfo`\
[in, out] Struttura `CONTEXT_INFO` compilata.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedere anche
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
