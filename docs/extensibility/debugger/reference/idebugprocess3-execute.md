---
title: Proprietà IDebugProcess3::Execute . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 444eadcce38adbd8ecd8655e8e0dc3f36f446848
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723675"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Continua l'esecuzione di questo processo da uno stato arrestato. Qualsiasi stato di esecuzione precedente (ad esempio un passaggio) viene cancellato e il processo viene avviato nuovamente l'esecuzione.

> [!NOTE]
> Questo metodo deve essere utilizzato al posto di [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md).

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Execute(
   IDebugThread2* pThread
);
```

```csharp
int Execute(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parametri
`pThread`\
[in] Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread da eseguire.

## <a name="return-value"></a>Valore restituito
 Se ha `S_OK`esito positivo, restituisce ; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Osservazioni
 Quando l'utente avvia l'esecuzione da uno stato arrestato nel thread di un altro processo, questo metodo viene chiamato su questo processo. Questo metodo viene chiamato anche quando l'utente seleziona il **start** comando dal **Debug** menu nell'IDE. L'implementazione di questo metodo può essere semplice come chiamare il [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) metodo sul thread corrente nel processo.

> [!WARNING]
> Non inviare un evento di arresto o un evento immediato (sincrona) [all'evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; in caso contrario, il debugger potrebbe bloccarsi.

## <a name="see-also"></a>Vedere anche
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Riprendi](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
