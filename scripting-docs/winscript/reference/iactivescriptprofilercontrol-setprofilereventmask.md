---
title: IActiveScriptProfilerControl::SetProfilerEventMask | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.SetProfilerEventMask
apilocation:
- scrobj.dll
ms.assetid: 207e192f-e12e-4fcb-b4d8-eaee50ecb86e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45ded6caec95f5421328be09e299af535765a9c2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086788"
---
# <a name="iactivescriptprofilercontrolsetprofilereventmask"></a>IActiveScriptProfilerControl::SetProfilerEventMask
Imposta una maschera di bit a 4 byte che specifica i tipi di eventi che il motore di scripting deve generare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwEventMask`  
 [in] Maschera di bit a 4 byte che specifica i tipi di eventi. I bit sono definiti in [enumerazione PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un HRESULT. I valori possibili sono i seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Il metodo è riuscito.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilatura non è abilitata.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)