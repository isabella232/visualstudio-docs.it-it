---
title: Proprietà IDebugProgram2::Continue . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d04445a7a1c444f30a0ef5c156dcd7ad744c6f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723071"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Continua l'esecuzione del programma da uno stato arrestato. Qualsiasi stato di esecuzione precedente (ad esempio un passaggio) viene mantenuto e il programma viene avviato nuovamente l'esecuzione.

> [!NOTE]
> Questo metodo è deprecato. Utilizzare invece il metodo [Continue.](../../../extensibility/debugger/reference/idebugprocess3-continue.md)

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Continue( 
   IDebugThread2* pThread
);
```

```csharp
int Continue( 
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parametri
`pThread`[in] Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo viene chiamato su questo programma indipendentemente dal numero di programmi sottoposti a debug o dal programma che ha generato l'evento di arresto. L'implementazione deve mantenere lo stato di esecuzione precedente (ad esempio un passaggio) e continuare l'esecuzione come se non si fosse mai arrestata prima di completare l'esecuzione precedente. Vale a dire, se un thread in questo programma stava eseguendo un'operazione di passaggio ed è stato arrestato perché un altro programma arrestato, e quindi questo metodo è stato chiamato, il programma deve completare l'operazione di passaggio originale.

> [!WARNING]
> Non inviare un evento di arresto o un evento immediato (sincrona) [all'evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; in caso contrario, il debugger potrebbe bloccarsi.

## <a name="see-also"></a>Vedere anche
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
