---
title: IDiaPropertyStorage::ReadBSTR | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef0b5bac11a1bf3da7e8081f7ae24b6a7a6f1a71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742923"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
Legge `BSTR` valori in un set di proprietà.

## <a name="syntax"></a>Sintassi

```C++
HRESULT ReadBSTR ( 
   PROPID id,
   BSTR*  pValue
);
```

#### <a name="parameters"></a>Parametri
 `id`

in Identificatore della proprietà da leggere (`PROPID` è definito in WTypes. h come `ULONG`).

 `pValue`

out Restituisce il valore della proprietà.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_INVALIDARG` se la proprietà non è di tipo `BSTR`.

## <a name="remarks"></a>Note
 Un `BSTR` viene definito da Windows come stringa di caratteri wide con terminazione zero.

## <a name="see-also"></a>Vedere anche
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)