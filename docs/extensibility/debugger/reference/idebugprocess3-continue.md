---
title: IDebugProcess3::Continua Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f8fa2e21e31297279a173c9c9edd087adc560903
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723773"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Continua l'esecuzione di questo processo da uno stato arrestato. Qualsiasi stato di esecuzione precedente (ad esempio un passaggio) viene mantenuto e il processo inizia l'esecuzione.

> [!NOTE]
> Questo metodo deve essere utilizzato al posto di [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

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
`pThread`\
[in] Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread da continuare.

## <a name="return-value"></a>Valore restituito
 Se ha `S_OK`esito positivo, restituisce ; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo viene chiamato su questo processo indipendentemente dal numero di processi sottoposti a debug o da quale processo ha generato l'evento di arresto. L'implementazione deve mantenere lo stato di esecuzione precedente (ad esempio un passaggio) e continuare l'esecuzione come se non si fosse mai arrestata prima di completare l'esecuzione precedente. Ovvero, se un thread in questo processo stava eseguendo un'operazione di passaggio `Continue` ed è stato arrestato perché un altro processo si è arrestato e quindi è stato chiamato, il thread specificato deve completare l'operazione di passaggio originale.

 **Avvertenza** Non inviare un evento di arresto o un evento immediato (sincrona) [all'evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; in caso contrario, il debugger potrebbe bloccarsi.

## <a name="see-also"></a>Vedere anche
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
