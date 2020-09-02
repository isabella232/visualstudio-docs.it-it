---
title: 'IDebugProcess3:: Step | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 054cfc305400e3916ed7ba796a74370dfc2c77a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386693"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Fa in modo che il processo passi un'istruzione o un'istruzione.

> [!NOTE]
> Questo metodo deve essere utilizzato al posto di [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md).

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Step(
   IDebugThread2* pThread,
   STEPKIND       sk,
   STEPUNIT       step,
);
```

```csharp
int Step(
   IDebugThread2 pThread,
   enum_STEPKIND sk,
   enum_STEPUNIT step
);
```

## <a name="parameters"></a>Parametri
`pThread`\
in Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread di cui viene eseguito il ripasso.

`sk`\
in Uno dei valori [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) .

`step`\
in Uno dei valori [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Osservazioni
 Se è presente una sincronizzazione dei thread o una comunicazione tra thread, gli altri thread del processo devono essere eseguiti quando viene eseguito un determinato thread.

 **Avviso** di Non inviare un evento di arresto o un evento immediato (sincrono) a [un evento durante](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) la gestione della chiamata; in caso contrario, il debugger potrebbe smettere di rispondere.

## <a name="see-also"></a>Vedere anche
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
