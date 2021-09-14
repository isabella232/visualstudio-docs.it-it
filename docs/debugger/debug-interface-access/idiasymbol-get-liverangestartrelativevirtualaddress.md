---
description: Restituisce l'inizio dell'intervallo di indirizzi in cui il simbolo locale è valido.
title: IDiaSymbol::get_liveRangeStartRelativeVirtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
ms.assetid: 1da52539-9872-4c20-8eaa-74b6cb5f3b02
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b6a6fee96546ee0ced5bd6ed7b0a9ff07f1aacf4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628032"
---
# <a name="idiasymbolget_liverangestartrelativevirtualaddress"></a>IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
Restituisce l'inizio dell'intervallo di indirizzi in cui il simbolo locale è valido.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_liveRangeStartRelativeVirtualAddress ( 
   DWORD* address
);
```

#### <a name="parameters"></a>Parametri
 `address`

[out] Restituisce l'inizio dell'intervallo di indirizzi.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. L'indirizzo virtuale relativo restituito è l'inizio dell'intervallo in cui il simbolo è valido.

> [!NOTE]
> Un codice di errore restituito indica che il simbolo non contiene informazioni sull'intervallo live.

## <a name="remarks"></a>Osservazioni

## <a name="requirements"></a>Requisiti
 Intestazione: Dia2.h

 Libreria: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
