---
title: IDebugStackFrame3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5511624fb69015351d8cc37d6b27ad142a5956d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961183"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Questa interfaccia estende [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) per gestire le eccezioni intercettate.

## <a name="syntax"></a>Sintassi

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia sullo stesso oggetto che implementa l'interfaccia [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) per supportare le eccezioni intercettate.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su un' `IDebugStackFrame2` interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` espone i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Gestisce un'eccezione per la stack frame corrente prima di qualsiasi normale gestione delle eccezioni.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Restituisce un contesto di codice se si verifica una rimozione dello stack.|

## <a name="remarks"></a>Commenti
 Un'eccezione intercettata indica che un debugger è in grado di elaborare un'eccezione prima che le normali routine di gestione delle eccezioni vengano chiamate in fase di esecuzione. L'intercettazione di un'eccezione significa essenzialmente che la fase di esecuzione finge che esista un gestore di eccezioni anche quando non è presente.

- Quando si esegue il debug di codice in modalità mista (codice gestito e non gestito), [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) viene chiamato durante tutti gli eventi normali di callback delle eccezioni. l'unica eccezione è rappresentata dal fatto che l'eccezione non può essere intercettata durante il callback dell'ultima possibilità. Se il DE non implementa `IDebugStackFrame3` o se il valore di de restituisce un errore da IDebugStackFrame3:: `InterceptCurrentException` (ad esempio `E_NOTIMPL` ), il debugger gestirà l'eccezione normalmente.

 Intercettando un'eccezione, il debugger può consentire all'utente di apportare modifiche allo stato del programma di cui è in corso il debug, quindi riprendere l'esecuzione nel punto in cui è stata generata l'eccezione.

> [!NOTE]
> Le eccezioni intercettate sono consentite solo nel codice gestito, ovvero in un programma in esecuzione in Common Language Runtime (CLR).

 Un motore di debug indica che supporta l'intercettazione delle eccezioni impostando "metricExceptions" su un valore pari a 1 in fase di esecuzione utilizzando la `SetMetric` funzione. Per ulteriori informazioni, vedere [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
