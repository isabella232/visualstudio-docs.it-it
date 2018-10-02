---
title: IDiaStackWalkHelper::get_registerValue | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 58876436a426a71df3f13df1e5857d9dbdace025
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526256"
---
# <a name="idiastackwalkhelpergetregistervalue"></a>IDiaStackWalkHelper::get_registerValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDiaStackWalkHelper::get_registerValue](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalkhelper-get-registervalue).  
  
Recupera il valore di un registro.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `index`  
 [in] Un valore compreso il [enumerazione CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) enumerazione che specifica quale registro da cui per ottenere il valore.  
  
 `pRetVal`  
 [out] Restituisce il valore corrente del registro.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Nonostante le dimensioni del `pRetVal` parametro, un'implementazione deve archiviare solo registro in genere conserva. Un registro a 8 bit, ad esempio, contiene solo i bit più bassi 8-del valore specificato. Questo valore a 8 bit viene espanso a 64-bit quando restituito da questo metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Enumerazione CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)



