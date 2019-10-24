---
title: IDiaAddressMap::set_addressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8414788af44d78943088b78b2d3e42a5a8d8c50b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745020"
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

in Numero di elementi nel parametro `data`.

 `data[]`

in Matrice di strutture di [struttura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md) che definiscono la mappa di conversione.

 `imagetoSymbols`

[in] `TRUE` se il parametro `data` definisce una mappa dal nuovo layout dell'immagine al layout originale (come descritto dai simboli di debug). `FALSE` se `data` è un mapping al nuovo layout dell'immagine tratto dal layout originale.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 In genere, il diametro recupera le mappe degli indirizzi da un file di database di programma (con estensione pdb). Se questi valori sono mancanti, il metodo [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) viene chiamato due volte, una volta con il parametro `imagetoSymbols` impostato su `TRUE` e una volta con il parametro `imagetoSymbols` impostato su `FALSE`. Non è possibile abilitare le traduzioni della mappa indirizzi usando il metodo [IDiaAddressMap::P ut_addressmapenabled,](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) a meno che non siano disponibili entrambe le mappe di conversione.

## <a name="see-also"></a>Vedere anche
- [Struttura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)