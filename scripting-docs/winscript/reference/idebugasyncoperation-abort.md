---
title: 'IDebugAsyncOperation:: Abort | Microsoft Docs'
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
ms.openlocfilehash: b9ca6c5e1498229c84dc28a13cda2cce77b58a4f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573304"
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
  
|Value|Descrizione|  
|-----------|-----------------|  
|S_OK|Il metodo è riuscito.|  
|E_NOTIMPL|Le operazioni non possono essere annullate.|  
  
## <a name="remarks"></a>Note  
 Questo metodo viene in genere chiamato dall'interno del thread del debugger per annullare un'operazione che non risponde. Questo metodo fa sì che il metodo `InProgressAbort` sull'oggetto `IDebugSyncOperation` venga chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)    
 @No__t_1 [IDebugAsyncOperation:: Start](../../winscript/reference/idebugasyncoperation-start.md)  
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)