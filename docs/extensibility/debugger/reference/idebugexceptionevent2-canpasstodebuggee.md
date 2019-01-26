---
title: IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ccf980fb3d5b357b6211674ca8b99132d81fae1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041009"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Determina se il motore di debug (DE) supporta la possibilità di passare questa eccezione per il programma in fase di debug quando si riprende l'esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno `S_OK` (l'eccezione può essere passato al programma) o `S_FALSE` (l'eccezione non può essere passata).  
  
## <a name="remarks"></a>Note  
 La Germania deve avere un'azione predefinita per il passaggio per l'oggetto del debug. Potrebbe essere visualizzato l'IDE di [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) eventi e chiamate il [continua](../../../extensibility/debugger/reference/idebugprocess3-continue.md) metodo senza chiamare il `CanPassToDebuggee` (metodo). Pertanto, la Germania deve avere un case predefinito per passare l'eccezione o non.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)