---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da3eb33d76f55310e6428a34dd09cabbc271aa68
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719451"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Il motore di debug (DE) può inviare questo evento facoltativo a gestione debug sessione (SDM) quando un programma è stato arrestato.

## <a name="syntax"></a>Sintassi

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori

Questa interfaccia è stata introdotta con Visual Studio 2005. Le versioni precedenti non supportano l'arresto asincrono.

- [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) viene chiamato da SDM negli scenari multiprocesso o Multiprogramma. Quando un programma invia un evento di arresto al SDM, l'SDM richiede anche l'arresto di altri programmi.

Stop viene usato per informare in modo asincrono che un programma è stato arrestato. L'informativa di SDM è utile per un motore di debug dell'interprete, in cui talvolta nessun codice è in esecuzione all'interno del programma sottoposto a debug. non è quindi possibile completare l' [arresto](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) in modo sincrono. Se un motore di debug vuole usare questa notifica asincrona, deve restituire `S_ASYNC_STOP` from [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Requisiti

Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
