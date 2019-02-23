---
title: IDebugExceptionEvent2::PassToDebuggee | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cae097b5ce02993fc125aafaffded32a35dde0a5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679359"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Specifica se l'eccezione deve essere passata per il programma in fase di debug quando si riprende l'esecuzione o se l'eccezione deve essere eliminato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT PassToDebuggee(
   BOOL fPass
);
```

```csharp
int PassToDebuggee(
   int fPass
);
```

#### <a name="parameters"></a>Parametri
 `fPass`

 [in] Diverso da zero (`TRUE`) se l'eccezione deve essere passata programma sottoposto a debug quando si riprende l'esecuzione, oppure zero (`FALSE`) se l'eccezione deve essere eliminato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Chiamare questo metodo non determina effettivamente qualsiasi codice da eseguire nel programma sottoposto a debug. La chiamata è semplicemente impostare lo stato per l'esecuzione di codice successiva. Ad esempio, le chiamate al [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) metodo può restituire `S_OK` con il [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` campo impostato su `EXCEPTION_STOP_SECOND_CHANCE`.

 Potrebbe essere visualizzato l'IDE di [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) eventi e chiamate di [continua](../../../extensibility/debugger/reference/idebugprogram2-continue.md) (metodo). Il motore di debug (DE) deve avere un comportamento predefinito per gestire il caso se il `PassToDebuggee` non viene chiamato.

## <a name="see-also"></a>Vedere anche
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)