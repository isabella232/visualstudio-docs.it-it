---
title: PROFILER_SCRIPT_TYPE Enumeration | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_SCRIPT_TYPE
apilocation:
- scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca90a566db422d75fefc44267ffe10504bb872ce
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157438"
---
# <a name="profilerscripttype-enumeration"></a>Enumerazione PROFILER_SCRIPT_TYPE
Specifica il tipo di script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|Specifica il codice di script scritto dall'utente.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Specifica il codice di script che viene generato in modo dinamico durante l'esecuzione.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Specifica il tipo di script per le funzioni native e gli oggetti definiti dal motore di script.|  
|PROFILER_SCRIPT_TYPE_DOM|Specifica una chiamata nel documento oggetto Model (DOM) di Internet Explorer, ad esempio, una chiamata al `document.getElementById` (metodo).|  
  
## <a name="see-also"></a>Vedere anche  
 [Script ActiveX Profiler costanti, enumerazioni e strutture](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)