---
title: Proprietà IDebugStackFrame3 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d86997d11e124fd5a47981314cf383f5cd8aff7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719478"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Questa interfaccia estende [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) per gestire le eccezioni intercettate.

## <a name="syntax"></a>Sintassi

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia sullo stesso oggetto che implementa il [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia per supportare le eccezioni intercettate.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) `IDebugStackFrame2` su un'interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` espone i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Gestisce un'eccezione per lo stack frame corrente prima di qualsiasi gestione regolare delle eccezioni.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Restituisce un contesto di codice se si verificasse una rimozione dello stack.|

## <a name="remarks"></a>Osservazioni
 Un'eccezione intercettata significa che un debugger può elaborare un'eccezione prima che qualsiasi normale routine di gestione delle eccezioni venga chiamata in fase di esecuzione. Intercettare un'eccezione significa essenzialmente far finta che in fase di esecuzione sia presente un gestore di eccezioni anche quando non è presente.

- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) viene chiamato durante tutti i normali eventi di callback di eccezione (l'unica eccezione è se si esegue il debug di codice in modalità mista (codice gestito e non gestito), nel qual caso l'eccezione non può essere intercettata durante il callback last-chance). Se il DE non `IDebugStackFrame3`implementa , o il DE restituisce un`InterceptCurrentException` errore `E_NOTIMPL`da IDebugStackFrame3:: (ad esempio ), il debugger gestirà l'eccezione normalmente.

 Intercettando un'eccezione, il debugger può consentire all'utente di apportare modifiche allo stato del programma sottoposto a debug e quindi riprendere l'esecuzione nel punto in cui è stata generata l'eccezione.

> [!NOTE]
> Le eccezioni intercettate sono consentite solo nel codice gestito, ovvero in un programma in esecuzione in Common Language Runtime (CLR).

 Un motore di debug indica che supporta l'intercettazione di eccezioni impostando "metricExceptions" `SetMetric` su un valore pari a 1 in fase di esecuzione utilizzando la funzione. Per ulteriori informazioni, vedere [SDK Helpers for Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
