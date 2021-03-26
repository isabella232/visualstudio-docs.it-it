---
description: Ottiene il riferimento derivato di un riferimento.
title: 'IDebugReference2:: GetDerivedMostReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c482b05620f280b2948aefe7e95eb38682268c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071441"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Ottiene il riferimento derivato di un riferimento. Riservato per utilizzi futuri.

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

## <a name="remarks"></a>Commenti
 Se, ad esempio, questa proprietà descrive un oggetto che implementa `ClassRoot` , ma che in realtà è una creazione di un'istanza di `ClassDerived` derivata da `ClassRoot` , questo metodo restituisce un oggetto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) che rappresenta un riferimento all' `ClassDerived` oggetto.

## <a name="see-also"></a>Vedi anche
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
