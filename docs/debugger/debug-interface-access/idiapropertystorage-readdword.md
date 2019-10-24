---
title: 'IDiaPropertyStorage:: ReadDWORD | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadDWORD
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1764ec83a69dcc5daff267767594473bf690b341
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742902"
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
Legge `DWORD` valori in un set di proprietà.

## <a name="syntax"></a>Sintassi

```C++
HRESULT ReadDWORD ( 
   PROPID id,
   DWORD* pValue
);
```

#### <a name="parameters"></a>Parametri
 `id`

in Identificatore della proprietà da leggere (`PROPID` è definito in WTypes. h come `ULONG`).

 `pValue`

out Restituisce il valore della proprietà.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_INVALIDARG` se la proprietà non è di tipo `DWORD`.

## <a name="remarks"></a>Note
 Un `DWORD` viene definito da Windows come Unsigned Integer a 32 bit.

## <a name="see-also"></a>Vedere anche
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)