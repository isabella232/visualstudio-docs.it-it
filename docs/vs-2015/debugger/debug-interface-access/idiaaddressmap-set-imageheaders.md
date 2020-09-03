---
title: IDiaAddressMap::set_imageHeaders | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18fa69929f78d5ae661169a09db97697d98f4d94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198645"
---
# <a name="idiaaddressmapset_imageheaders"></a>IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Imposta le intestazioni dell'immagine per abilitare la conversione di indirizzi virtuali relativa.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 cbData  
 in Numero di byte dei dati di intestazione. Deve essere `n*sizeof(IMAGE_SECTION_HEADER)` dove `n` è il numero di intestazioni di sezione nell'eseguibile.  
  
 data[]  
 in Matrice di  `IMAGE_SECTION_HEADER` strutture da utilizzare come intestazioni di immagine.  
  
 originalHeaders  
 in Impostare su `FALSE` se le intestazioni di immagine sono della nuova immagine, `TRUE` se riflettono l'immagine originale prima di un aggiornamento. In genere, viene impostato su `TRUE` solo in combinazione con le chiamate al metodo [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 La `IMAGE_SECTION_HEADER` struttura viene dichiarata in Winnt. h e rappresenta il formato dell'intestazione della sezione dell'immagine del file eseguibile.  
  
 I calcoli degli indirizzi virtuali relativi dipendono dai `IMAGE_SECTION_HEADER` valori. In genere, il DIA li recupera dal file di database di programma (con estensione pdb). Se questi valori sono mancanti, il DIA non è in grado di calcolare gli indirizzi virtuali relativi e il metodo [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) restituisce `FALSE` . Il client deve quindi chiamare il metodo [IDiaAddressMap::p ut_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) per abilitare i calcoli degli indirizzi virtuali relativi dopo aver fornito le intestazioni di immagine mancanti dall'immagine stessa.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)
