---
title: 'IDebugEngineProgram2:: WatchForExpressionEvaluationOnThread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebc513ead1ae911147217becd8f541cb11cd5585
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431472"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Consente o impedisce la valutazione di espressioni nel thread specificato, anche se il programma è stato arrestato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
 in Oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma che sta valutando un'espressione.  
  
 `dwTid`  
 in Specifica l'identificatore del thread.  
  
 `dwEvalFlags`  
 in Combinazione di flag dell'enumerazione [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) che specificano la modalità di esecuzione della valutazione.  
  
 `pExprCallback`  
 in Oggetto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) da utilizzare per inviare eventi di debug che si verificano durante la valutazione dell'espressione.  
  
 `fWatch`  
 in Se diverso da zero ( `TRUE` ), consente la valutazione dell'espressione sul thread identificato da `dwTid` ; in caso contrario, zero ( `FALSE` ) non consente la valutazione delle espressioni su tale thread.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 Quando la gestione del debug della sessione chiede a un programma, identificato dal `pOriginatingProgram` parametro, di valutare un'espressione, invia una notifica a tutti gli altri programmi collegati chiamando questo metodo.  
  
 La valutazione delle espressioni in un programma può causare l'esecuzione di codice in un altro programma, a causa della valutazione della funzione o della valutazione delle `IDispatch` Proprietà. Per questo motivo, questo metodo consente l'esecuzione e il completamento della valutazione dell'espressione anche se il thread può essere arrestato in questo programma.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
