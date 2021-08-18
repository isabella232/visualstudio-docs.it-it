---
description: Consente o non consente la valutazione dell'espressione nel thread specificato, anche se il programma è stato arrestato.
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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c6f7563adf23ce6a75c504cca675e0f6ac7e9e84
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127220"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Consente o non consente la valutazione dell'espressione nel thread specificato, anche se il programma è stato arrestato.

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
[in] Combinazione di flag [dell'enumerazione EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) che specificano la modalità di esecuzione della valutazione.

`pExprCallback`\
[in] Oggetto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) da usare per inviare eventi di debug che si verificano durante la valutazione dell'espressione.

`fWatch`\
[in] Se diverso da zero ( ), consente la valutazione dell'espressione nel thread identificato da ; in caso contrario, zero ( ) non consente la valutazione `TRUE` `dwTid` dell'espressione su tale `FALSE` thread.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Quando gestione debug sessione (SDM) chiede a un programma, identificato dal parametro , di valutare un'espressione, invia una notifica a tutti gli altri programmi collegati chiamando `pOriginatingProgram` questo metodo.

 La valutazione delle espressioni in un programma può causare l'esecuzione del codice in un altro, a causa della valutazione della funzione o della valutazione di qualsiasi `IDispatch` proprietà. Per questo scopo, questo metodo consente l'esecuzione e il completamento della valutazione delle espressioni anche se il thread può essere arrestato in questo programma.

## <a name="see-also"></a>Vedi anche
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
