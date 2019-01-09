---
title: IActiveScriptSite::OnScriptTerminate | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: f8ff7c3d531b46fa6681776e79fbb73f6d1efca2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087113"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Comunica all'host che lo script è stata completata l'esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pvarResult`  
 [in] Indirizzo di una variabile che contiene il risultato dello script, o `NULL` se lo script ha prodotto alcun risultato.  
  
 `pexcepinfo`  
 [in] Indirizzo di un `EXCEPINFO` struttura che contiene le informazioni sull'eccezione generate quando lo script è terminata, o `NULL` se è stata generata alcuna eccezione.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`.  
  
## <a name="remarks"></a>Note  
 Il motore di script chiama questo metodo prima della chiamata ai [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) metodo, con il set di flag SCRIPTSTATE_INITIALIZED, viene completata. Questo metodo può essere utilizzato per restituire lo stato di completamento e i risultati per l'host. Si noti che molti linguaggi di script, che si basano sugli eventi di sink dall'host, vita intervalli definiti dall'host. In questo caso, questo metodo non può mai essere chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)