---
title: IActiveScript::Close | Microsoft Docs
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
ms.openlocfilehash: 53b71471ada55751de301391fdcc70387c1bb6c2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157049"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Fa sì che il motore di scripting abbandonare tutti gli script attualmente caricato, perdono il proprio stato e rilasciare eventuali puntatori a interfaccia che dispone ad altri oggetti, quindi immettere uno stato chiuso. Sink di evento, il testo script eseguito immediatamente e le chiamate alle macro che sono già in corso vengono completati prima i cambiamenti di stato (usare [IActiveScript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) per annullare un thread in esecuzione di script). Questo metodo deve essere chiamato dall'host di creazione prima del rilascio dell'interfaccia per evitare problemi relativi ai riferimenti circolari.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore|Significato|  
|-----------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di script era già in stato di chiusura).|  
|`OLESCRIPT_S_PENDING`|Il metodo è stato accodato correttamente, ma lo stato non è stato modificato ancora. Quando i cambiamenti di stato, il sito viene richiamata nel [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) (metodo).|  
|`S_FALSE`|Il metodo ha avuto esito positivo, ma lo script è già stato chiuso.|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)