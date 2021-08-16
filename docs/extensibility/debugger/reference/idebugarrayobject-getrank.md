---
description: Ottiene il rango della matrice, cio, il numero di dimensioni.
title: IDebugArrayObject::GetRank | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dcabb4c84ea5c22074e95eb724770b61b5632806d38a9e3b3aba59ca7465f937
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403091"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
Ottiene il rango della matrice, cio, il numero di dimensioni.

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
 Usare il [metodo GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) per recuperare le dimensioni di ogni dimensione dell'oggetto matrice.

## <a name="see-also"></a>Vedi anche
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
