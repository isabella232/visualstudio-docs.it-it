---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d67290ea7bf88f8cdf01e88444cd69ec25d73a9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519258"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugEngineProgram2::WatchForExpressionEvaluationOnThread](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread).  
  
Consente o non consente la valutazione delle espressioni si verifichi nel thread specifico, anche se il programma è stato arrestato.  
  
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
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
