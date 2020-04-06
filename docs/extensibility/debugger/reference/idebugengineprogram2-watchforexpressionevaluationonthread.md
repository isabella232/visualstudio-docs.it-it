---
title: Proprietà IDebugEngineProgram2::WatchForExpressionEvaluationOnThread . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e988e1d64af38a55f5d946f704e1edb4df29b1d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730371"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Consente (o non consente) la valutazione dell'espressione sul thread specificato, anche se il programma è stato arrestato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WatchForExpressionEvaluationOnThread( 
   IDebugProgram2*       pOriginatingProgram,
   DWORD                 dwTid,
   DWORD                 dwEvalFlags,
   IDebugEventCallback2* pExprCallback,
   BOOL                  fWatch
);
```

```csharp
int WatchForExpressionEvaluationOnThread( 
   IDebugProgram2       pOriginatingProgram,
   uint                  dwTid,
   uint                  dwEvalFlags,
   IDebugEventCallback2 pExprCallback,
   int                   fWatch
);
```

## <a name="parameters"></a>Parametri
`pOriginatingProgram`\
[in] Oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma che sta valutando un'espressione.

`dwTid`\
[in] Specifica l'identificatore del thread.

`dwEvalFlags`\
[in] Combinazione di flag dell'enumerazione [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) che specificano come deve essere eseguita la valutazione.

`pExprCallback`\
[in] Oggetto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) da utilizzare per inviare eventi di debug che si verificano durante la valutazione dell'espressione.

`fWatch`\
[in] Se diverso da`TRUE`zero ( ), consente `dwTid`la valutazione dell'espressione nel thread identificato da ; in caso`FALSE`contrario, zero ( ) non consente la valutazione dell'espressione in tale thread.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Quando il gestore di sessione di debug (SDM) chiede a un programma, identificato dal `pOriginatingProgram` parametro, per valutare un'espressione, notifica tutti gli altri programmi collegati chiamando questo metodo.

 La valutazione dell'espressione in un programma può causare l'esecuzione `IDispatch` del codice in un altro, a causa della valutazione della funzione o della valutazione di qualsiasi proprietà. Per questo motivo, questo metodo consente l'esecuzione e il completamento della valutazione dell'espressione anche se il thread potrebbe essere arrestato in questo programma.

## <a name="see-also"></a>Vedere anche
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
