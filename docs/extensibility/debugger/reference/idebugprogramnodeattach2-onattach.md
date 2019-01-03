---
title: IDebugProgramNodeAttach2::OnAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8ff183f60733ec125ba4635e154a589318500fdb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53924566"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Collega al programma associato oppure rinvia il processo di collegamento per il [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) (metodo).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```csharp  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### <a name="parameters"></a>Parametri  
 `guidProgramId`  
 [in] `GUID` da assegnare al programma associato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se il [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodo non deve essere chiamato. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato durante il processo di collegamento, in precedenza il [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) viene chiamato il metodo. Il `OnAttach` metodo può eseguire il processo di collegamento (in questo caso, questo metodo restituisce `S_FALSE`) o posticipare il processo di collegamento per il `IDebugEngine2::Attach` metodo (il `OnAttach` restituzione del metodo `S_OK`). In entrambi i casi il `OnAttach` metodo può impostare il `GUID` del programma in fase di debug per il dato `GUID`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)