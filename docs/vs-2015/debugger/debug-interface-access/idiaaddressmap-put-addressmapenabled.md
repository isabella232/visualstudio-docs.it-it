---
title: Put_addressmapenabled | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24098d21644b51c134aa7ea20d2ee6efd6d7e814
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193570"
---
# <a name="idiaaddressmapputaddressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Specifica se la mappa indirizzi deve essere utilizzata per convertire gli indirizzi di simboli.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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



