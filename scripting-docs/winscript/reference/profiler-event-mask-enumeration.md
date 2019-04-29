---
title: Enumerazione PROFILER_EVENT_MASK | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_EVENT_MASK
apilocation:
- scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7230e65e5559d53e56cf6424a34dd44aa4edda7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831642"
---
# <a name="profilereventmask-enumeration"></a>Enumerazione PROFILER_EVENT_MASK
Indica i tipi di eventi che devono essere profilati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef enum {  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL = 0x00000001,  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL = 0x00000002,  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL    = 0x00000004,  
    PROFILER_EVENT_MASK_TRACE_ALL =  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL |  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL,  
    PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM = PROFILER_EVENT_MASK_TRACE_ALL |  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL  
} PROFILER_EVENT_MASK;  
```  
  
## <a name="members"></a>Membri  
  
|Member|Descrizione|  
|------------|-----------------|  
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|Funzioni di profili che sono definite nello script scritto dall'utente e codice dinamico.|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|Funzioni native profili definiti dal motore di script.|  
|PROFILER_EVENT_MASK_TRACE_ALL|I profili di tutte le funzioni definite dall'utente e di scripting del motore, escluse le chiamate nel modello DOM (Document Object).|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|Funzioni di profili che effettuano chiamate nel DOM.|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|I profili di tutte le funzioni, tra cui le chiamate nel DOM.|  
  
## <a name="see-also"></a>Vedere anche  
 [Script ActiveX Profiler costanti, enumerazioni e strutture](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)