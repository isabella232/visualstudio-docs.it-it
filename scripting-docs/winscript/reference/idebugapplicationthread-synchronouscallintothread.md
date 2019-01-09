---
title: IDebugApplicationThread::SynchronousCallIntoThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.SynchronousCallIntoThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::SynchronousCallIntoThread
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5e25f42b2bce66cf3bb7ab3e69d3711e2526ae1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097058"
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Fornisce un meccanismo per il chiamante può eseguire codice nel thread dell'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstcb`  
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
 Questo metodo fornisce un meccanismo per il chiamante deve eseguire il codice nel thread del debugger. Gli host e motori di linguaggio usano in genere questo metodo per implementare gli oggetti a thread libero sopra le implementazioni a thread singole.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)   
 [Interfaccia IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md)