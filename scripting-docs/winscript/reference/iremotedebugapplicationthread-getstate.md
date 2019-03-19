---
title: IRemoteDebugApplicationThread::GetState | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetState
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetState
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6534f57c92776dcd3cde9083335becbd66002a32
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152993"
---
# <a name="iremotedebugapplicationthreadgetstate"></a>IRemoteDebugApplicationThread::GetState
Ottiene lo stato di questo thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pState`  
 [out] Combinazione dei flag di stato thread seguenti:  
  
|Costante|Value|Descrizione|  
|--------------|-----------|-----------------|  
|THREAD_STATE_RUNNING|0x00000001|Il thread è in esecuzione.|  
|THREAD_STATE_SUSPENDED|0x00000002|Il thread viene sospeso.|  
|THREAD_BLOCKED|0x00000004|Il thread è bloccato.|  
|THREAD_OUT_OF_CONTEXT|0x00000008|Il thread non rientra contenuto.|  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo ottiene lo stato di questo thread.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)