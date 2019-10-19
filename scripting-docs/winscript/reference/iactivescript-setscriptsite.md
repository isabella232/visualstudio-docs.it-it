---
title: 'IActiveScript:: SetScriptSite | Microsoft Docs'
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
ms.openlocfilehash: 063dcc7b580334bff9780e9c209b621ef7e25656
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575322"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Informa il motore di scripting del sito dell'interfaccia [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) fornito dall'host. Chiamare questo metodo prima di utilizzare altri metodi di interfaccia [IActiveScript](../../winscript/reference/iactivescript.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pScriptSite`  
 in Indirizzo del sito di script fornito dall'host da associare a questa istanza del motore di scripting. Il sito deve essere assegnato in modo univoco a questa istanza del motore di script; non può essere condiviso con altri motori di scripting.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_FAIL`|Si è verificato un errore non specificato. il motore di scripting non è stato in grado di completare l'inizializzazione del sito.|  
|`E_INVALIDARG`|Argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era prevista (ad esempio, un sito era già impostato).|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)