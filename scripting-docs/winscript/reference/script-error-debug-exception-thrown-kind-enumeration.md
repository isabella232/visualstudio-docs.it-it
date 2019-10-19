---
title: Enumerazione SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8eb089efbf608b488465809f997ffc82fc2c2e3c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574402"
---
# <a name="script_error_debug_exception_thrown_kind-enumeration"></a>Enumerazione SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Indica il tipo di eccezione generata. Questa enumerazione viene utilizzata dal metodo [IActiveScriptErrorDebug110:: GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) .  
  
> [!IMPORTANT]
> Queste costanti sono implementate da PDM versione 11.0 e successiva. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Members  
  
|Member|Value|Descrizione|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|L'eccezione è un'eccezione first-chance.|  
|ETK_USER_UNHANDLED|0x00000001|L'eccezione non è gestita nel codice utente.|  
|ETK_UNHANDLED|0x00000002|L'eccezione non è gestita nel codice.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)