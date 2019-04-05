---
title: IDebugExceptionEvent2::GetException | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a0e19dc924101fcceb93948272fc1e83353e2815
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966752"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene una descrizione dettagliata dell'eccezione che ha generato questo evento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetException(   
   EXCEPTION_INFO* pExceptionInfo  
);  
```  
  
```csharp  
int GetException(   
   EXCEPTION_INFO[] pExceptionInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pExceptionInfo`  
 [in, out] Un' [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struttura compilata con la descrizione dell'eccezione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 [Solo C++] Il chiamante è responsabile della liberazione tutte le stringhe nel [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struttura, nonché di rilasciare la [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto nella struttura.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
