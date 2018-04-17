---
title: 'Idiaaddressmap:: Put_imagealign | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c40e2f325ac30eb109f72615e5cc74a5d30e5eba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
Imposta l'allineamento dell'immagine.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 NewVal  
 [in] Nuovo valore di allineamento immagine per il file eseguibile.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Immagini, caricare file eseguibili, vengono allineate ai limiti di memoria specificata. L'allineamento in quanto può essere influenzata dall'architettura di sistema corrente e da opzioni della fase di compilazione e collegamento. L'allineamento dell'immagine è sempre nei limiti di byte. I valori di allineamento immagine seguente sono validi: i limiti di 1, 2, 4, 8, 16, 32 e 64 byte.  
  
 L'allineamento dell'immagine corrente può essere recuperato con una chiamata al [idiaaddressmap:: Get_imagealign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) metodo.  
  
> [!NOTE]
>  L'immagine è già caricato nel momento in cui che questo metodo può essere chiamato. Il `put_imageAlign` metodo viene in genere utilizzato quando l'immagine è stato spostato o modificato e un nuovo allineamento è obbligatorio.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)