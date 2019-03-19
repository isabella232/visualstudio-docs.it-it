---
title: IActiveScriptProfilerCallback::OnFunctionEnter | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.OnFunctionEnter
apilocation:
- scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b8410fba08c1799d88532266c022d811c9553fd
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158240"
---
# <a name="iactivescriptprofilercallbackonfunctionenter"></a>IActiveScriptProfilerCallback::OnFunctionEnter
Indica all'oggetto di profiler che il motore di scripting sta per essere eseguita una chiamata di funzione che non è una chiamata nel modello DOM (Document Object).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT OnFunctionEnter(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### <a name="parameters"></a>Parametri  
 `scriptId`  
 [in] ID univoco dello script che fa parte della funzione. Questo ID viene assegnato dal motore di script.  
  
 `functionId`  
 [in] ID univoco della funzione. Questo ID viene assegnato dal motore di script.  
  
## <a name="return-value"></a>Valore restituito  
 Il valore restituito di questo metodo viene ignorato dal motore di script.  
  
## <a name="remarks"></a>Note  
 Per le chiamate di DOM, chiama il motore di scripting [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) invece di `IActiveScriptProfilerCallback::OnFunctionEnter`. Si tratta causa dell'elevato numero di metodi univoci e proprietà nel DOM.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [Interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)