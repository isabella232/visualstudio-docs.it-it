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
ms.openlocfilehash: 7a8cabb51b13262553d70e45ffd3e26219cb4563e597b519c79ef26a734a68cd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345348"
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

[in] Impostare su `TRUE` per abilitare la conversione dei simboli o `FALSE` per disabilitare.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 I postprocessori eseguibili talvolta aggiornano il file eseguibile. DIA contiene un meccanismo per supportare la conversione dei simboli nel nuovo layout.

 Quando viene caricato un file PDB, la mappa degli indirizzi archiviata nel file è abilitata. In alcuni casi, tuttavia, un'applicazione client potrebbe dover fornire la propria mappa indirizzi chiamando il metodo [IDiaAddressMap::set_addressMap.](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) Se il metodo ha esito positivo, l'applicazione client deve chiamare il metodo con un parametro di per `set_addressMap` `put_addressMapEnabled` consentire `NewVal` `TRUE` l'uso di tale mappa indirizzi.

 Lo stato corrente della mappa degli indirizzi abilitata può essere recuperato con una chiamata al metodo [IDiaAddressMap::get_addressMapEnabled.](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)

## <a name="see-also"></a>Vedi anche
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)
