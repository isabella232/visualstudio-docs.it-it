---
description: Ottiene l'ordine di priorità della matrice, ovvero il numero di dimensioni.
title: 'IDebugArrayObject:: GetRank | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1440ff2fa82c8296bf54b106b622556a8eebb611
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094328"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
Ottiene l'ordine di priorità della matrice, ovvero il numero di dimensioni.

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
 Usare il metodo [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) per recuperare le dimensioni di ogni dimensione dell'oggetto Array.

## <a name="see-also"></a>Vedi anche
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
