---
title: 'IDebugAsyncOperation:: Start | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Start
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Start
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 485eb34ebe200e7f7898d9338effed37cbf2aa10
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573253"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
Determina l'inizio dell'operazione asincrona.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `padocb`  
 Interfaccia di callback che riceve gli eventi di stato da questa operazione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_UNEXPECTED`|Un'operazione è già in sospeso.|  
  
## <a name="remarks"></a>Note  
 Questo metodo fa sì che `IDebugSyncOperation::Execute` venga chiamato in modo asincrono nel thread ottenuto da `IDebugSyncOperation::GetTargetThread`. Questo metodo deve essere chiamato solo dall'interno del thread del debugger. in caso contrario, non verrà restituito fino al completamento dell'operazione.  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 [IDebugAsyncOperation:: Abort](../../winscript/reference/idebugasyncoperation-abort.md)  
 [Interfaccia IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)    
 @No__t_1 [IDebugSyncOperation:: Execute](../../winscript/reference/idebugsyncoperation-execute.md)  
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)