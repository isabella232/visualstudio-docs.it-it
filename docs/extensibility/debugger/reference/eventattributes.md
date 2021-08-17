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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c496e30b5d20bfad7b06e44660045e2e2394ed1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073071"
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
Indica che l'evento è sincrono. rispondere tramite [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).

`EVENT_STOPPING`\
Indica che si tratta di un evento di arresto. Deve essere combinato con o `EVENT_ASYNCHRONOUS` `EVENT_SYNCHRONOUS` .

`EVENT_ASYNC_STOP`\
Indica un evento di arresto asincrono. Non esiste attualmente alcun evento di questo tipo. Questo flag è solo un segnaposto.

`EVENT_SYNC_STOP`\
Indica un evento di arresto sincrono (una combinazione `EVENT_SYNCHRONOUS` di e `EVENT_STOPPING` ). Questo valore viene usato da un motore di debug quando invia un evento di arresto. La risposta viene effettuata tramite una chiamata a [Execute,](../../../extensibility/debugger/reference/idebugprogram2-execute.md) [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)o [Continue.](../../../extensibility/debugger/reference/idebugprogram2-continue.md)

`EVENT_IMMEDIATE`\
Indica un evento inviato immediatamente e in modo sincrono all'IDE. Questo flag viene combinato con altri flag, ad esempio , o per indicare il tipo di evento e il fatto che il meccanismo di risposta `EVENT_ASYNCHRONOUS` `EVENT_SYNCHRONOUS` `EVENT_SYNC_STOP` (se presente) è noto.

`EVENT_EXPRESSION_EVALUATION`\
L'evento è il risultato della valutazione dell'espressione.

## <a name="remarks"></a>Commenti
Questi valori vengono passati nel `dwAttrib` parametro del [metodo](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Event.

Questi valori possono essere combinati con un oggetto bit per `OR` bit.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
