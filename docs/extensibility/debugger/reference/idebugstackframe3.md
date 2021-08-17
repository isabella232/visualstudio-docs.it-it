---
description: Questa interfaccia estende IDebugStackFrame2 per gestire le eccezioni intercettate.
title: IDebugStackFrame3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 6dbe76962d525daf22d276c229011ef318ba266d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126128"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Questa interfaccia estende [IDebugStackFrame2 per](../../../extensibility/debugger/reference/idebugstackframe2.md) gestire le eccezioni intercettate.

## <a name="syntax"></a>Sintassi

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia sullo stesso oggetto che implementa [l'interfaccia IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) per supportare le eccezioni intercettate.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [QueryInterface](/cpp/atl/queryinterface) su `IDebugStackFrame2` un'interfaccia per ottenere questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Oltre ai metodi ereditati da [IDebugStackFrame2,](../../../extensibility/debugger/reference/idebugstackframe2.md) `IDebugStackFrame3` espone i metodi seguenti.

|Metodo|Descrizione|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Gestisce un'eccezione per l'oggetto stack frame prima di qualsiasi normale gestione delle eccezioni.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Restituisce un contesto del codice se si verifica una rimozione dello stack.|

## <a name="remarks"></a>Commenti
 Un'eccezione intercettata significa che un debugger può elaborare un'eccezione prima che qualsiasi normale routine di gestione delle eccezioni venga chiamata dal run-time. Intercettare un'eccezione significa essenzialmente far fingere al run-time che sia presente un gestore di eccezioni anche quando non è presente.

- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) viene chiamato durante tutti i normali eventi di callback delle eccezioni (l'unica eccezione è quando si esegue il debug di codice in modalità mista (codice gestito e non gestito), nel qual caso l'eccezione non può essere intercettata durante il callback last-chance. Se DE non implementa o de restituisce un errore da `IDebugStackFrame3` IDebugStackFrame3:: (ad esempio ), il debugger gestirà normalmente `InterceptCurrentException` `E_NOTIMPL` l'eccezione.

 Intercettando un'eccezione, il debugger può consentire all'utente di apportare modifiche allo stato del programma in fase di debug e quindi riprendere l'esecuzione nel punto in cui è stata generata l'eccezione.

> [!NOTE]
> Le eccezioni intercettate sono consentite solo nel codice gestito, ovvero in un programma in esecuzione in Common Language Runtime (CLR).

 Un motore di debug indica che supporta l'intercettazione delle eccezioni impostando "metricExceptions" su un valore pari a 1 in fase di esecuzione usando la `SetMetric` funzione . Per altre informazioni, vedere [Helper SDK per il debug.](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
