---
title: Costanti SCRIPTTHREADID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: bf1b23b191bda29b00bf29f482332301897f9f37
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575662"
---
# <a name="scriptthreadid-constants"></a>Costanti SCRIPTTHREADID
Utilizzato per specificare il tipo di thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Costanti  
  
|Costante|Value|Significato|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|Thread attualmente in esecuzione.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|Thread di base; ovvero il thread in cui è stata creata un'istanza del motore di script.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|Tutti i thread.|  
  
## <a name="remarks"></a>Note  
 Il tipo di `SCRIPTTHREADID` viene utilizzato da `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState` e `IActiveScript::InterruptScriptThread`, ma le costanti possono essere utilizzate solo da `IActiveScript::GetScriptThreadState` e `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 [IActiveScript:: GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)  
 @No__t_1 [IActiveScript:: GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)  
 @No__t_1 [IActiveScript:: GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)  
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)