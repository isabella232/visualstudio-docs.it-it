---
description: Recupera l'indirizzo di caricamento per il file eseguibile che corrisponde ai simboli in questo archivio simboli.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f4da8cf494e4fcff8cf09909079ab19d306ce3e295c34c21a788048509acc0a2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121344764"
---
# <a name="idiasessionget_loadaddress"></a>IDiaSession::get_loadAddress
Recupera l'indirizzo di caricamento per il file eseguibile che corrisponde ai simboli in questo archivio simboli.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_loadAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce un indirizzo virtuale in cui viene caricato un file .exe o .dll file.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'indirizzo di caricamento restituito è sempre zero, a meno che non venga impostato in modo specifico usando il metodo [IDiaSession::p ut_loadAddress.](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)

## <a name="see-also"></a>Vedi anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)
