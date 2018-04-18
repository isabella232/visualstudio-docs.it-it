---
title: 'Idiaaddressmap:: Put_addressmapenabled | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a9d81a9204987348f7664f53c1873ddbbfc62cf0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idiaaddressmapputaddressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Specifica se la mappa indirizzi deve essere utilizzata per convertire gli indirizzi di simbolo.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 NewVal  
 [in] Impostare su `TRUE` per abilitare la conversione dei simboli, o `FALSE` disabilitare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Post-processori di eseguibile talvolta aggiornare il file eseguibile. DIA contiene un meccanismo per supportare la conversione dei simboli per il nuovo layout.  
  
 Quando viene caricato un file PDB, è abilitata la mappa indirizzi archiviata nel file. Esistono casi, tuttavia, quando un'applicazione client potrebbe essere necessario fornire il proprio indirizzo di mappa chiamando il [idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metodo. Se il `set_addressMap` metodo ha esito positivo, l'applicazione client deve chiamare il `put_addressMapEnabled` metodo con un `NewVal` parametro di `TRUE` per consentire l'utilizzo di tale mappa indirizzo.  
  
 Lo stato corrente della mappa indirizzo abilitata può essere recuperato con una chiamata al [idiaaddressmap:: Get_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)