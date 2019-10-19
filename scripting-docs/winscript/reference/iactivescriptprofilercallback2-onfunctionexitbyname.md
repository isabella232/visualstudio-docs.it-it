---
title: 'IActiveScriptProfilerCallback2:: OnFunctionExitByName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionExitByName
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a70bc72dd1070759ad8b78e43926f06a2c56ec15
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571627"
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
Notifica all'oggetto profiler che il motore di script ha terminato l'esecuzione di una chiamata di funzione Document Object Model (DOM).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>Parametri  
 `pwszFunctionName`  
 in Nome della funzione completata dall'esecuzione del motore di script.  
  
 `scriptType`  
 in Tipo della funzione. Per le descrizioni dei valori validi, vedere [enumerazione PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## <a name="return-value"></a>Valore restituito  
 Il valore restituito di questo metodo viene ignorato dal motore di scripting.  
  
## <a name="remarks"></a>Note  
 Per le chiamate DOM, il motore di script chiama questo metodo anziché chiamare [IActiveScriptProfilerCallback:: OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md). Questo è dovuto all'elevato numero di proprietà e metodi univoci nel DOM.  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 [IActiveScriptProfilerCallback2:: OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)  
 [Interfaccia IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)