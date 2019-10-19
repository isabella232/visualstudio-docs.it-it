---
title: 'IActiveScript:: Clone | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fbaad29cb31af26a0f26a1c679a900192fc77041
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575790"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Clona il motore di scripting corrente (meno qualsiasi stato di esecuzione corrente), restituendo un motore di script caricato senza sito nel thread corrente. Le proprietà di questo nuovo motore di scripting saranno identiche a quelle del motore di script originale in se è stato eseguito il passaggio allo stato inizializzato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppscript`  
 out Indirizzo di una variabile che riceve un puntatore all'interfaccia [IActiveScript](../../winscript/reference/iactivescript.md) del motore di scripting clonato. L'host deve creare un sito e chiamare il metodo [IActiveScript:: SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) sul nuovo motore di scripting prima che si trovi nello stato Initialized e quindi utilizzabile.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_NOTIMPL`|Questo metodo non è supportato.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era prevista (ad esempio, il motore di scripting non è ancora stato caricato o inizializzato).|  
  
## <a name="remarks"></a>Note  
 Il metodo `IActiveScript::Clone` è un'ottimizzazione di `IPersist*::Save`, `CoCreateInstance` e `IPersist*::Load`, quindi lo stato del nuovo motore di scripting deve essere identico a quello in cui lo stato del motore di script originale veniva salvato e caricato in un nuovo motore di script. Gli elementi denominati vengono duplicati nel motore di script clonato, ma i puntatori a oggetti specifici per ogni elemento vengono dimenticati e vengono ottenuti con il metodo [IActiveScriptSite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) . In questo modo, è possibile usare un modello a oggetti identico con punti di ingresso per thread (un modello di Apartment).  
  
 Questo metodo viene utilizzato per gli host server multithreading in cui è possibile eseguire più istanze dello stesso script. Il motore di scripting può restituire `E_NOTIMPL`, nel qual caso l'host può ottenere lo stesso risultato duplicando lo stato persistente e creando una nuova istanza del motore di script con un'interfaccia `IPersist*`.  
  
 Questo metodo può essere chiamato da thread non di base senza comportare un callout non di base per ospitare oggetti o per l'interfaccia [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)