---
title: IDebugSyncOperation::Execute | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.Execute
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::Execute
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2bc204169ff94a240e363eb8caa35ec8c7de9be
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146357"
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
In modo sincrono esegue l'operazione e restituisce.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppunkResult`  
 [out] Il parametro dell'oggetto restituito dall'operazione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_ABORT`|L'operazione è stata interrotta chiamando il `IDebugSyncOperation::InProgressAbort` (metodo).|  
  
## <a name="remarks"></a>Note  
 Il gestore di eseguire il Debug di processi nelle chiamate di thread di destinazione di `Execute` metodo in modo sincrono.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)