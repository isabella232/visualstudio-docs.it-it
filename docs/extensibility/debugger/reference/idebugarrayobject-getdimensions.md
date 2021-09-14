---
description: Ottiene le dimensioni della matrice.
title: IDebugArrayObject::GetDimensions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: e637f1139de8ee6caebea92cc5ca1fe494c206e6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627570"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Ottiene le dimensioni della matrice.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetDimensions( 
   DWORD dwCount,
   DWORD dwDimensions[]
);
```

```csharp
int GetDimensions(
   [In] uint    dwCount,
   [Out] uint[] dwDimensions
);
```

## <a name="parameters"></a>Parametri
`dwCount`\
[in] Numero di dimensioni da recuperare.

`dwDimensions`\
[in, out] Matrice compilata con le dimensioni di ogni dimensione. `dwCount` specifica le dimensioni massime della `dwDimensions` matrice.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Una matrice multidimensionale può avere dimensioni diverse per ogni dimensione. Ad esempio, dato la matrice tridimensionale , questo metodo restituirebbe `myarray[3][2][6]` 3, 2 e 6 nel `dwDimensions` parametro nell'ordine specificato.

## <a name="see-also"></a>Vedi anche
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
