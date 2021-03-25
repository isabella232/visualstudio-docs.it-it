---
description: Questa interfaccia fornisce supporto per il debug multithread.
title: IDebugEngineProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6e52ae6477b49325d4b8a4d81192fe2ecf736163
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092657"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Questa interfaccia fornisce supporto per il debug multithread.

## <a name="syntax"></a>Sintassi

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un motore di debug implementa questa interfaccia per supportare il debug simultaneo di più thread. Questa interfaccia viene implementata nello stesso oggetto che implementa l'interfaccia [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .

## <a name="notes-for-callers"></a>Note per i chiamanti
 Usare [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia da un' `IDebugProgram2` interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDebugEngineProgram2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Arresta tutti i thread in esecuzione in questo programma.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Esegue il controllo dell'esecuzione (o Interrompi l'esecuzione) nel thread specificato.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Consente o impedisce la valutazione di espressioni nel thread specificato, anche se il programma viene arrestato.|

## <a name="remarks"></a>Commenti
 Visual Studio chiama questa interfaccia in risposta a un evento [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) e per impostare gli Stati del programma "Watch for thread Step" e "Watch for Expression Evaluation on thread". [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) viene chiamato ogni volta che il programma deve essere arrestato. Questo metodo fornisce al programma la possibilità di terminare tutti i thread.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
