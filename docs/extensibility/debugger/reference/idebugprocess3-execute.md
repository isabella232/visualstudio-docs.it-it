---
description: Continua l'esecuzione di questo processo da uno stato arrestato. Qualsiasi stato di esecuzione precedente, ad esempio un passaggio, viene cancellato e l'esecuzione del processo viene avviata di nuovo.
title: IDebugProcess3::Execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b32c80a904e9ec96fd5f49b3d54c75fce26327b3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126674"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Continua l'esecuzione di questo processo da uno stato arrestato. Qualsiasi stato di esecuzione precedente, ad esempio un passaggio, viene cancellato e l'esecuzione del processo viene avviata di nuovo.

> [!NOTE]
> Questo metodo deve essere usato al posto di [Execute.](../../../extensibility/debugger/reference/idebugprogram2-execute.md)

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
[in] Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread da eseguire.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Commenti
 Quando l'utente avvia l'esecuzione da uno stato arrestato nel thread di un altro processo, questo metodo viene chiamato su questo processo. Questo metodo viene chiamato anche quando l'utente seleziona il **comando Avvia** dal menu **Debug** nell'IDE. L'implementazione di questo metodo può essere semplice quanto chiamare il metodo [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) sul thread corrente nel processo.

> [!WARNING]
> Non inviare un evento di arresto o un evento immediato (sincrono) [all'evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; In caso contrario, il debugger potrebbe smettere di rispondere.

## <a name="see-also"></a>Vedi anche
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Riprendi](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
