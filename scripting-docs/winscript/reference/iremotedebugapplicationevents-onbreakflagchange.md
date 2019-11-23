---
title: 'IRemoteDebugApplicationEvents:: OnBreakFlagChange | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnBreakFlagChange
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnBreakFlagChange
ms.assetid: 25684454-a0d8-47e0-85f5-2217069a9f45
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71e9a29b6dcc5cd6864ce4edffe9e5f96b64ba9e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561715"
---
# <a name="iremotedebugapplicationeventsonbreakflagchange"></a>IRemoteDebugApplicationEvents::OnBreakFlagChange
Gestisce un evento quando i flag di interruzioni cambiano.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT OnBreakFlagChange(  
   APPBREAKFLAGS                   abf,  
   IRemoteDebugApplicationThread*  prdatSteppingThread  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `abf`  
 in Flag di interruzioni correnti per l'applicazione.  
  
 `prdatSteppingThread`  
 in Thread attualmente in esecuzione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo gestisce l'evento quando cambia il flag di interruzioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)   
 [Enumerazione APPBREAKFLAGS](../../winscript/reference/appbreakflags-enumeration.md)