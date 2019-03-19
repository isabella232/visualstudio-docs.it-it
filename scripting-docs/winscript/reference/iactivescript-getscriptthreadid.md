---
title: IActiveScript::GetScriptThreadID | Microsoft Docs
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
ms.openlocfilehash: d329e08e6a17d9edcdf26e14b468c3c56f036c00
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154400"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Recupera un identificatore scripting-engine-definite per il thread associato al thread Win32 specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwWin32ThreadID` ,  
 [in] Identificatore del thread di un thread Win32 in esecuzione nel processo corrente. Usare la [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) funzione per recuperare l'identificatore del thread del thread attualmente in esecuzione.  
  
 `pstidThread` ,  
 [out] Indirizzo di una variabile che riceve l'identificatore del thread script associato al thread Win32 specificato. L'interpretazione di questo identificatore viene lasciata al motore di script, ma può essere solo una copia dell'identificatore di thread di Windows. Si noti che se il thread Win32 termina, questo identificatore diventerà non assegnato e successivamente può essere assegnato a un altro thread.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di scripting non è ancora caricato o inizializzato) e pertanto non è riuscita.|  
  
## <a name="remarks"></a>Note  
 L'identificatore recuperato può essere utilizzato nelle successive chiamate a metodi di controllo di esecuzione thread dello script, ad esempio la [IActiveScript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) (metodo).  
  
 Questo metodo può essere chiamato dal thread non di base senza causando un callout non in base agli oggetti di host o al [IActiveScript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)