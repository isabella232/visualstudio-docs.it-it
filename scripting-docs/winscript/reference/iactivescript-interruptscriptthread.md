---
title: 'IActiveScript:: Interruptscriptthread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d20847245e25ec6227bb043df3190a6db5f095d5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088933"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Interrompe l'esecuzione di un thread dello script in esecuzione (un sink di evento, un'esecuzione immediata o una chiamata di macro). Questo metodo può essere utilizzato per terminare uno script che è bloccato (ad esempio, in un ciclo infinito). Può essere chiamato dal thread non di base senza causando un callout non in base agli oggetti di host o al [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) (metodo).  
  
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
 [in] Identificatore del thread di interrupt o uno dei valori identificatore thread speciali seguenti:  
  
|Value|Significato|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Tutti i thread. L'interruzione viene applicato a tutti i metodi di script attualmente in corso. Si noti che, a meno che il chiamante ha richiesto che lo script di disconnessione, l'evento successivo con script comporta il codice di script eseguire di nuovo chiamando il [IActiveScript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) metodo con il SCRIPTSTATE_DISCONNECTED o Set di flag SCRIPTSTATE_INITIALIZED.|  
|SCRIPTTHREADID_BASE|Thread di base; vale a dire, il thread in cui la creazione di script del motore è stata creata un'istanza.|  
|SCRIPTTHREADID_CURRENT|Il thread attualmente in esecuzione.|  
  
 `pexcepinfo`  
 [in] Indirizzo di un `EXCEPINFO` struttura che contiene le informazioni sull'errore che deve essere segnalati allo script interrotto.  
  
 `dwFlags`  
 [in] Flag di opzione associato l'interruzione. Può essere uno dei seguenti valori:  
  
|Value|Significato|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Se supportato, immettere il debugger del motore di script in corrispondenza del punto di esecuzione di script corrente.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Se supportati dal linguaggio del motore di script, consente allo script di gestire l'eccezione. Il metodo di script viene interrotta e il codice di errore viene restituito al chiamante; in caso contrario, vale a dire l'invoker di evento origine o una macro.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di scripting non è ancora caricato o inizializzato).|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)