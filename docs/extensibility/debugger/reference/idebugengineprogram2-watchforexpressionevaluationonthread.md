---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c0572bfa8ebe1b70548483b17c58d08c8a0f9ca
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920367"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Consente o non consente la valutazione delle espressioni si verifichi nel thread specifico, anche se il programma è stato arrestato.

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

#### <a name="parameters"></a>Parametri
 `pOriginatingProgram`

 [in] Un' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto che rappresenta il programma che sta valutando un'espressione.

 `dwTid`

 [in] Specifica l'identificatore del thread.

 `dwEvalFlags`

 [in] Una combinazione di flag dal [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumerazione che specificano come deve essere eseguita la valutazione.

 `pExprCallback`

 [in] Un' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) oggetto da utilizzare per inviare gli eventi di debug che si verificano durante la valutazione dell'espressione.

 `fWatch`

 [in] Se diverso da zero (`TRUE`), consente la valutazione dell'espressione nel thread identificato da `dwTid`; in caso contrario, zero (`FALSE`) non consente la valutazione delle espressioni in tale thread.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Quando il gestore di debug di sessione (SDM) richiede un programma, identificato dal `pOriginatingProgram` parametro, per valutare un'espressione, notifica a tutti gli altri programmi collegati chiamando questo metodo.

 Valutazione dell'espressione in un programma potrebbe causare codice da eseguire in un'altra, a causa di valutazione della funzione o di valutazione di qualsiasi `IDispatch` proprietà. Per questo motivo, questo metodo consente di valutazione delle espressioni eseguire e completare anche se il thread può essere arrestato in questo programma.

## <a name="see-also"></a>Vedere anche
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)