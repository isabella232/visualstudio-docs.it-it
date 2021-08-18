---
description: Chiamato dal debugger sul stack frame quando vuole intercettare l'eccezione corrente.
title: IDebugStackFrame3::InterceptCurrentException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6604c4a47e44df05d02b3b6c24c9efe12eeac0f2478ff28037e9bdb3c2a2e18a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338436"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Chiamato dal debugger sul stack frame quando vuole intercettare l'eccezione corrente.

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
[in] Specifica azioni diverse. Attualmente, solo il [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) è `IEA_INTERCEPT` supportato e deve essere specificato.

`pqwCookie`\
[out] Valore univoco che identifica una particolare eccezione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

 Di seguito sono riportati gli errori restituiti più comuni.

|Errore|Descrizione|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|L'eccezione corrente non può essere intercettata.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Il frame di esecuzione corrente non è ancora stato cercato per un gestore.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Questo metodo non è supportato per questo frame.|

## <a name="remarks"></a>Commenti
 Quando viene generata un'eccezione, il debugger ottiene il controllo dal tempo di esecuzione nei punti chiave durante il processo di gestione delle eccezioni. Durante questi momenti chiave, il debugger può chiedere al stack frame se il frame vuole intercettare l'eccezione. In questo modo, un'eccezione intercettata è essenzialmente un gestore di eccezioni in tempo reale per un stack frame, anche se tale stack frame non ha un gestore di eccezioni (ad esempio, un blocco try/catch nel codice del programma).

 Quando il debugger vuole sapere se l'eccezione deve essere intercettata, chiama questo metodo sull'oggetto stack frame corrente. Questo metodo è responsabile della gestione di tutti i dettagli dell'eccezione. Se [l'interfaccia IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) non è implementata o il metodo restituisce un errore, il debugger continua a elaborare normalmente `InterceptStackException` l'eccezione.

> [!NOTE]
> Le eccezioni possono essere intercettate solo nel codice gestito, ad esempio quando il programma in fase di debug è in esecuzione in fase di esecuzione .NET. Naturalmente, gli implementatori di linguaggi di terze parti possono implementare nei propri `InterceptStackException` motori di debug, se lo desiderano.

 Al termine dell'intercettazione, viene segnalato [un oggetto IDebugInterceptExceptionCompleteEvent2.](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)

## <a name="see-also"></a>Vedi anche
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
