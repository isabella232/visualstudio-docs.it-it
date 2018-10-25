---
title: IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ac6c84005530f72ef9ed0f252bf40b035c3034e8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881943"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Determina se il motore di debug (DE) supporta la possibilità di passare questa eccezione per il programma in fase di debug quando si riprende l'esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno `S_OK` (l'eccezione può essere passato al programma) o `S_FALSE` (l'eccezione non può essere passata).  
  
## <a name="remarks"></a>Note  
 La Germania deve avere un'azione predefinita per il passaggio per l'oggetto del debug. Potrebbe essere visualizzato l'IDE di [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) eventi e chiamate il [continua](../../../extensibility/debugger/reference/idebugprocess3-continue.md) metodo senza chiamare il `CanPassToDebuggee` (metodo). Pertanto, la Germania deve avere un case predefinito per passare l'eccezione o non.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)

