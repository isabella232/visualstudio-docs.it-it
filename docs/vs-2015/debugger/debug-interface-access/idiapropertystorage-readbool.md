---
title: IDiaPropertyStorage::ReadBOOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64eee421a5ed5bd46a64b51694d913a4f2dc4d41
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538876"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
Legge `BOOL` valori in un set di proprietà.

## <a name="syntax"></a>Sintassi

```C++
HRESULT ReadBOOL ( 
   PROPID id,
   BOOL*  pValue
);
```

#### <a name="parameters"></a>Parametri
 `id`

[in] Identificatore della proprietà da leggere (`PROPID` definito in Wtypes. H come un `ULONG`).

 `pValue`

[out] Restituisce il valore della proprietà.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_INVALIDARG` se la proprietà non è di tipo `BOOL`.

## <a name="remarks"></a>Note
 Per ottenere risultati coerenti, interpretare la `BOOL` valore in modo che siano valori diversi da zero `TRUE` e zero è `FALSE`.

## <a name="see-also"></a>Vedere anche
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)