---
title: IRemoteDebugApplicationThread::SetNextStatement | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.SetNextStatement
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::SetNextStatement
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c4b19322a15e92adcf2609c479af6b21e2078bd
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145174"
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
Forza continuare l'esecuzione più vicino possibile al contesto di codice specificato, nel contesto del frame specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pStackFrame`  
 [in] L'oggetto stack frame. Questo argomento può essere NULL, il che implica che lo stack frame corrente deve essere utilizzato.  
  
 `pCodeContext`  
 [in] Il contesto del codice. Questo argomento può essere NULL, il che implica che il contesto codice corrente deve essere utilizzato.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo forza l'esecuzione più vicino possibile al contesto di codice specificato dal continuare `pCodeContext`, nel contesto del frame specificato da `pStackFrame`. Uno di questi argomenti può essere `NULL`, che rappresenta il contesto o il frame corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)