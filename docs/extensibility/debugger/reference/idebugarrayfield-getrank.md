---
title: Proprietà IDebugArrayField::GetRank . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 692f2f13d861d9688ba349fbc80cb1ca426582c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736305"
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
[fuori] Restituisce il rango.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Il rango di una matrice corrisponde al numero di dimensioni. Le matrici multidimensionali sono in realtà matrici di matrici e possono quindi essere considerate solo una matrice `GetRank` unidimensionale (e il metodo restituisce sempre 1). In [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], d'altra parte, le matrici multidimensionali vengono gestite in modo diverso e il `GetRank` rango di tale matrice riflette il numero di dimensioni (e il metodo restituisce sempre il numero di dimensioni).

## <a name="see-also"></a>Vedere anche
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
