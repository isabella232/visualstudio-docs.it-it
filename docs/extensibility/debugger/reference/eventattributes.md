---
title: EVENTATTRIBUTES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a3361d27a9e0a4a1f56035c0d2af20d9fa9a9303
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337760"
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
Indica che l'evento è asincrona e non necessita di alcuna risposta all'evento.

`EVENT_SYNCHRONOUS`\
Indica che l'evento è sincrona; per mezzo di rispondere [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).

`EVENT_STOPPING`\
Indica che si tratta di un evento di arresto. Deve essere combinato con `EVENT_ASYNCHRONOUS` o `EVENT_SYNCHRONOUS`.

`EVENT_ASYNC_STOP`\
Indica un evento di arresto asincrona. Non è attualmente alcun evento di questo tipo. Questo flag è solo un segnaposto.

`EVENT_SYNC_STOP`\
Indica un evento di arresto sincrono (una combinazione di `EVENT_SYNCHRONOUS` e `EVENT_STOPPING`). Questo valore viene utilizzato da un motore di debug (DE) quando si invia un evento di arresto. La risposta viene effettuata mediante una chiamata a [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [passaggio](../../../extensibility/debugger/reference/idebugprogram2-step.md), o [continua](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

`EVENT_IMMEDIATE`\
Indica un evento che viene inviato immediatamente e in modo sincrono all'IDE. Questo flag viene combinato con altri flag Analogamente `EVENT_ASYNCHRONOUS`, `EVENT_SYNCHRONOUS`, o `EVENT_SYNC_STOP` per indicare il tipo di evento e il fatto che il meccanismo di risposta (se presente) è noto.

`EVENT_EXPRESSION_EVALUATION`\
L'evento è il risultato della valutazione dell'espressione.

## <a name="remarks"></a>Note
Questi valori vengono passati il `dwAttrib` parametro del [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) (metodo).

Questi valori possono essere combinati con un bit per bit `OR`.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
