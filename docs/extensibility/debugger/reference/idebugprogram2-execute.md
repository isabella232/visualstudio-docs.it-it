---
title: 'IDebugProgram2:: Execute | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 25f1544fe13c6dc44aa90b73f69854893beae14f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844736"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Continua l'esecuzione del programma da uno stato interrotto. Qualsiasi stato di esecuzione precedente (ad esempio un passaggio) viene cancellato e l'esecuzione del programma viene nuovamente avviata.

> [!NOTE]
> Questo metodo è deprecato. Usare invece il metodo [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) .

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Execute(
   void
);
```

```csharp
int Execute();
```

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Quando l'utente avvia l'esecuzione da uno stato interrotto nel thread di un altro programma, questo metodo viene chiamato su questo programma. Questo metodo viene chiamato anche quando l'utente seleziona il comando **Avvia** dal menu **debug** nell'IDE. L'implementazione di questo metodo può essere semplice quanto la chiamata al metodo [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) sul thread corrente del programma.

> [!WARNING]
> Non inviare un evento di arresto o un evento immediato (sincrono) a [un evento durante](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) la gestione della chiamata; in caso contrario, il debugger potrebbe smettere di rispondere.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Riprendi](../../../extensibility/debugger/reference/idebugthread2-resume.md)
