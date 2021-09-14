---
description: Specifica se la mappa indirizzi deve essere usata per convertire gli indirizzi dei simboli.
title: IDiaAddressMap::put_addressMapEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f4c3a08361942df789c7e6bbd055464d69d056fd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630540"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Specifica se la mappa indirizzi deve essere usata per convertire gli indirizzi dei simboli.

## <a name="syntax"></a>Sintassi

```C++
HRESULT put_addressMapEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Parametri
 NewVal

[in] Impostare su `TRUE` per abilitare la conversione dei simboli o `FALSE` per disabilitarla.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 I postprocessori eseguibili a volte aggiornano il file eseguibile. DIA contiene un meccanismo per supportare la conversione dei simboli nel nuovo layout.

 Quando viene caricato un file PDB, la mappa indirizzi archiviata nel file è abilitata. In alcuni casi, tuttavia, un'applicazione client potrebbe dover fornire la propria mappa indirizzi chiamando il metodo [IDiaAddressMap::set_addressMap.](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) Se il metodo ha esito positivo, l'applicazione client deve chiamare il metodo con un parametro di per consentire `set_addressMap` l'uso di tale mappa `put_addressMapEnabled` `NewVal` `TRUE` indirizzi.

 Lo stato corrente della mappa indirizzi abilitata può essere recuperato con una chiamata al metodo [IDiaAddressMap::get_addressMapEnabled.](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)

## <a name="see-also"></a>Vedi anche
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)
