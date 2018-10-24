---
title: Get_functionstart | Microsoft Docs
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
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0a39212fd93138444c6aa412071cec4894b0667
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812686"
---
# <a name="idiaframedatagetfunctionstart"></a>IDiaFrameData::get_functionStart
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera un flag che indica se il blocco contiene il punto di ingresso di una funzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_functionStart (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce `TRUE` se il blocco contiene il punto di ingresso; in caso contrario restituisce `FALSE`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 È possibile che uno stack frame non sia l'inizio di una funzione in quanto il frame rappresenta un metodo in linea o una funzione inserito in una funzione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



