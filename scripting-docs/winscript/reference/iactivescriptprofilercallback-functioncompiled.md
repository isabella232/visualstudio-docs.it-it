---
title: 'IActiveScriptProfilerCallback:: FunctionCompiled | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.FunctionCompiled
apilocation:
- scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a17ce7548a6524df6911cdf952393020472b88ed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576466"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Notifica all'oggetto profiler che il motore di script ha rilevato una funzione durante la compilazione di uno script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Parametri  
 `functionId`  
 in ID univoco della funzione. Questo ID viene assegnato dal motore di scripting.  
  
 `scriptId`  
 in ID univoco dello script di cui fa parte la funzione.  
  
 `pwszFunctionName`  
 in Nome della funzione o null per una funzione anonima.  
  
 `pwszFunctionNameHint`  
 in Nome dedotto della funzione o null se il motore di script non deduce alcun nome.  
  
 `pIDebugDocumentContext`  
 in Se disponibile, il puntatore a un'interfaccia `IUnknown` cui il profiler deve eseguire una query per un puntatore di [interfaccia IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md) . In caso contrario, Null.  
  
## <a name="return-value"></a>Valore restituito  
 Il valore restituito di questo metodo viene ignorato dal motore di scripting.  
  
## <a name="remarks"></a>Note  
 Il motore di scripting può fornire il contesto del documento solo se è supportato dall'host.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)