---
title: IDiaImageData::get_imageBase | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4a8ed3f52a6e4709aa9553b0d7cc906069c9bcd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968683"
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera la posizione di memoria in cui deve basarsi l'immagine.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce il valore di base dell'immagine suggerita.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 A causa di conflitti di base di immagine, un'immagine può essere riassegnata automaticamente in una posizione di memoria inutilizzata al momento del caricamento. Questo metodo restituisce l'hint di base (percorso consigliato per la memoria) che è stato archiviato nel modulo in fase di compilazione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)
