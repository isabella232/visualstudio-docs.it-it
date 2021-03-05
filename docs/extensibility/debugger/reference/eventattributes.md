---
description: Specifica gli attributi dell'evento.
title: EVENTATTRIBUTES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e6b56e815d8145e3f870468751a0978475245c86
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150887"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Specifica gli attributi dell'evento.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
typedef DWORD EVENTATTRIBUTES;
```

```csharp
public enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
```

## <a name="fields"></a>Campi
`EVENT_ASYNCHRONOUS`\
Indica che l'evento è asincrono e non è necessaria alcuna risposta all'evento.

`EVENT_SYNCHRONOUS`\
Indica che l'evento è sincrono; rispondere per mezzo di [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).

`EVENT_STOPPING`\
Indica che si tratta di un evento di arresto. Deve essere combinato con `EVENT_ASYNCHRONOUS` o `EVENT_SYNCHRONOUS` .

`EVENT_ASYNC_STOP`\
Indica un evento di arresto asincrono. Attualmente non esiste alcun evento di questo tipo. Questo flag è solo un segnaposto.

`EVENT_SYNC_STOP`\
Indica un evento di arresto sincrono, ovvero una combinazione di `EVENT_SYNCHRONOUS` e `EVENT_STOPPING` . Questo valore viene usato da un motore di debug (DE) quando invia un evento di arresto. La risposta viene effettuata per mezzo di una chiamata a [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)o [continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

`EVENT_IMMEDIATE`\
Indica un evento inviato immediatamente e in modo sincrono all'IDE. Questo flag è combinato con altri flag `EVENT_ASYNCHRONOUS` , ad esempio, `EVENT_SYNCHRONOUS` o, `EVENT_SYNC_STOP` per indicare il tipo di evento e il fatto che il meccanismo di risposta (se presente) è noto.

`EVENT_EXPRESSION_EVALUATION`\
L'evento è il risultato della valutazione dell'espressione.

## <a name="remarks"></a>Commenti
Questi valori vengono passati nel `dwAttrib` parametro del metodo dell' [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .

Questi valori possono essere combinati con un bit per bit `OR` .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
