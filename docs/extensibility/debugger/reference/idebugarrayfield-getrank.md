---
description: Ottiene la classificazione o il numero di dimensioni della matrice.
title: IDebugArrayField::GetRank | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a35563f55824ae95269c944f34f87a8af2222a08
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627594"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Ottiene la classificazione o il numero di dimensioni della matrice.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>Parametri
`pdwRank`\
[out] Restituisce la classificazione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 La classificazione di una matrice corrisponde al numero di dimensioni. In C++ e C#, le matrici multidimensionali sono effettivamente matrici di matrici e possono quindi essere considerate solo una matrice unidimensionale (e il metodo restituisce `GetRank` sempre 1). In , d'altra parte, le matrici multidimensionali vengono gestite in modo diverso e la classificazione di tale matrice riflette il numero di dimensioni (e il metodo restituisce sempre il numero [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] `GetRank` di dimensioni).

## <a name="see-also"></a>Vedi anche
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
