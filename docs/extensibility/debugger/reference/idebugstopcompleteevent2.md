---
title: IDebugStopCompleteEvent2 . Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719451"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Il motore di debug (DE) può inviare questo evento facoltativo al gestore di sessione di debug (SDM) quando un programma è stato arrestato.

## <a name="syntax"></a>Sintassi

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori

Questa interfaccia è stata introdotta con Visual Studio 2005. Le versioni precedenti non supportavano l'arresto asincrono.

- [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) viene chiamato dal modello SDM in scenari multiprocesso o multiprogramma. Quando un programma invia un evento di arresto al modello SDM, anche il modello SDM richiede l'arresto di altri programmi.

Stop viene utilizzato per informare in modo asincrono il processo SDM che un programma è stato arrestato. Informare il processo SDM è utile per un motore di debug interprete, in cui a volte non è in esecuzione alcun codice all'interno del programma sottoposto a debug, pertanto [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) non può essere completato in modo sincrono. Se un motore di debug desidera utilizzare `S_ASYNC_STOP` questa notifica asincrona, deve restituire da [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Requisiti

Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
