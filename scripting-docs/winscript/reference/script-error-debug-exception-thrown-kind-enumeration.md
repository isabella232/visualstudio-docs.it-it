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
ms.openlocfilehash: 3be6989195eacdd4d70bd13790d55e4f6cfc769d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443634"
---
# <a name="scripterrordebugexceptionthrownkind-enumeration"></a>Enumerazione SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Indica il tipo di eccezione generata. Questa enumerazione viene utilizzata per la [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) (metodo).  
  
> [!IMPORTANT]
> Queste costanti sono implementate da PDM versione 11.0 e successiva. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Membri  
  
|Member|Value|Descrizione|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|L'eccezione è un'eccezione first-chance.|  
|ETK_USER_UNHANDLED|0x00000001|L'eccezione non è gestita nel codice utente.|  
|ETK_UNHANDLED|0x00000002|L'eccezione non è gestita nel codice.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)