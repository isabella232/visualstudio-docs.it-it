---
title: IDebugAsyncOperation::Abort | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Abort
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Abort
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be696f852f7038316141415494920c43580738c9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155446"
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
Annulla un'operazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|S_OK|Il metodo è riuscito.|  
|E_NOTIMPL|Le operazioni non possono essere annullate.|  
  
## <a name="remarks"></a>Note  
 In genere, questo metodo viene chiamato dall'interno del thread debugger per annullare un'operazione che non risponda. Questo metodo fa sì che il `InProgressAbort` metodo su di `IDebugSyncOperation` oggetto da chiamare.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)