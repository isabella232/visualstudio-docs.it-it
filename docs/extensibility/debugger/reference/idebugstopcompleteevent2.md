---
description: Il motore di debug (DE) può inviare questo evento facoltativo a gestione debug sessione (SDM) quando un programma è stato arrestato.
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8e4fd1826f44cb1d830ef45874b1c41c21a34895
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087145"
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
