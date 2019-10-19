---
title: Enumerazione PROFILER_SCRIPT_TYPE | Microsoft Docs
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
ms.openlocfilehash: e08583f9bb914adfbd144715646991c6070f3f32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574576"
---
# <a name="profiler_script_type-enumeration"></a>Enumerazione PROFILER_SCRIPT_TYPE
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
  
## <a name="members"></a>Members  
  
|Member|Descrizione|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|Specifica il codice di script scritto dall'utente.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Specifica il codice di script generato in modo dinamico durante l'esecuzione.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Specifica il tipo di script per le funzioni native e gli oggetti definiti dal motore di scripting.|  
|PROFILER_SCRIPT_TYPE_DOM|Specifica una chiamata al Document Object Model (DOM) di Internet Explorer, ad esempio una chiamata al metodo `document.getElementById`.|  
  
## <a name="see-also"></a>Vedere anche  
 [Costanti, enumerazioni e strutture del profiler di script activex](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)    
 @No__t_1 [IActiveScriptProfilerCallback:: ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)  
 @No__t_1 [IActiveScriptProfilerCallback2:: OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)