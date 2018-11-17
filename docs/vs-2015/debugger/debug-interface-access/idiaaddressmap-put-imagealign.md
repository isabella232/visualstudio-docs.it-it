---
title: Put_imagealign | Microsoft Docs
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
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4c745d6b9df5f58b4aa2431a051e6fa583c73d7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773704"
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Imposta l'allineamento dell'immagine.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 NewVal  
 [in] Il valore di allineamento immagine nuova del file eseguibile.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Immagini (caricare file eseguibili) sono allineate a limiti di memoria specificato. Questo allineamento può essere influenzato dall'architettura di sistema corrente e da opzioni della fase di compilazione e collegamento. Allineamento dell'immagine è sempre nei limiti di byte. I valori di allineamento di immagine seguenti sono validi: i limiti di 1, 2, 4, 8, 16, 32 e 64 byte.  
  
 L'allineamento dell'immagine corrente può essere recuperato con una chiamata per il [Get_imagealign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) (metodo).  
  
> [!NOTE]
>  L'immagine è già caricata entro l'ora di che questo metodo può essere chiamato. Il `put_imageAlign` metodo viene in genere utilizzato quando l'immagine è stato spostato o modificato e un allineamento nuovo è obbligatorio.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)



