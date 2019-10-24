---
title: IDiaAddressMap::put_addressMapEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5fe5589b667054ee75e3b01743553a2d60bef92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745070"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Specifica se la mappa degli indirizzi deve essere utilizzata per tradurre gli indirizzi dei simboli.

## <a name="syntax"></a>Sintassi

```C++
HRESULT put_addressMapEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Parametri
 NewVal

in Impostare su `TRUE` per abilitare la conversione di simboli o `FALSE` per disabilitare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 I successivi processori eseguibili a volte aggiornano il file eseguibile. DIA contiene un meccanismo per supportare la conversione di simboli nel nuovo layout.

 Quando viene caricato un file PDB, la mappa degli indirizzi archiviata nel file è abilitata. In alcuni casi, tuttavia, quando un'applicazione client potrebbe dover fornire la propria mappa degli indirizzi chiamando il metodo [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) . Se il `set_addressMap` metodo ha esito positivo, l'applicazione client deve chiamare il metodo `put_addressMapEnabled` con un parametro `NewVal` di `TRUE` per consentire l'uso di tale mappa di indirizzi.

 Lo stato corrente della mappa degli indirizzi abilitata può essere recuperato con una chiamata al metodo [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) .

## <a name="see-also"></a>Vedere anche
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)