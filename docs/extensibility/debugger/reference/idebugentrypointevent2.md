---
title: IDebugEntryPointEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c2cd0f92e5bd954c8247fa86c39f3ad206aa99b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345104"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
Il motore di debug (DE) invia questa interfaccia al gestore di sessione di debug (SDM) quando il programma sta per essere eseguito nella prima istruzione del codice utente.

## <a name="syntax"></a>Sintassi

```
IDebugEntryPointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 La Germania implementa questa interfaccia come parte del normale funzionamento. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata per lo stesso oggetto di questa interfaccia. Usa il modello SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso di `IDebugEvent2` interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 La Germania crea e invia l'oggetto evento quando il programma sottoposto a debug è stato caricato ed è pronto per l'esecuzione della prima istruzione del codice utente. L'evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback che viene fornito per il modello SDM quando associato al programma in fase di debug.

## <a name="remarks"></a>Note
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) viene inviato quando il programma sta per essere eseguita molto prima istruzione. Ad esempio, `IDebugEntryPoint2` viene inviato quando il programma sta per essere eseguito il suo `main` (funzione).

 Quando invia la Germania `IDebugEntryPointEvent2`, la posizione corrente del codice deve essere alla prima istruzione del codice utente, ad esempio `main`.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)