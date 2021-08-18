---
description: Questa interfaccia rappresenta un thread in esecuzione in un programma.
title: Interfaccia IDebugThread2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: e0618ab89a49849f86ee2560c928470e699ffd0d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122070815"
---
# <a name="idebugthread2"></a>IDebugThread2
Questa interfaccia rappresenta un thread in esecuzione in un programma.

## <a name="syntax"></a>Sintassi

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia per rappresentare un thread di esecuzione in un singolo programma.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) per ottenere questa interfaccia che rappresenta il thread attualmente attivo.

 Questa interfaccia viene usata anche nella creazione di una richiesta di punto di interruzione [(vedere BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).

 Questa interfaccia viene restituita anche durante la risoluzione di un punto di interruzione associato o di errore [(vedere](../../../extensibility/debugger/reference/bp-resolution-info.md) BP_RESOLUTION_INFO e [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugThread2` .

|Metodo|Descrizione|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Recupera un elenco degli stack frame per questo thread.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Ottiene il nome del thread.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Imposta il nome del thread.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Ottiene il programma in cui è in esecuzione un thread.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Determina se l'istruzione successiva può essere impostata sul contesto stack frame e sul contesto del codice specificati.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Imposta l'istruzione successiva sul contesto stack frame codice specificati.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Ottiene l'identificatore del thread di sistema.|
|[Sospendi](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Sospende un thread.|
|[Riprendi](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Riprende un thread.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Ottiene le proprietà che descrivono un thread.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Ottiene il thread logico associato a questo thread fisico.|

## <a name="remarks"></a>Commenti
 Poiché un singolo thread fisico può essere eseguito in più programmi, più di uno da più di un `IDebugThread2` programma può rappresentare lo stesso thread fisico.

 Quando si verifica un punto di interruzione o un'eccezione, viene inviato un evento chiamando [l'evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Uno degli argomenti di questo metodo è `IDebugThread2` un'interfaccia che rappresenta il thread corrente. [EnumFrameInfo viene](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) usato per ottenere [l'interfaccia IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) per il stack frame.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
