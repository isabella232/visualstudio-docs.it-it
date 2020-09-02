---
title: IDiaSession::get_loadAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::get_loadAddress method
ms.assetid: 5162ae1a-38e3-4571-8995-4ed9be1dec3e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0615933715c0e78513f9ee33ee171cc764f5d743
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465433"
---
# <a name="idiasessionget_loadaddress"></a>IDiaSession::get_loadAddress
Recupera l'indirizzo di caricamento per il file eseguibile che corrisponde ai simboli nell'archivio simboli.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_loadAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce un indirizzo virtuale (VA) in cui viene caricato un file con estensione exe o dll.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 L'indirizzo di caricamento restituito è sempre zero, a meno che non sia impostato in modo specifico tramite il metodo [IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) .

## <a name="see-also"></a>Vedere anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)