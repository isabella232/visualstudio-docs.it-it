---
title: IDebugArrayObject2::GetBaseIndices | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04252ed40cd0ac2c0e5f41bc1104104aeee302c4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317564"
---
# <a name="idebugarrayobject2getbaseindices"></a>IDebugArrayObject2::GetBaseIndices
Recupera gli indici di base (inferiore) per ogni indice dato il numero di dimensioni nella matrice.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetBaseIndices (
   DWORD  dwRank,
   DWORD* dwIndices
);
```

```csharp
int GetBaseIndices (
   uint       dwRank,
   out uint[] dwIndices
);
```

## <a name="parameters"></a>Parametri
`dwRank`\
[in] Il numero di dimensioni (rank) della matrice.

`dwIndices`\
[out] Indici base (inferiore) per la matrice.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Ad esempio, questa funzione restituirà '5' per la matrice creata nel modo seguente C# code:

```
int[] lengths = { 12 };
int[] lowerbounds = { 5 };
Array.CreateInstance(typeof(int), lengths, lowerbounds);
```

## <a name="see-also"></a>Vedere anche
- [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)