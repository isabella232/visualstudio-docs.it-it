---
title: 'IActiveScript:: Setscriptstate | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 58edef17fec1d94a09b327dff626658c42a273ba
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095030"
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
 [IActiveScript:: Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript:: Getscriptdispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [Iactivescriptparse:: Parsescripttext](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)