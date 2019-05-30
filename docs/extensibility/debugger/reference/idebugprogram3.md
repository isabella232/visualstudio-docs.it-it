---
title: IDebugProgram3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0cfc29f300bc9f28f857424a7a91b4b6bfd3bf82
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331520"
---
# <a name="idebugprogram3"></a>IDebugProgram3
Questa interfaccia rappresenta un programma è in esecuzione in un processo che si estende [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md) fornendo informazioni relative al thread.

## <a name="syntax"></a>Sintassi

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) e un fornitore di porte personalizzate implementano questa interfaccia per rappresentare un programma in un processo. Gestore di sessione di debug (SDM) implementa anche questa interfaccia per fornire informazioni al [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) evento restituisce questa interfaccia per un nuovo programma. Questa interfaccia viene inoltre utilizzata come parametro per molti metodi in più interfacce.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDebugProgram3`.

|Metodo|Descrizione|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Esegue il programma. Il thread viene restituito per fornire le informazioni sui debugger thread in cui l'utente visualizza durante l'esecuzione.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Note
 Un programma è un contenitore di thread in esecuzione in una particolare architettura di runtime, mentre un processo è costituito da uno o più programmi.

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [avanti](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)