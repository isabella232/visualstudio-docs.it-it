---
title: IActiveScript::GetCurrentScriptThreadID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: bac3b5755328e643c26c8f3746af6648d8ac06aa
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345799"
---
# <a name="iactivescriptgetcurrentscriptthreadid"></a>IActiveScript::GetCurrentScriptThreadID
Recupera un identificatore scripting-engine-definite per il thread attualmente in esecuzione. L'identificatore può essere utilizzato nelle chiamate successive ai metodi di controllo di esecuzione thread dello script, ad esempio la [IActiveScript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) (metodo).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstidThread`  
 [out] Indirizzo di una variabile che riceve l'identificatore del thread script associato al thread corrente. L'interpretazione di questo identificatore viene lasciata al motore di script, ma può essere solo una copia dell'identificatore di thread di Windows. Se il thread Win32 termina, questo identificatore diventa non assegnato e successivamente può essere assegnato a un altro thread.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` caso di esito positivo o `E_POINTER` se è stato specificato un puntatore non valido.  
  
## <a name="remarks"></a>Note  
 Questo metodo può essere chiamato dal thread non di base senza causando un callout non in base agli oggetti di host o al [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)