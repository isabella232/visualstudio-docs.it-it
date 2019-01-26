---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33272f87ae30832588a998ebea2fc46e9adaae50
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984236"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Il motore di debug (DE) può inviare questo evento facoltativo da gestore di sessione di debug (SDM) quando un programma è stato arrestato.

## <a name="syntax"></a>Sintassi

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori

Questa interfaccia è stato introdotto con Visual Studio 2005. Arresto asincrono non supporta le versioni precedenti.

[Arrestare](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) viene chiamato da SDM negli scenari a più processi o multi-programma. Quando un programma invia un evento di arresto per il modello SDM, il modello SDM richiede altri programmi per arrestare, troppo.

Arresto viene utilizzato per indicare in modo asincrono il modello SDM che un programma è stato arrestato. Per informare il modello SDM è utile per un motore di debug dell'interprete, in cui a volte codice non è in esecuzione all'interno in fase di debug del programma, pertanto [arrestare](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) non può essere eseguita in modo sincrono. Se un motore di debug vuole adottare questa notifica asincrona, deve restituire `S_ASYNC_STOP` dal [arrestare](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Requisiti

Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll