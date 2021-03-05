---
description: Restituisce la lunghezza dell'intervallo di indirizzi in cui il simbolo locale è valido.
title: IDiaSymbol::get_liveRangeLength | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeLength
ms.assetid: ffcce3cc-085c-44eb-8145-46e3819c54f9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 44c4871915ca32dfde0b04d30ada8ce2721cb7de
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161956"
---
# <a name="idiasymbolget_liverangelength"></a>IDiaSymbol::get_liveRangeLength
Restituisce la lunghezza dell'intervallo di indirizzi in cui il simbolo locale è valido.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_liveRangeLength ( 
   ULONGLONG* length
);
```

#### <a name="parameters"></a>Parametri
 `length`

out Restituisce la lunghezza dell'intervallo di indirizzi.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

> [!NOTE]
> Un codice di errore restituito indica che il simbolo non contiene informazioni sull'intervallo Live.

## <a name="remarks"></a>Osservazioni

## <a name="requirements"></a>Requisiti
 Intestazione: dia2. h

 Libreria: diaguids. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
