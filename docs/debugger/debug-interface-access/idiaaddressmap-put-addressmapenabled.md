---
title: Put_addressmapenabled | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: f139e6d034fc3b738e345f385fbb8e8ad2150da4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915386"
---
# <a name="idiaaddressmapputaddressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Specifica se la mappa indirizzi deve essere utilizzata per convertire gli indirizzi di simboli.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 NewVal  
 [in] Impostare su `TRUE` per abilitare la traduzione di simboli o `FALSE` disabilitare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Eseguibile postprocessori talvolta aggiornare il file eseguibile. DIA contiene un meccanismo per supportare la traduzione di simboli a cui il nuovo layout.  
  
 Quando viene caricato un file PDB, viene abilitata la mappa indirizzi archiviata nel file. Esistono casi, tuttavia, quando un'applicazione client potrebbe essere necessario fornire la propria mappa indirizzo chiamando il [Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) (metodo). Se il `set_addressMap` metodo ha esito positivo, l'applicazione client deve chiamare il `put_addressMapEnabled` metodo con un `NewVal` parametri di `TRUE` per consentire l'uso della mappa tale indirizzo.  
  
 Può essere recuperato lo stato corrente della mappa indirizzo viene abilitata con una chiamata ai [Get_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)