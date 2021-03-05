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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3a246cda3f5b9395ae013b4bca9d4d27d6f8a5c1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158540"
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
