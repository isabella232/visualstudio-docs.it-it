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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9e3d822bac6fa16314f5d2962d69adbf74d0bc3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143714"
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
