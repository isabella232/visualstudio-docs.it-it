---
title: 'IActiveScript:: GetScriptThreadID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a0fb1eebfcb6ed100056289fab6bce662f86a7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575711"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Recupera un identificatore definito dal motore di script per il thread associato al thread Win32 specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwWin32ThreadID` ,  
 in Identificatore del thread di un thread Win32 in esecuzione nel processo corrente. Usare la funzione [IActiveScript:: GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) per recuperare l'identificatore del thread attualmente in esecuzione.  
  
 `pstidThread` ,  
 out Indirizzo di una variabile che riceve l'identificatore del thread di script associato al thread Win32 specificato. L'interpretazione di questo identificatore viene lasciata al motore di scripting, ma può trattarsi semplicemente di una copia dell'identificatore del thread di Windows. Si noti che se il thread Win32 termina, questo identificatore diventa non assegnato e potrebbe essere successivamente assegnato a un altro thread.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era prevista (ad esempio, il motore di scripting non è ancora stato caricato o inizializzato) e pertanto non è riuscito.|  
  
## <a name="remarks"></a>Note  
 L'identificatore recuperato può essere usato nelle chiamate successive ai metodi di controllo dell'esecuzione del thread di script, ad esempio il metodo [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
 Questo metodo può essere chiamato da thread non di base senza comportare un callout non di base per ospitare oggetti o nell'interfaccia [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)