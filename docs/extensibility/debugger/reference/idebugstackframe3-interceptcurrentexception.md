---
title: IDebugStackFrame3::InterceptCurrentException . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7debd5323e753c6c5fd1476eac3c062fb63393b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719487"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Chiamato dal debugger sullo stack frame corrente quando desidera intercettare l'eccezione corrente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT InterceptCurrentException(
   INTERCEPT_EXCEPTION_ACTION dwFlags,
   UINT64*                    pqwCookie
);
```

```csharp
int InterceptCurrentException(
   uint dwFlags,
   out  ulong pqwCookie
);
```

## <a name="parameters"></a>Parametri
`dwFlags`\
[in] Specifica diverse azioni. Attualmente, solo [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) il `IEA_INTERCEPT` valore INTERCEPT_EXCEPTION_ACTION è supportato e deve essere specificato.

`pqwCookie`\
[fuori] Valore univoco che identifica una particolare eccezione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

 Di seguito sono riportati i ritorni di errore più comuni.

|Errore|Descrizione|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|L'eccezione corrente non può essere intercettata.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Il frame di esecuzione corrente non è stato ancora cercato un gestore.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Questo metodo non è supportato per questo frame.|

## <a name="remarks"></a>Osservazioni
 Quando viene generata un'eccezione, il debugger ottiene il controllo dalla fase di esecuzione in punti chiave durante il processo di gestione delle eccezioni. Durante questi momenti chiave, il debugger può chiedere lo stack frame corrente se il frame desidera intercettare l'eccezione. In questo modo, un'eccezione intercettata è essenzialmente un gestore di eccezioni in tempo reale per uno stack frame, anche se tale stack frame non dispone di un gestore di eccezioni (ad esempio, un blocco try/catch nel codice del programma).

 Quando il debugger desidera sapere se l'eccezione deve essere intercettata, chiama questo metodo sull'oggetto stack frame corrente. Questo metodo è responsabile della gestione di tutti i dettagli dell'eccezione. Se il [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) interfaccia non `InterceptStackException` è implementata o il metodo restituisce alcun errore, quindi il debugger continua l'elaborazione dell'eccezione normalmente.

> [!NOTE]
> Le eccezioni possono essere intercettate solo nel codice gestito, ovvero quando il programma in fase di debug è in esecuzione in fase di esecuzione di .NET. Naturalmente, gli implementatori di linguaggio di terze parti possono implementare `InterceptStackException` nei propri motori di debug, se lo desiderano.

 Al termine dell'intercettazione, viene segnalato un [oggetto IDebugInterceptExceptionCompleteEvent2.After](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) the interception is complete, an IDebugInterceptExceptionCompleteEvent2 is signaled.

## <a name="see-also"></a>Vedere anche
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
