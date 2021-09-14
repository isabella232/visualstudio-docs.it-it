---
description: Imposta le intestazioni dell'immagine per abilitare la conversione degli indirizzi virtuali relativi.
title: IDiaAddressMap::set_imageHeaders | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3acedb7cf87d9dac560f552a305fc736f7b570fe
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630521"
---
# <a name="idiaaddressmapset_imageheaders"></a>IDiaAddressMap::set_imageHeaders
Imposta le intestazioni dell'immagine per abilitare la conversione degli indirizzi virtuali relativi.

## <a name="syntax"></a>Sintassi

```C++
HRESULT set_imageHeaders ( 
   DWORD cbData,
   BYTE  data[],
   BOOL  originalHeaders
);
```

#### <a name="parameters"></a>Parametri
 cbData

[in] Numero di byte di dati di intestazione. Deve essere `n*sizeof(IMAGE_SECTION_HEADER)` dove è il numero di intestazioni di sezione nel file `n` eseguibile.

 data[]

[in] Matrice di  `IMAGE_SECTION_HEADER` strutture da utilizzare come intestazioni dell'immagine.

 originalHeaders

[in] Impostare su `FALSE` se le intestazioni dell'immagine sono della nuova immagine, se `TRUE` riflettono l'immagine originale prima di un aggiornamento. In genere, questa proprietà viene impostata su solo in combinazione con le chiamate al metodo `TRUE` [IDiaAddressMap::set_addressMap.](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 La `IMAGE_SECTION_HEADER` struttura è dichiarata in Winnt.h e rappresenta il formato di intestazione della sezione image del file eseguibile.

 I calcoli relativi degli indirizzi virtuali dipendono dai `IMAGE_SECTION_HEADER` valori. In genere, la dia recupera questi dati dal file di database di programma (con estensione pdb). Se questi valori non sono presenti, il dia non è in grado di calcolare gli indirizzi virtuali relativi e il metodo [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) restituisce `FALSE` . Il client deve quindi chiamare il metodo [IDiaAddressMap::p ut_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) per abilitare i calcoli relativi degli indirizzi virtuali dopo aver fornito le intestazioni di immagine mancanti dall'immagine stessa.

## <a name="see-also"></a>Vedi anche
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)
