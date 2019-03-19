---
title: IActiveScript::GetScriptThreadState | Microsoft Docs
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
ms.openlocfilehash: a0066894830c111a8e0ad18f7acdc09d6114162e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145967"
---
# <a name="iactivescriptgetscriptthreadstate"></a>IActiveScript::GetScriptThreadState
Recupera lo stato corrente di un thread dello script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `stidThread`  
 [in] Identificatore del thread per il quale si desidera lo stato, o uno degli identificatori di thread speciali seguenti:  
  
|Value|Significato|  
|-----------|-------------|  
|SCRIPTTHREADID_BASE|Thread di base; vale a dire, il thread in cui la creazione di script del motore è stata creata un'istanza.|  
|SCRIPTTHREADID_CURRENT|Il thread attualmente in esecuzione.|  
  
 `pstsState`  
 [out] Indirizzo di una variabile che riceve lo stato del thread indicato. Lo stato è indicato da uno dei valori di costante denominati definiti per il [enumerazione SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md) enumerazione. Se questo parametro identifica il thread corrente, lo stato può cambiare in qualsiasi momento.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di scripting non è ancora caricato o inizializzato).|  
  
## <a name="remarks"></a>Note  
 Questo metodo può essere chiamato dal thread non di base senza causando un callout non in base agli oggetti di host o al [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)