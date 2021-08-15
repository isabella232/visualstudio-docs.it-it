---
description: Restituisce la parte dell'offset dell'indirizzo iniziale dell'intervallo in cui il simbolo locale è valido.
title: IDiaSymbol::get_liveRangeStartAddressOffset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressOffset
ms.assetid: f5b28914-0a14-4b22-8259-59d7f97ee610
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3ce82f2eb649aed098508e20ebb9e7f2d6bf4fae63dd1fa3ae8f464607fbd8a7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121344511"
---
# <a name="idiasymbolget_liverangestartaddressoffset"></a>IDiaSymbol::get_liveRangeStartAddressOffset
Restituisce la parte dell'offset dell'indirizzo iniziale dell'intervallo in cui il simbolo locale è valido.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_liveRangeStartAddressOffset ( 
   DWORD* offset
);
```

#### <a name="parameters"></a>Parametri
 `offset`

[out] Restituisce la parte dell'offset dell'intervallo di indirizzi iniziale.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

> [!NOTE]
> Un codice di errore restituito indica che il simbolo non contiene informazioni sull'intervallo live.

## <a name="remarks"></a>Commenti
 L'indirizzo formato dalla sezione e dall'offset è l'inizio dell'intervallo in cui il simbolo è valido.

 Per ottenere la parte della sezione dell'indirizzo, usare [IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md).

## <a name="requirements"></a>Requisiti
 Intestazione: Dia2.h

 Libreria: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
