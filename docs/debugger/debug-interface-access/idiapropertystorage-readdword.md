---
description: Legge i valori DWORD in un set di proprietà.
title: IDiaPropertyStorage::ReadDWORD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadDWORD
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 58b51638b742fa8dfe874c4d46ff7bd0894f7766
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629550"
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
Legge i `DWORD` valori in un set di proprietà.

## <a name="syntax"></a>Sintassi

```C++
HRESULT ReadDWORD ( 
   PROPID id,
   DWORD* pValue
);
```

#### <a name="parameters"></a>Parametri
 `id`

[in] Identificatore della proprietà da leggere ( `PROPID` è definito in WTypes.h come `ULONG` ).

 `pValue`

[out] Restituisce il valore della proprietà.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore. Restituisce `E_INVALIDARG` se la proprietà non è di tipo `DWORD` .

## <a name="remarks"></a>Commenti
 Un `DWORD` oggetto è definito da Windows come intero senza segno a 32 bit.

## <a name="see-also"></a>Vedi anche
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
