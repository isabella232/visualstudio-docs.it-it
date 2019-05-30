---
title: IDebugErrorEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2
helpviewer_keywords:
- IDebugErrorEvent2 interface
ms.assetid: 275b6f38-b3d4-4cae-8491-491177f524fb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 945b04fc2d5a370ef4b2d17abd90e6bdaa818553
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327667"
---
# <a name="idebugerrorevent2"></a>IDebugErrorEvent2
Questa interfaccia specifica un messaggio di errore da segnalare all'utente.

## <a name="syntax"></a>Sintassi

```
IDebugErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) implementa questa interfaccia per segnalare gli errori come messaggi leggibili. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata per lo stesso oggetto di questa interfaccia. Usa il modello SDM [QueryInterface](/cpp/atl/queryinterface) per l'accesso di `IDebugEvent2` interfaccia.

## <a name="notes-for-callers"></a>Note per i chiamanti
 La Germania crea e invia l'oggetto evento per segnalare un errore. L'evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback che viene fornito per il modello SDM quando associato al programma in fase di debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|`GetErrorMessage`|Restituisce un errore sotto forma di stringa leggibile dall'utente.|

## <a name="remarks"></a>Note
 Se il motore di debug si verifica un errore, è possibile utilizzare questa interfaccia per segnalare il messaggio tramite Visual Studio per l'utente.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)