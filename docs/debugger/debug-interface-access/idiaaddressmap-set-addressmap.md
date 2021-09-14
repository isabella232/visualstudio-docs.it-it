---
description: Fornisce una mappa indirizzi per supportare le traduzioni del layout delle immagini.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: dd73b8bad816556ac598bc4c2c115e29f660e0fa
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630522"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
Fornisce una mappa indirizzi per supportare le traduzioni del layout delle immagini.

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

[in] Numero di elementi nel `data` parametro .

 `data[]`

[in] Matrice di [strutture DiaAddressMapEntry che](../../debugger/debug-interface-access/diaaddressmapentry.md) definiscono la mappa di conversione.

 `imagetoSymbols`

[in] `TRUE` se il `data` parametro definisce una mappa dal nuovo layout di immagine al layout originale (come descritto dai simboli di debug). `FALSE` se `data` è una mappa al nuovo layout dell'immagine tratto dal layout originale.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 In genere, la dia recupera le mappe di conversione degli indirizzi dal file di database di programma (con estensione pdb). Se questi valori non sono presenti, il metodo [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) viene chiamato due volte, una volta con il parametro impostato su e una volta con il parametro `imagetoSymbols` impostato su `TRUE` `imagetoSymbols` `FALSE` . Le traduzioni della mappa indirizzi non possono essere abilitate usando il metodo [IDiaAddressMap::p ut_addressMapEnabled,](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) a meno che non vengano fornite entrambe le mappe di traduzione.

## <a name="see-also"></a>Vedi anche
- [Struttura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
