---
description: Fornisce una mappa degli indirizzi per supportare le traduzioni del layout dell'immagine.
title: IDiaAddressMap::set_addressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b9b00147f4ea8b2313e49e86795c36ec33aae9f1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158308"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
Fornisce una mappa degli indirizzi per supportare le traduzioni del layout dell'immagine.

## <a name="syntax"></a>Sintassi

```C++
HRESULT set_addressMap ( 
   DWORD                     cbData,
   struct DiaAddressMapEntry data[],
   BOOL                      imagetoSymbols
);
```

#### <a name="parameters"></a>Parametri
 `cbData`

in Numero di elementi nel `data` parametro.

 `data[]`

in Matrice di strutture di [struttura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md) che definiscono la mappa di conversione.

 `imagetoSymbols`

[in] `TRUE` Se il `data` parametro definisce una mappa dal nuovo layout dell'immagine al layout originale (come descritto dai simboli di debug). `FALSE` Se `data` è un mapping al nuovo layout dell'immagine tratto dal layout originale.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 In genere, il diametro recupera le mappe degli indirizzi da un file di database di programma (con estensione pdb). Se questi valori sono mancanti, il metodo [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) viene chiamato due volte, una volta con il `imagetoSymbols` parametro impostato su `TRUE` e una volta con il `imagetoSymbols` parametro impostato su `FALSE` . Non è possibile abilitare le traduzioni della mappa indirizzi usando il metodo [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) , a meno che non vengano fornite entrambe le mappe di traduzione.

## <a name="see-also"></a>Vedi anche
- [Struttura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
