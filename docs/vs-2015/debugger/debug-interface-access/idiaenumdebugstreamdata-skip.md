---
title: Idiaenumdebugstreamdata | Microsoft Docs
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
- IDiaEnumDebugStreamData::Skip method
ms.assetid: 106ae1d3-a379-4077-babf-2665e697b0c4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0558209c8ad7d328194e9958421c21048e6cef94
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874631"
---
# <a name="idiaenumdebugstreamdataskip"></a>IDiaEnumDebugStreamData::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ignora un determinato numero di record in una sequenza enumerata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 celt  
 [in] Il numero di record da ignorare nella sequenza enumerata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` se sono presenti più record da ignorare.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)



