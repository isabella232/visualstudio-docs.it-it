---
description: Recupera gli indici di base (limiti inferiori) per ogni indice in base al numero di dimensioni nella matrice.
title: IDebugArrayObject2::GetBaseIndices | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 584b0f39bd9f50b68f928cdfb2b93e6e9ea0af28
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627552"
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
[in] Numero di dimensioni (classificazione) della matrice.

`dwIndices`\
[out] Indici di base (limiti inferiori) per la matrice.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Ad esempio, questa funzione restituirebbe '5' per la matrice creata dal codice C# seguente:

```
int[] lengths = { 12 };
int[] lowerbounds = { 5 };
Array.CreateInstance(typeof(int), lengths, lowerbounds);
```

## <a name="see-also"></a>Vedi anche
- [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)
