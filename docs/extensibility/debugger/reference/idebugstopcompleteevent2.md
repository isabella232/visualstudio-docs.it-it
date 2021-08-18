---
description: Il motore di debug (DE) può inviare questo evento facoltativo al gestore di debug sessione (SDM) quando un programma è stato arrestato.
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 55e6bbe87f6b57f95cad69fcd545aef9afede6f5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095920"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Il motore di debug (DE) può inviare questo evento facoltativo al gestore di debug sessione (SDM) quando un programma è stato arrestato.

## <a name="syntax"></a>Sintassi

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori

Questa interfaccia è stata introdotta con Visual Studio 2005. Le versioni precedenti non supportano l'arresto asincrono.

- [L'arresto](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) viene chiamato da SDM in scenari multi-processo o multi-programma. Quando un programma invia un evento di arresto a SDM, il modello SDM richiede anche l'arresto di altri programmi.

L'arresto viene usato per informare in modo asincrono SDM che un programma è stato arrestato. L'informazione di SDM è utile per un motore di debug dell'interprete, in cui talvolta non è in esecuzione codice all'interno del programma di cui è stato eseguito il debug, pertanto [l'arresto](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) non può essere completato in modo sincrono. Se un motore di debug vuole utilizzare questa notifica asincrona, deve restituire `S_ASYNC_STOP` da [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Requisiti

Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
