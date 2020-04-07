---
title: PROPRIETÀ EVENTATTRIBUTES . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c479058a5e6abb61fb419425706d2a8b26858d04
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737067"
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
Indica che l'evento è asincrono ed è necessaria alcuna risposta all'evento.

`EVENT_SYNCHRONOUS`\
Indica che l'evento è sincrono; rispondere tramite [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).

`EVENT_STOPPING`\
Indica che si tratta di un evento di arresto. Deve essere combinato `EVENT_ASYNCHRONOUS` `EVENT_SYNCHRONOUS`con uno o .

`EVENT_ASYNC_STOP`\
Indica un evento di arresto asincrono. Al momento non esiste alcun evento di questo tipo. Questo flag è solo un segnaposto.

`EVENT_SYNC_STOP`\
Indica un evento di arresto `EVENT_SYNCHRONOUS` sincrono (una combinazione di e `EVENT_STOPPING`). Questo valore viene utilizzato da un motore di debug (DE) quando invia un evento di arresto. La risposta viene effettuata tramite una chiamata a [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)o [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

`EVENT_IMMEDIATE`\
Indica un evento che viene inviato immediatamente e in modo sincrono all'IDE. Questo flag viene combinato `EVENT_ASYNCHRONOUS`con `EVENT_SYNCHRONOUS`altri `EVENT_SYNC_STOP` flag come , , o per indicare il tipo di evento e il fatto che il meccanismo di risposta (se presente) è noto.

`EVENT_EXPRESSION_EVALUATION`\
L'evento è il risultato della valutazione dell'espressione.

## <a name="remarks"></a>Osservazioni
Questi valori vengono `dwAttrib` passati nel parametro del metodo [Event.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

Questi valori possono essere combinati `OR`con un oggetto .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
