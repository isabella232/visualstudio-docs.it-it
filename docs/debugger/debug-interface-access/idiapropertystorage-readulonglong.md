---
description: Legge i valori ULONGLONG in un set di proprietà.
title: IDiaPropertyStorage::ReadULONGLONG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5434587770fb632cc353bc5254902a9fb3614c37
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629520"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
Legge i `ULONGLONG` valori in un set di proprietà.

## <a name="syntax"></a>Sintassi

```C++
HRESULT ReadULONGLONG ( 
   PROPID     id,
   ULONGLONG* pValue
);
```

#### <a name="parameters"></a>Parametri
 `id`

[in] Identificatore della proprietà da leggere ( `PROPID` è definito in WTypes.h come `ULONG` ).

 `pValue`

[out] Restituisce il valore della proprietà.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore. Restituisce `E_INVALIDARG` se la proprietà non è di tipo `ULONGLONG` .

## <a name="remarks"></a>Commenti
 Un oggetto è definito da Windows come intero senza `ULONGLONG` segno a 64 bit.

## <a name="see-also"></a>Vedi anche
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
