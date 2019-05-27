---
title: IEnumDebugBoundBreakpoints2::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2::GetCount
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2::GetCount
ms.assetid: 5a572eeb-beb7-4fc7-8259-792d277069be
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38916b7c5a7721509091218b5a66e1a7d7ca8a47
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66208540"
---
# <a name="ienumdebugboundbreakpoints2getcount"></a>IEnumDebugBoundBreakpoints2::GetCount
Restituisce il numero di elementi nell'enumerazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetCount(
   ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parametri
`pcelt`\
[out] Restituisce il numero di elementi nell'enumerazione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo non fa parte dell'interfaccia di enumerazione COM facoltativa che specifica che solo le `Next`, `Clone`, `Skip`, e `Reset` devono essere implementati i metodi.

## <a name="see-also"></a>Vedere anche
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)