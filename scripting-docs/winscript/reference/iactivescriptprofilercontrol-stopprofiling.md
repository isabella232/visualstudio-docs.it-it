---
title: IActiveScriptProfilerControl::StopProfiling | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StopProfiling
apilocation:
- scrobj.dll
ms.assetid: 23b46ed6-a398-44c0-bc49-bf122e697cfe
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 750693db9aa809e6b3521f0312cebcf45d8d720d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157711"
---
# <a name="iactivescriptprofilercontrolstopprofiling"></a>IActiveScriptProfilerControl::StopProfiling
Arresta la profilatura sul motore di scripting. Questo metodo chiama [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) sull'oggetto del profiler e lo rilascia.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT StopProfiling(  
    [in] HRESULT hrShutdownReason);  
```  
  
#### <a name="parameters"></a>Parametri  
 `hrShutdownReason`  
 [in] Il valore HRESULT deve essere passato come parametro per il [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) metodo dell'oggetto del profiler.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un HRESULT. I valori possibili sono i seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Il metodo è riuscito.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilatura non è abilitata.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)