---
title: 'IDebugExceptionEvent2:: GetException | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 332cbb28bd175aa5c3b4187ae735a479ba9de6b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729856"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Ottiene una descrizione dettagliata dell'eccezione che ha generato l'evento.

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
[in, out] Struttura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) compilata con la descrizione dell'eccezione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni

 [Solo C++] Il chiamante è responsabile di liberare tutte le stringhe nella struttura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) e di rilasciare l'oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nella struttura.

## <a name="see-also"></a>Vedere anche
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
