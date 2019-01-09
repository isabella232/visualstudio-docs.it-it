---
title: IDebugApplication::SynchronousCallInDebuggerThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b5c2a4d6c23339a396fbc367e68b81bb13c75adc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089947"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Fornisce un meccanismo per il chiamante deve eseguire il codice nel thread del debugger.  
  
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
 [in] Oggetto da chiamare.  
  
 `dwParam1`  
 [in] Primo parametro da passare al `IDebugThreadCall::ThreadCallHandler` (metodo).  
  
 `dwParam2`  
 [in] Secondo parametro da passare al `IDebugThreadCall::ThreadCallHandler` (metodo).  
  
 `dwParam3`  
 [in] Terzo parametro da passare al `IDebugThreadCall::ThreadCallHandler` (metodo).  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Gli host e motori di linguaggio usano in genere questo metodo per implementare gli oggetti a thread libero sopra le implementazioni a thread singole.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Interfaccia IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)