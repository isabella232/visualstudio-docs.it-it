---
description: Continua l'esecuzione di questo processo da uno stato interrotto. Qualsiasi stato di esecuzione precedente (ad esempio un passaggio) viene cancellato e l'esecuzione del processo viene nuovamente riavviata.
title: 'IDebugProcess3:: Execute | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 149497bcee5c37813e9d1134237ddb991d5893da
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150250"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Continua l'esecuzione di questo processo da uno stato interrotto. Qualsiasi stato di esecuzione precedente (ad esempio un passaggio) viene cancellato e l'esecuzione del processo viene nuovamente riavviata.

> [!NOTE]
> Questo metodo deve essere utilizzato al posto di [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md).

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Execute(
   IDebugThread2* pThread
);
```

```csharp
int Execute(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parametri
`pThread`\
in Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread da eseguire.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Commenti
 Quando l'utente avvia l'esecuzione da uno stato interrotto in un altro thread del processo, questo metodo viene chiamato su questo processo. Questo metodo viene chiamato anche quando l'utente seleziona il comando **Avvia** dal menu **debug** nell'IDE. L'implementazione di questo metodo può essere semplice quanto la chiamata al metodo [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) sul thread corrente nel processo.

> [!WARNING]
> Non inviare un evento di arresto o un evento immediato (sincrono) a [un evento durante](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) la gestione della chiamata; in caso contrario, il debugger potrebbe smettere di rispondere.

## <a name="see-also"></a>Vedi anche
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Riprendi](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
