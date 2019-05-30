---
title: IDebugStackFrame3::InterceptCurrentException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ffc50f9884d40083d9696869c0e1b34284e4a794
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352053"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Chiamato dal debugger sul frame dello stack corrente quando desidera intercettare l'eccezione corrente.

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
[in] Specifica le azioni diverse. Attualmente, solo il [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) valore `IEA_INTERCEPT` è supportata e deve essere specificato.

`pqwCookie`\
[out] Valore univoco che identifica una particolare eccezione.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

 Di seguito sono la restituzione di errori più comuni.

|Error|Descrizione|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Non è possibile intercettare l'eccezione corrente.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Il frame di esecuzione corrente non è stato cercato un gestore ancora.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Questo metodo non è supportato per questo frame.|

## <a name="remarks"></a>Note
 Quando viene generata un'eccezione, il debugger ottiene il controllo dal runtime momenti durante il processo di gestione delle eccezioni. Durante queste chiavi istante, il debugger può chiedere lo stack frame corrente se il frame vuole intercettare l'eccezione. In questo modo, un'eccezione intercettata è essenzialmente un gestore di eccezioni in tempo reale per uno stack frame, anche se quel frame dello stack non contiene un gestore di eccezioni (ad esempio, un blocco try/catch nel codice del programma).

 Quando il debugger vuole sapere se è necessario intercettare l'eccezione, viene chiamato questo metodo sull'oggetto stack frame corrente. Questo metodo è responsabile per la gestione di tutti i dettagli dell'eccezione. Se il [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) interfaccia non è implementata o `InterceptStackException` metodo restituisce qualsiasi errore, quindi il debugger continua l'elaborazione normale in corso l'eccezione.

> [!NOTE]
> Le eccezioni possono essere intercettate solo nel codice gestito, vale a dire, quando il programma sottoposto a debug è in esecuzione con il runtime .NET. Naturalmente, è possono implementare gli implementatori del linguaggio di terze parti `InterceptStackException` nei propri motori di debug, se necessario.

 Al termine l'intercettazione, un' [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) viene segnalato.

## <a name="see-also"></a>Vedere anche
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)