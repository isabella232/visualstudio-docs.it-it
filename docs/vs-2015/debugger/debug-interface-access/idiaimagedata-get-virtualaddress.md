---
title: Idiaimagedata | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_virtualAddress method
ms.assetid: 67ecdc8c-d342-4d0b-b02a-c6b88e22fd02
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df8a8a351fb7557d5483b006c9b0b31ea7fcf27d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965896"
---
# <a name="idiaimagedatagetvirtualaddress"></a>IDiaImageData::get_virtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera la posizione nella memoria virtuale dell'immagine.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_virtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce l'indirizzo virtuale dell'immagine.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)
