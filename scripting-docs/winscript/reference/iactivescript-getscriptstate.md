---
title: 'IActiveScript:: GetScriptState | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d266e713879aafe1c5ca271d46b3030f3275460f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575732"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Recupera lo stato corrente del motore di script. Questo metodo può essere chiamato da thread non di base senza comportare un callout non di base per ospitare oggetti o per l'interfaccia [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pss`  
 out Indirizzo di una variabile che riceve un valore definito nell'enumerazione [SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md) . Il valore indica lo stato corrente del motore di scripting associato al thread chiamante.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se ha esito positivo oppure `E_POINTER` se è stato specificato un puntatore non valido.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)