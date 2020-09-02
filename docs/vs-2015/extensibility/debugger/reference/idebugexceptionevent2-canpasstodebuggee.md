---
title: 'IDebugExceptionEvent2:: CanPassToDebuggee | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 383287a027a75adfb4c58020675e08a46198eacf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163802"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Determina se il motore di debug (DE) supporta l'opzione di passaggio di questa eccezione al programma di cui è in corso il debug al riavvio dell'esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` (l'eccezione può essere passata al programma) o `S_FALSE` (non è possibile passare l'eccezione).  
  
## <a name="remarks"></a>Osservazioni  
 Il DE deve avere un'azione predefinita per passare all'oggetto del debug. L'IDE può ricevere l'evento [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) e chiamare il metodo [continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) senza chiamare il `CanPassToDebuggee` metodo. Pertanto, il valore di DE deve avere un caso predefinito per il passaggio dell'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continua](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
