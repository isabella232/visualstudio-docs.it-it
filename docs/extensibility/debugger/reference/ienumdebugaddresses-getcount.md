---
title: 'IEnumDebugAddresses:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::GetCount
helpviewer_keywords:
- IEnumDebugAddresses::GetCount method
ms.assetid: f2ca8ff8-539f-457c-83f8-9bbf97618065
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4610613b6fef5e80ae0fd36c3548b4dfdcbc8591
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717672"
---
# <a name="ienumdebugaddressesgetcount"></a>IEnumDebugAddresses::GetCount
Questo metodo restituisce il numero di elementi nell'enumerazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parametri
`pcelt`\
out Restituisce il numero di elementi nell'enumerazione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo non fa parte dell'interfaccia di enumerazione COM personalizzata che specifica che deve essere implementato solo Next, clone, Skip e reset.

## <a name="see-also"></a>Vedere anche
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
