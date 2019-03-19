---
title: 'IActiveScript:: Setscriptsite | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptSite
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3fdf5f3ae84d1a991d67170b5f2b02114b91ee05
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157068"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Segnala al motore di scripting di [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) sito interfaccia fornita dall'host. Chiamare questo metodo prima di qualsiasi altro [IActiveScript](../../winscript/reference/iactivescript.md) viene usato metodi di interfaccia.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pScriptSite`  
 [in] Indirizzo del sito script fornito dall'host da associare a questa istanza del motore di scripting. Il sito deve essere assegnato in modo univoco a questa istanza del motore di scripting; non può essere condiviso con altri motori di script.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_FAIL`|Si è verificato un errore non specificato; il motore di scripting non è riuscito a completare l'inizializzazione del sito.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, un sito è stato già impostato).|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)