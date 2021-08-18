---
description: Fa sì che il processo passi un'istruzione o un'istruzione.
title: IDebugProcess3::Step | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27dc90056c9c0e5c0521a4102cec4714c72b3cc9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132821"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Fa sì che il processo passi un'istruzione o un'istruzione.

> [!NOTE]
> Questo metodo deve essere usato al posto del [passaggio](../../../extensibility/debugger/reference/idebugprogram2-step.md).

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
[in] Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread di cui si esegue l'esecuzione di un'interruzione.

`sk`\
[in] Uno dei [valori STEPKIND.](../../../extensibility/debugger/reference/stepkind.md)

`step`\
[in] Uno dei [valori di STEPUNIT.](../../../extensibility/debugger/reference/stepunit.md)

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Commenti
 In caso di sincronizzazione dei thread o di comunicazione tra thread, gli altri thread del processo devono essere eseguiti quando un particolare thread esegue un'istruzione alla volta.

 **Avviso** Non inviare un evento di arresto o un evento immediato (sincrono) [all'evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; In caso contrario, il debugger potrebbe smettere di rispondere.

## <a name="see-also"></a>Vedi anche
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
