---
title: 'IActiveScript:: GetCurrentScriptThreadID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetCurrentScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetCurrentScriptThreadID
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dedb16e0c007ed05370fb54835f84f00784c1ae4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575770"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Recupera un identificatore definito dal motore di script per il thread attualmente in esecuzione. L'identificatore può essere usato nelle chiamate successive ai metodi di controllo dell'esecuzione del thread di script, ad esempio il metodo [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstidThread`  
 out Indirizzo di una variabile che riceve l'identificatore del thread di script associato al thread corrente. L'interpretazione di questo identificatore viene lasciata al motore di scripting, ma può trattarsi semplicemente di una copia dell'identificatore del thread di Windows. Se il thread Win32 termina, questo identificatore diventa non assegnato e può essere successivamente assegnato a un altro thread.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se ha esito positivo oppure `E_POINTER` se è stato specificato un puntatore non valido.  
  
## <a name="remarks"></a>Note  
 Questo metodo può essere chiamato da thread non di base senza comportare un callout non di base per ospitare oggetti o per l'interfaccia [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)