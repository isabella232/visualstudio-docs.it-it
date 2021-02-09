---
title: 'IDebugArrayObject:: GetDimensions | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2c0c71032fc8f5c75522f6b1f9e0d8cb1308f63f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870194"
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
in Numero di dimensioni da recuperare.

`dwDimensions`\
[in, out] Matrice compilata con le dimensioni di ogni dimensione. `dwCount` Specifica la dimensione massima della `dwDimensions` matrice.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Una matrice multidimensionale può avere dimensioni diverse per ogni dimensione. Ad esempio, in base alla matrice tridimensionale `myarray[3][2][6]` , questo metodo restituisce 3, 2 e 6 nel `dwDimensions` parametro in tale ordine.

## <a name="see-also"></a>Vedi anche
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
