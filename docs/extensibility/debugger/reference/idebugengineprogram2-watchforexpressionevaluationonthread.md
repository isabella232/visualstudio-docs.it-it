---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
titleSuffix: ''
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4f36431ef7a190e98d35e795ffd8213781553dfc
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036119"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Consente o impedisce la valutazione di espressioni nel thread specificato, anche se il programma è stato arrestato.

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
in Oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma che sta valutando un'espressione.

`dwTid`\
in Specifica l'identificatore del thread.

`dwEvalFlags`\
in Combinazione di flag dell'enumerazione [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) che specificano la modalità di esecuzione della valutazione.

`pExprCallback`\
in Oggetto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) da utilizzare per inviare eventi di debug che si verificano durante la valutazione dell'espressione.

`fWatch`\
in Se diverso da zero ( `TRUE` ), consente la valutazione dell'espressione sul thread identificato da `dwTid` ; in caso contrario, zero ( `FALSE` ) non consente la valutazione delle espressioni su tale thread.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Quando la gestione del debug della sessione chiede a un programma, identificato dal `pOriginatingProgram` parametro, di valutare un'espressione, invia una notifica a tutti gli altri programmi collegati chiamando questo metodo.

 La valutazione delle espressioni in un programma può causare l'esecuzione di codice in un altro programma, a causa della valutazione della funzione o della valutazione delle `IDispatch` Proprietà. Per questo motivo, questo metodo consente l'esecuzione e il completamento della valutazione dell'espressione anche se il thread può essere arrestato in questo programma.

## <a name="see-also"></a>Vedi anche
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
