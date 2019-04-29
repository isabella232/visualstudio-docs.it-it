---
title: IDebugAsyncOperation::Start | Microsoft Docs
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
ms.openlocfilehash: b3e02869abab65878412f96b77d5782b9717a1b6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821928"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
Fa sì che l'operazione asincrona iniziare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `padocb`  
 L'interfaccia di callback che riceve gli eventi di stato da questa operazione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_UNEXPECTED`|Un'operazione è già in sospeso.|  
  
## <a name="remarks"></a>Note  
 Questo metodo determina `IDebugSyncOperation::Execute` alla chiamata asincrona nel thread ottenuto da `IDebugSyncOperation::GetTargetThread`. Questo metodo deve essere chiamato solo da all'interno del thread debugger; in caso contrario, non verrà restituito fino al completamento dell'operazione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [Interfaccia IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)