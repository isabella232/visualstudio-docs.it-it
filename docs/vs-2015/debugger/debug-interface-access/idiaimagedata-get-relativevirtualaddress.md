---
title: Idiaimagedata | Microsoft Docs
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
- IDiaImageData::get_relativeVirtualAddress method
ms.assetid: e6d6deee-dc12-4b38-af15-f917b2d4368e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd09468aa038997a6ba7b02bcb9143bb61cc87e5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794088"
---
# <a name="idiaimagedatagetrelativevirtualaddress"></a>IDiaImageData::get_relativeVirtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera la posizione nella memoria virtuale del modulo relativo all'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_relativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce l'offset relativo della memoria virtuale del modulo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)



