---
title: IActiveScriptProfilerCallback::FunctionCompiled | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4bd032914605c61b13a0a56a42e510c2af252f7e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091403"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Notifica al profiler che la creazione di script del motore ha rilevato una funzione quando la compilazione di uno script.  
  
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
 [in] ID univoco della funzione. Questo ID viene assegnato dal motore di script.  
  
 `scriptId`  
 [in] ID univoco dello script che fa parte della funzione.  
  
 `pwszFunctionName`  
 [in] Il nome della funzione, o null per una funzione anonima.  
  
 `pwszFunctionNameHint`  
 [in] Nome della funzione, o null se il motore di scripting non deduce qualsiasi nome dedotto.  
  
 `pIDebugDocumentContext`  
 [in] Se disponibile, il puntatore a un `IUnknown` interfaccia che il profiler deve eseguire una query per un [interfaccia IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md) puntatore. In caso contrario, Null.  
  
## <a name="return-value"></a>Valore restituito  
 Il valore restituito di questo metodo viene ignorato dal motore di script.  
  
## <a name="remarks"></a>Note  
 Il motore di scripting può offrire il contesto del documento solo se supportato dall'host.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)