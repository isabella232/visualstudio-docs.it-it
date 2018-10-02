---
title: Set_imageheaders | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6ec20d37f06f5a51ebf83b1212feafd886f84b4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531841"
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Set_imageheaders](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaaddressmap-set-imageheaders).  
  
Set di intestazioni per abilitare la conversione dell'indirizzo virtuale relativo dell'immagine.  
  
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
 [in] Numero di byte di dati dell'intestazione. Deve essere `n*sizeof(IMAGE_SECTION_HEADER)` in cui `n` è il numero di intestazioni delle sezioni nel file eseguibile.  
  
 [dati]  
 [in] Matrice di `IMAGE_SECTION_HEADER` strutture da utilizzare come intestazioni di immagine.  
  
 originalHeaders  
 [in] Impostare su `FALSE` se le intestazioni di immagine dalla nuova immagine, `TRUE` se riflettono l'immagine originale prima di un aggiornamento. In genere, ciò verrebbe impostato su `TRUE` solo in combinazione con le chiamate per il [Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) (metodo).  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il `IMAGE_SECTION_HEADER` struttura è dichiarato in Winnt. h e rappresenta il formato dell'intestazione sezione del file eseguibile.  
  
 I calcoli di indirizzo virtuale relativo variano a seconda di `IMAGE_SECTION_HEADER` valori. In genere, il DIA recupera queste informazioni dal file di database (con estensione pdb) di programma. Se questi valori sono mancanti, il DIA non riesce a calcolare indirizzi virtuali relativi e la [Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) restituzione del metodo `FALSE`. Il client deve quindi chiamare il [Put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) metodo per consentire i calcoli di indirizzo virtuale relativo dopo aver fornito le intestazioni di immagine mancante dall'immagine di se stesso.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)



