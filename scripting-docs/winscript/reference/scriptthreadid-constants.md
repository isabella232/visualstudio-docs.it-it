---
title: Costanti SCRIPTTHREADID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADID
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADID
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27852f97cf0a78919b10043c64b1c5a7cc7d3ec5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097812"
---
# <a name="scriptthreadid-constants"></a>Costanti SCRIPTTHREADID
Consente di specificare il tipo di thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Costanti  
  
|Costante|Value|Significato|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|Il thread attualmente in esecuzione.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|Thread di base; vale a dire, il thread in cui la creazione di script del motore è stata creata un'istanza.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|Tutti i thread.|  
  
## <a name="remarks"></a>Note  
 Il `SCRIPTTHREADID` tipo viene utilizzato da `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`, e `IActiveScript::InterruptScriptThread`, ma le costanti possono essere utilizzate solo da `IActiveScript::GetScriptThreadState` e `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)