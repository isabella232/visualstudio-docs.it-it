---
title: 'IActiveScript:: GetScriptThreadState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadState
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38f6ef4b0acdf6e3b746316bef8abe9a3f0f8225
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578000"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Recupera lo stato corrente di un thread di script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `stidThread`  
 in Identificatore del thread per il quale si desidera lo stato o uno dei seguenti identificatori di thread speciali:  
  
|Value|Significato|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Thread di base; ovvero il thread in cui è stata creata un'istanza del motore di script.|  
|SCRIPTTHREADID_CURRENT|Thread attualmente in esecuzione.|  
  
 `pstsState`  
 out Indirizzo di una variabile che riceve lo stato del thread indicato. Lo stato è indicato da uno dei valori costanti denominati definiti dall'enumerazione [SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md) . Se questo parametro non identifica il thread corrente, lo stato potrebbe cambiare in qualsiasi momento.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era prevista (ad esempio, il motore di scripting non è ancora stato caricato o inizializzato).|  
  
## <a name="remarks"></a>Note  
 Questo metodo può essere chiamato da thread non di base senza comportare un callout non di base per ospitare oggetti o per l'interfaccia [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)