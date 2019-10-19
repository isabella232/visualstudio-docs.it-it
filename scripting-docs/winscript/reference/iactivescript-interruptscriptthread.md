---
title: 'IActiveScript:: InterruptScriptThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.InterruptScriptThread
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a436f973df05b945c0939f3a593640f567774277
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577259"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Interrompe l'esecuzione di un thread di script in esecuzione (un sink di evento, un'esecuzione immediata o una chiamata di macro). Questo metodo può essere utilizzato per terminare uno script bloccato, ad esempio in un ciclo infinito. Può essere chiamato da thread non di base senza comportare un callout non di base per ospitare oggetti o per il metodo [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `stidThread`  
 in Identificatore del thread da interrompere o uno dei seguenti valori speciali dell'identificatore del thread:  
  
|Value|Significato|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Tutti i thread. L'interrupt viene applicato a tutti i metodi di script attualmente in corso. Si noti che, a meno che il chiamante non abbia richiesto che lo script venga disconnesso, il successivo evento con script fa in modo che il codice script venga eseguito di nuovo chiamando il metodo [IActiveScript:: SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) con il flag SCRIPTSTATE_DISCONNECTED o SCRIPTSTATE_INITIALIZED set.|  
|SCRIPTTHREADID_BASE|Thread di base; ovvero il thread in cui è stata creata un'istanza del motore di script.|  
|SCRIPTTHREADID_CURRENT|Thread attualmente in esecuzione.|  
  
 `pexcepinfo`  
 in Indirizzo di una struttura `EXCEPINFO` contenente le informazioni sull'errore che devono essere segnalate allo script interrotto.  
  
 `dwFlags`  
 in Flag di opzione associati all'interruzione. Può essere uno dei seguenti valori:  
  
|Value|Significato|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Se supportato, immettere il debugger del motore di script in corrispondenza del punto di esecuzione dello script corrente.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Se supportato dal linguaggio del motore di script, consentire allo script di gestire l'eccezione. In caso contrario, il metodo script viene interrotto e il codice di errore viene restituito al chiamante. ovvero l'origine evento o l'invoker della macro.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era prevista (ad esempio, il motore di scripting non è ancora stato caricato o inizializzato).|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)