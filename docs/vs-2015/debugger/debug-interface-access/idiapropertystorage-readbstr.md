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
ms.openlocfilehash: e0c7a796a57d5c96d870850bb02051d745fd8473
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538829"
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

[in] Identificatore della proprietà da leggere (`PROPID` definito in Wtypes. H come un `ULONG`).

 `pValue`

[out] Restituisce il valore della proprietà.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_INVALIDARG` se la proprietà non è di tipo `BSTR`.

## <a name="remarks"></a>Note
 Oggetto `BSTR` è definito da Windows come una stringa con terminazione zero caratteri "wide".

## <a name="see-also"></a>Vedere anche
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)