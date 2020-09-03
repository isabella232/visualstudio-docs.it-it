---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e23f5752229ece7ecac02362c294bc661d109039
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468595"
---
# <a name="idiaaddressmapget_addressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
Indica se è stata stabilita una mappa degli indirizzi per una determinata sessione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_addressMapEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 pRetVal

out Restituisce `TRUE` se il mapping degli indirizzi è abilitato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 I successivi processori eseguibili a volte aggiornano il file eseguibile. DIA contiene un meccanismo per supportare la conversione di simboli nel nuovo layout.

 Le applicazioni client possono impostare la mappa degli indirizzi per una determinata sessione ottenendo l'interfaccia [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) dall'interfaccia [IDiaSession](../../debugger/debug-interface-access/idiasession.md) e chiamando il metodo [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) seguito da una chiamata al metodo [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) . Il `get_addressMapEnabled` metodo restituisce i risultati della chiamata al `put_addressMapEnabled` metodo.

## <a name="see-also"></a>Vedere anche
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)