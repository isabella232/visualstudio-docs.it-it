---
title: IDebugEngineProgram2::Stop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3cb9627ba11bdec5729383bd6a31e4a338f3ef9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920334"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Arresta tutti i thread in esecuzione in questo programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Stop( 
   void 
);
```

```csharp
int Stop();
```

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo viene chiamato quando questo programma viene eseguito il debug in un ambiente multi-programma. Quando viene ricevuto un evento di arresto da un altro programma, questo metodo viene chiamato su questo programma. L'implementazione di questo metodo deve essere asincrono; vale a dire, non tutti i thread deve essere obbligatorio deve essere arrestato prima di questo metodo restituisce. L'implementazione di questo metodo potrebbe essere semplice come chiamare le [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) metodo su questo programma.

 Nessun evento di debug viene inviato in risposta a questo metodo.

## <a name="see-also"></a>Vedere anche
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)