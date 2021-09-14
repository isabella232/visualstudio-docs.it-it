---
description: Indica se è stata stabilita una mappa degli indirizzi per una sessione specifica.
title: IDiaAddressMap::get_addressMapEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 592beea4cd85ad14b878886e0cbd8c94ad4d88eb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630557"
---
# <a name="idiaaddressmapget_addressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
Indica se è stata stabilita una mappa degli indirizzi per una sessione specifica.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_addressMapEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 pRetVal

[out] Restituisce `TRUE` se il mapping degli indirizzi è abilitato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 I postprocessori eseguibili talvolta aggiornano il file eseguibile. DIA contiene un meccanismo per supportare la conversione dei simboli nel nuovo layout.

 Le applicazioni client possono impostare la mappa degli indirizzi per una determinata sessione ottenendo l'interfaccia [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) dall'interfaccia [IDiaSession](../../debugger/debug-interface-access/idiasession.md) e chiamando il metodo [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) seguito da una chiamata al metodo [IDiaAddressMap::p ut_addressMapEnabled.](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) Il `get_addressMapEnabled` metodo restituisce i risultati della chiamata al metodo `put_addressMapEnabled` .

## <a name="see-also"></a>Vedi anche
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
