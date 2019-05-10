---
title: IEnumDebugPortSuppliers2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2::Next
helpviewer_keywords:
- IEnumDebugPortSuppliers2::Next
ms.assetid: e2a2d226-e70b-42c2-bf00-a936517940c8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ec7dc97d0cfe7940939f1c253a22b92d36f9537
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65225454"
---
# <a name="ienumdebugportsuppliers2next"></a>IEnumDebugPortSuppliers2::Next
Restituisce il set successivo di elementi dall'enumerazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Next(
   ULONG                 celt,
   IDebugPortSupplier2** rgelt,
   ULONG*                pceltFetched
);
```

```csharp
int Next(
   uint                  celt,
   IDebugPortSupplier2[] rgelt,
   ref uint              pceltFetched
);
```

## <a name="parameters"></a>Parametri
 `celt`\

 [in] Il numero di elementi da recuperare. Specifica inoltre la dimensione massima del `rgelt` matrice.

 `rgelt`\

 [in, out] Matrice di [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) elementi da compilare.

 `pceltFetched`\

 [out] Restituisce il numero di elementi effettivamente restituiti nella `rgelt`.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se inferiore al numero richiesto di elementi potrebbe essere restituiti; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)