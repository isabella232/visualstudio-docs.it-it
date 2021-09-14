---
description: Legge i valori BSTR in un set di proprietà.
title: IDiaPropertyStorage::ReadBSTR | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8294b245f2bb71d1cf46abcfd555db23b3ceebe9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629555"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
Legge i `BSTR` valori in un set di proprietà.

## <a name="syntax"></a>Sintassi

```C++
HRESULT ReadBSTR ( 
   PROPID id,
   BSTR*  pValue
);
```

#### <a name="parameters"></a>Parametri
 `id`

[in] Identificatore della proprietà da leggere ( `PROPID` è definito in WTypes.h come `ULONG` ).

 `pValue`

[out] Restituisce il valore della proprietà.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore. Restituisce `E_INVALIDARG` se la proprietà non è di tipo `BSTR` .

## <a name="remarks"></a>Commenti
 Un oggetto è definito da Windows come stringa di caratteri `BSTR` wide con terminazione zero.

## <a name="see-also"></a>Vedi anche
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
