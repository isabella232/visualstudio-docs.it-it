---
description: Chiamato dal debugger sul stack frame corrente quando vuole intercettare l'eccezione corrente.
title: 'IDebugStackFrame3:: InterceptCurrentException | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93fa7f73b3e13c655716ecbb16ff420605f76c90
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145781"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Chiamato dal debugger sul stack frame corrente quando vuole intercettare l'eccezione corrente.

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
in Specifica azioni diverse. Attualmente, è supportato solo il valore [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) `IEA_INTERCEPT` e deve essere specificato.

`pqwCookie`\
out Valore univoco che identifica una particolare eccezione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

 Di seguito sono riportati i ritorni degli errori più comuni.

|Errore|Descrizione|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Impossibile intercettare l'eccezione corrente.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Il frame di esecuzione corrente non è ancora stato cercato per un gestore.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Questo metodo non è supportato per questo frame.|

## <a name="remarks"></a>Commenti
 Quando viene generata un'eccezione, il debugger acquisisce il controllo dal runtime in corrispondenza dei punti chiave durante il processo di gestione delle eccezioni. Durante questi istanti, il debugger può richiedere la stack frame corrente se il frame vuole intercettare l'eccezione. In questo modo, un'eccezione intercettata è essenzialmente un gestore di eccezioni immediato per un stack frame, anche se tale stack frame non dispone di un gestore di eccezioni (ad esempio, un blocco try/catch nel codice del programma).

 Quando il debugger desidera conoscere se l'eccezione deve essere intercettata, chiama questo metodo sull'oggetto stack frame corrente. Questo metodo è responsabile della gestione di tutti i dettagli dell'eccezione. Se l'interfaccia [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) non è implementata o il `InterceptStackException` metodo restituisce un errore, il debugger continua a elaborare l'eccezione normalmente.

> [!NOTE]
> Le eccezioni possono essere intercettate solo nel codice gestito, ovvero quando il programma di cui è in corso il debug è in esecuzione in fase di esecuzione in .NET. Naturalmente, gli implementatori del linguaggio di terze parti possono implementare `InterceptStackException` nei propri motori di debug, se lo scelgono.

 Una volta completata l'intercettazione, viene segnalato un [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
