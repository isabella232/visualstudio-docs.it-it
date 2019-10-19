---
title: 'IActiveScript:: Close | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f858de42ef2948d218aac6c3194cc6af544da5e9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575787"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Fa in modo che il motore di script abbandoni tutti gli script attualmente caricati, perda il proprio stato e rilasci tutti i puntatori di interfaccia che contiene ad altri oggetti, entrando quindi in uno stato chiuso. I sink di evento, il testo dello script immediatamente eseguito e le chiamate di macro già in corso vengono completati prima che lo stato venga modificato (usare [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) per annullare un thread di script in esecuzione). Questo metodo deve essere chiamato dall'host di creazione prima che l'interfaccia venga rilasciata per evitare problemi di riferimento circolare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Value|Significato|  
|-----------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_UNEXPECTED`|La chiamata non era prevista (ad esempio, il motore di scripting era già nello stato Closed).|  
|`OLESCRIPT_S_PENDING`|Il metodo è stato accodato correttamente, ma lo stato non è ancora stato modificato. Quando lo stato viene modificato, il sito deve essere richiamato nel metodo [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .|  
|`S_FALSE`|Il metodo ha avuto esito positivo, ma lo script è già stato chiuso.|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)