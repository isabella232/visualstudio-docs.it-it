---
title: 'IDebugApplication:: SynchronousCallInDebuggerThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.SynchronousCallInDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::SynchronousCallInDebuggerThread
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 134717b6ce30c87ccfb4bbb50ffe958717ae757f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574592"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Fornisce un meccanismo che consente al chiamante di eseguire codice nel thread del debugger.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pptc`  
 in Oggetto da chiamare.  
  
 `dwParam1`  
 in Primo parametro da passare al metodo `IDebugThreadCall::ThreadCallHandler`.  
  
 `dwParam2`  
 in Secondo parametro da passare al metodo `IDebugThreadCall::ThreadCallHandler`.  
  
 `dwParam3`  
 in Terzo parametro da passare al metodo `IDebugThreadCall::ThreadCallHandler`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 I motori di linguaggio e gli host utilizzano in genere questo metodo per implementare oggetti a thread libero sulle rispettive implementazioni a thread singolo.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Interfaccia IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)