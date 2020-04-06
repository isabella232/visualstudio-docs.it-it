---
title: Proprietà IDebugArrayObject2::GetBaseIndices . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 925ce3a7bcce9f787e02c2bd2714f8b26d8cec26
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736137"
---
# <a name="idebugarrayobject2getbaseindices"></a>IDebugArrayObject2::GetBaseIndices
Recupera gli indici di base (limiti inferiori) per ogni indice in base al numero di dimensioni nella matrice.

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
[in] Numero di dimensioni (rank) della matrice.

`dwIndices`\
[fuori] Gli indici di base (limiti inferiori) per la matrice.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Ad esempio, questa funzione restituirebbe '5' per la matrice creata dal seguente codice C:

```
int[] lengths = { 12 };
int[] lowerbounds = { 5 };
Array.CreateInstance(typeof(int), lengths, lowerbounds);
```

## <a name="see-also"></a>Vedere anche
- [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)
