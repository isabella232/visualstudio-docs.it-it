---
title: IDiaAddressMap::put_imageAlign | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e0fa57c38c8451bde84d96ab32bc7980c5e2d8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839596"
---
# <a name="idiaaddressmapput_imagealign"></a>IDiaAddressMap::put_imageAlign
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
 in Nuovo valore di allineamento dell'immagine per l'eseguibile.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Commenti  
 Le immagini (file eseguibili caricati) sono allineate ai limiti di memoria specificati. Questo allineamento può essere influenzato dall'architettura del sistema corrente e dalle opzioni di tempo di compilazione e collegamento. L'allineamento delle immagini è sempre in corrispondenza dei limiti di byte. I valori di allineamento immagine seguenti sono validi: 1, 2, 4, 8, 16, 32 e 64 limiti di byte.  
  
 L'allineamento dell'immagine corrente può essere recuperato con una chiamata al metodo [IDiaAddressMap:: get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) .  
  
> [!NOTE]
> L'immagine è già caricata nel momento in cui è possibile chiamare questo metodo. Il `put_imageAlign` metodo viene in genere utilizzato quando l'immagine è stata spostata o modificata ed è necessario un nuovo allineamento.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)
