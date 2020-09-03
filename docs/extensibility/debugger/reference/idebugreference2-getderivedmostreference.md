---
title: 'IDebugReference2:: GetDerivedMostReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15e98884d040cfb2ebf1b33a56c7edea331fbff0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720621"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Ottiene il riferimento derivato di un riferimento. Riservato per usi futuri.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetDerivedMostReference( 
   IDebugReference2** ppDerivedMost
);
```

```csharp
int GetDerivedMostReference( 
   out IDebugReference2 ppDerivedMost
);
```

## <a name="parameters"></a>Parametri
`ppDerivedMost`\
out Restituisce un oggetto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) che rappresenta la proprietà Derived-most.

## <a name="return-value"></a>Valore restituito
 Restituisce sempre `E_NOTIMPL`.

## <a name="remarks"></a>Osservazioni
 Se, ad esempio, questa proprietà descrive un oggetto che implementa `ClassRoot` , ma che in realtà è una creazione di un'istanza di `ClassDerived` derivata da `ClassRoot` , questo metodo restituisce un oggetto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) che rappresenta un riferimento all' `ClassDerived` oggetto.

## <a name="see-also"></a>Vedere anche
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
