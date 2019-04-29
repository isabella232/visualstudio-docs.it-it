---
title: 'IActiveScript:: Setscriptstate | Microsoft Docs'
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
ms.openlocfilehash: 16a13b545ddd482f8aa143d289d46447370e23ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935531"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Inserisce il motore di scripting nello stato specificati. Questo metodo può essere chiamato dal thread non di base senza causando un callout non in base agli oggetti di host o al [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfaccia.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ss`  
 [in] Imposta il motore di scripting per lo stato specificati. Può essere uno dei valori definiti nel [enumerazione SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md) enumerazione.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_FAIL`|Il motore di scripting non supporta la transizione allo stato inizializzato. L'host deve annullare questo motore di script e creare, inizializzare e caricare un nuovo motore di scripting per ottenere lo stesso effetto.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di scripting non è ancora caricato o inizializzato) e pertanto non è riuscita.|  
|`OLESCRIPT_S_PENDING`|Il metodo è stato accodato correttamente, ma lo stato non è stato modificato ancora. Quando le modifiche di stato, il sito verrà richiamato tramite il [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) (metodo).|  
|`S_FALSE`|Il metodo ha avuto esito positivo, ma lo script è stato già nello stato specificato.|  
  
## <a name="remarks"></a>Note  
 Per altre informazioni sugli stati del motore di script, vedere la sezione degli Stati del motore di Script di [motori di Script di Windows](../../winscript/windows-script-engines.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)