---
description: Ottiene il rango o il numero di dimensioni della matrice.
title: 'IDebugArrayField:: GetRank | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ac945e23090b649ffb5ad2f452ec9245aac81ad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058976"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Ottiene il rango o il numero di dimensioni della matrice.

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
out Restituisce il rango.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Il rango di una matrice corrisponde al numero di dimensioni. In C++ e C#, le matrici multidimensionali sono effettivamente matrici di matrici e possono quindi essere considerate solo una matrice unidimensionale (e il `GetRank` metodo restituisce sempre 1). In [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] , d'altra parte, le matrici multidimensionali vengono gestite in modo diverso e il rango di tale matrice riflette il numero di dimensioni (e il `GetRank` metodo restituisce sempre il numero di dimensioni).

## <a name="see-also"></a>Vedi anche
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
