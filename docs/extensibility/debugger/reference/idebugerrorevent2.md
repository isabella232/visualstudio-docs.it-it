---
description: Questa interfaccia specifica un messaggio di errore da inviare all'utente.
title: IDebugErrorEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2
helpviewer_keywords:
- IDebugErrorEvent2 interface
ms.assetid: 275b6f38-b3d4-4cae-8491-491177f524fb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 3e1b781ed584714e149e1373f8be82e596aac464
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634843"
---
# <a name="idebugerrorevent2"></a>IDebugErrorEvent2
Questa interfaccia specifica un messaggio di errore da inviare all'utente.

## <a name="syntax"></a>Sintassi

```
IDebugErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia per segnalare gli errori come messaggi leggibili dall'utente. [L'interfaccia IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve essere implementata nello stesso oggetto di questa interfaccia. SDM usa [QueryInterface per](/cpp/atl/queryinterface) accedere all'interfaccia. `IDebugEvent2`

## <a name="notes-for-callers"></a>Note per i chiamanti
 Il de crea e invia questo oggetto evento per segnalare un errore. L'evento viene inviato usando la funzione di callback [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornita da SDM quando è collegato al programma in fase di debug.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 Questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|`GetErrorMessage`|Restituisce un errore come stringa leggibile dall'utente.|

## <a name="remarks"></a>Commenti
 Se il motore di debug rileva un errore, può usare questa interfaccia per segnalare il messaggio tramite Visual Studio all'utente.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
