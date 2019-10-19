---
title: 'IActiveScriptSite:: OnScriptTerminate | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptTerminate
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a715b39b07df4183d4ec542a1dd82b4229d1f41e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570211"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Informa l'host che l'esecuzione dello script è stata completata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pvarResult`  
 in Indirizzo di una variabile che contiene il risultato dello script o `NULL` se lo script non ha prodotto alcun risultato.  
  
 `pexcepinfo`  
 in Indirizzo di una struttura di `EXCEPINFO` contenente le informazioni sulle eccezioni generate al termine dello script oppure `NULL` se non è stata generata alcuna eccezione.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`.  
  
## <a name="remarks"></a>Note  
 Il motore di scripting chiama questo metodo prima della chiamata al metodo [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) , con il flag SCRIPTSTATE_INITIALIZED impostato, viene completato. Questo metodo può essere utilizzato per restituire lo stato di completamento e i risultati all'host. Si noti che molti linguaggi di script, basati su eventi di sink dall'host, hanno intervalli di vita definiti dall'host. In questo caso, questo metodo non può mai essere chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)