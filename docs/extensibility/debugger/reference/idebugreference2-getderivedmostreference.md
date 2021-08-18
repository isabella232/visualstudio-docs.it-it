---
description: Ottiene il riferimento più derivato di un riferimento.
title: IDebugReference2::GetDerivedMostReference | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e2980792572a6ac9c2d833a0fef62350db968d00
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132587"
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
[out] Restituisce un [oggetto IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) che rappresenta la proprietà più derivata.

## <a name="return-value"></a>Valore restituito
 Restituisce sempre `E_NOTIMPL`.

## <a name="remarks"></a>Commenti
 Ad esempio, se questa proprietà descrive un oggetto che implementa ma che è effettivamente una creazione di un'istanza di derivato da , questo metodo restituisce un `ClassRoot` `ClassDerived` oggetto `ClassRoot` [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) che rappresenta un riferimento all'oggetto `ClassDerived` .

## <a name="see-also"></a>Vedi anche
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
