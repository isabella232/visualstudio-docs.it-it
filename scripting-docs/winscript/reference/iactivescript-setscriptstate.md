---
title: 'IActiveScript:: SetScriptState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptState
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea947e00ffd5a3498261f4a3a8acd4791e8ace60
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577997"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Inserisce il motore di scripting nello stato specificato. Questo metodo può essere chiamato da thread non di base senza comportare un callout non di base per ospitare oggetti o per l'interfaccia [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ss`  
 in Imposta il motore di scripting sullo stato specificato. Può essere uno dei valori definiti nell'enumerazione [SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md) .  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_FAIL`|Il motore di scripting non supporta la transizione allo stato inizializzato. L'host deve eliminare questo motore di script e creare, inizializzare e caricare un nuovo motore di script per ottenere lo stesso effetto.|  
|`E_UNEXPECTED`|La chiamata non era prevista (ad esempio, il motore di scripting non è ancora stato caricato o inizializzato) e pertanto non è riuscito.|  
|`OLESCRIPT_S_PENDING`|Il metodo è stato accodato correttamente, ma lo stato non è ancora stato modificato. Quando lo stato viene modificato, il sito verrà richiamato tramite il metodo [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .|  
|`S_FALSE`|Il metodo ha avuto esito positivo, ma lo script si trovava già nello stato specificato.|  
  
## <a name="remarks"></a>Note  
 Per ulteriori informazioni sugli Stati del motore di script, vedere la sezione Stati del motore di script dei [motori di script Windows](../../winscript/windows-script-engines.md) .  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 [IActiveScript:: Clone](../../winscript/reference/iactivescript-clone.md)  
 @No__t_1 [IActiveScript:: GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)  
 @No__t_1 [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)  
 [IActiveScriptParse::P arsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md)    
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)