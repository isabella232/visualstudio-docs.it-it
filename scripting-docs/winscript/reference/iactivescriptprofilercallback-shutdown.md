---
title: 'IActiveScriptProfilerCallback:: Shutdown | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Shutdown
apilocation:
- scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: deecfe4134a4b0e18591823f194ceaf6d1eb0a14
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571654"
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Chiamato per informare l'oggetto profiler ogni volta che viene arrestata la profilatura in un motore di script. In questo modo, l'oggetto profiler può chiamare le routine di pulitura, se necessario. Questo metodo viene chiamato anche dal motore di script quando il motore di scripting viene arrestato o quando una chiamata a [IActiveScriptProfilerCallback:: Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) ha esito negativo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Parametri  
 `hrReason`  
 in Motivo dell'arresto. Se il motore di scripting viene arrestato, `S_OK` viene passato. Se la chiamata a [IActiveScriptProfilerCallback:: Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) restituisce un errore HRESULT, viene passato HRESULT. In caso contrario, questo valore viene recuperato da [IActiveScriptProfilerControl:: StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## <a name="return-value"></a>Valore restituito  
 Il valore restituito di questo metodo viene ignorato dal motore di scripting.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)