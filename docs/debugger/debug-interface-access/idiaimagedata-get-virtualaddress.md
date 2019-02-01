---
title: Idiaimagedata | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_virtualAddress method
ms.assetid: 67ecdc8c-d342-4d0b-b02a-c6b88e22fd02
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 09e4ba99f22ef620f1f761bfa88dd0cd1ec00906
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919837"
---
# <a name="idiaimagedatagetvirtualaddress"></a>IDiaImageData::get_virtualAddress
Recupera la posizione nella memoria virtuale dell'immagine.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
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