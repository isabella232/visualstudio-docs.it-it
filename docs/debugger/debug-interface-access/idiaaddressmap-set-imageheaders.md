---
title: IDiaAddressMap::set_imageHeaders | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10835f422f8d2d116234eadd91da0d27c424f314
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635943"
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
Set di intestazioni per abilitare la conversione dell'indirizzo virtuale relativo dell'immagine.

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

[in] Numero di byte di dati dell'intestazione. Deve essere `n*sizeof(IMAGE_SECTION_HEADER)` in cui `n` è il numero di intestazioni delle sezioni nel file eseguibile.

 data[]

[in] Matrice di `IMAGE_SECTION_HEADER` strutture da utilizzare come intestazioni di immagine.

 originalHeaders

[in] Impostare su `FALSE` se le intestazioni di immagine dalla nuova immagine, `TRUE` se riflettono l'immagine originale prima di un aggiornamento. In genere, ciò verrebbe impostato su `TRUE` solo in combinazione con le chiamate per il [Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) (metodo).

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Il `IMAGE_SECTION_HEADER` struttura è dichiarato in Winnt. h e rappresenta il formato dell'intestazione sezione del file eseguibile.

 I calcoli di indirizzo virtuale relativo variano a seconda di `IMAGE_SECTION_HEADER` valori. In genere, il DIA recupera queste informazioni dal file di database (con estensione pdb) di programma. Se questi valori sono mancanti, il DIA non riesce a calcolare indirizzi virtuali relativi e la [Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) restituzione del metodo `FALSE`. Il client deve quindi chiamare il [Put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) metodo per consentire i calcoli di indirizzo virtuale relativo dopo aver fornito le intestazioni di immagine mancante dall'immagine di se stesso.

## <a name="see-also"></a>Vedere anche
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)