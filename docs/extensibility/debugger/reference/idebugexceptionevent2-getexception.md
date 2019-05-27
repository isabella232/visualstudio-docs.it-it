---
title: IDebugExceptionEvent2::GetException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa6f4646894607823608b911c7a4e1df787fc05d
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66201132"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Ottiene una descrizione dettagliata dell'eccezione che ha generato questo evento.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetException( 
   EXCEPTION_INFO* pExceptionInfo
);
```

```csharp
int GetException( 
   EXCEPTION_INFO[] pExceptionInfo
);
```

## <a name="parameters"></a>Parametri
`pExceptionInfo`\
[in, out] Un' [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struttura compilata con la descrizione dell'eccezione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note

 [C++ solo] Il chiamante è responsabile della liberazione tutte le stringhe nel [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struttura, nonché di rilasciare la [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto nella struttura.

## <a name="see-also"></a>Vedere anche
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)