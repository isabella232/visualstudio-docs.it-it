---
title: IDiaAddressMap::put_addressMapEnabled | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f2f7fc6fd512fa121cf96cb64f4ce4b961772e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198680"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Specifica se la mappa degli indirizzi deve essere utilizzata per tradurre gli indirizzi dei simboli.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 NewVal  
 in Impostare su `TRUE` per abilitare la conversione dei simboli o `FALSE` per disabilitare.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 I successivi processori eseguibili a volte aggiornano il file eseguibile. DIA contiene un meccanismo per supportare la conversione di simboli nel nuovo layout.  
  
 Quando viene caricato un file PDB, la mappa degli indirizzi archiviata nel file è abilitata. In alcuni casi, tuttavia, quando un'applicazione client potrebbe dover fornire la propria mappa degli indirizzi chiamando il metodo [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) . Se il `set_addressMap` metodo ha esito positivo, l'applicazione client deve chiamare il `put_addressMapEnabled` metodo con un `NewVal` parametro di `TRUE` per consentire l'uso di tale mappa di indirizzi.  
  
 Lo stato corrente della mappa degli indirizzi abilitata può essere recuperato con una chiamata al metodo [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)
