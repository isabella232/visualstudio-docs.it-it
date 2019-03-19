---
title: IDebugSyncOperation::InProgressAbort | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.InProgressAbort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a794ea70d6d2fe937afb311e6961d53f22bd7ac2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159725"
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
Annulla un'operazione in corso in un altro thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|L'operazione non può essere annullata.|  
|`E_ABORT`|Non è stato possibile completare l'operazione.|  
  
## <a name="remarks"></a>Note  
 Il gestore di eseguire il Debug di processi chiama questo metodo dall'interno del thread debugger per annullare un'operazione che è in corso in un altro thread.  
  
 Se il `InProgressAbort` metodo non è possibile completare l'operazione, viene restituito `E_ABORT` appena possibile. Questo metodo può restituire `E_NOTIMPL` se l'operazione non può essere annullata.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)