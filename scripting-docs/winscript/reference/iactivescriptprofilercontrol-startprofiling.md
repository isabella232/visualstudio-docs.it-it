---
title: 'IActiveScriptProfilerControl:: StartProfiling | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StartProfiling
apilocation:
- scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b37b60f50351496faceb97190ae0d173eba3a5f4
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983266"
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
Avvia la profilatura sul motore di scripting. Il motore di scripting crea un'istanza dell'oggetto Profiler effettuando una chiamata a [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parametri  
 `clsidProfilerObject`  
 in Identificatore di classe (CLSID) dell'oggetto Profiler da creare.  
  
 `dwEventMask`  
 in Maschera di bit a 4 byte che specifica i tipi di eventi. I bit sono definiti nell' [enumerazione PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
 `dwContext`  
 in Valore a 4 byte passato all'oggetto Profiler.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un valore HRESULT. I valori possibili sono i seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Il metodo è riuscito.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|La profilatura è già abilitata.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)