---
title: IDebugReference2::GetDerivedMostReference . Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720621"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Ottiene il riferimento più derivato di un riferimento. Riservato per utilizzi futuri.

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
[fuori] Restituisce un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) oggetto che rappresenta la proprietà più derivata.

## <a name="return-value"></a>Valore restituito
 Restituisce sempre `E_NOTIMPL`.

## <a name="remarks"></a>Osservazioni
 Ad esempio, se questa proprietà descrive `ClassRoot` un oggetto che implementa `ClassDerived` ma che `ClassRoot`è in realtà un'istanza di che deriva da `ClassDerived` , questo metodo restituisce un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) oggetto che rappresenta un riferimento all'oggetto.

## <a name="see-also"></a>Vedere anche
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
