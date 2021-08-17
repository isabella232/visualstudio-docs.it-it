---
description: IDebugProgram2::Execute continua l'esecuzione del programma da uno stato arrestato. Qualsiasi stato di esecuzione precedente, ad esempio un passaggio, viene cancellato e l'esecuzione del programma viene avviata di nuovo.
title: IDebugProgram2::Execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e79fcde5a554abedc030861004b8117a54a2366a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057447"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Continua l'esecuzione del programma da uno stato arrestato. Qualsiasi stato di esecuzione precedente, ad esempio un passaggio, viene cancellato e l'esecuzione del programma viene avviata di nuovo.

> [!NOTE]
> Questo metodo è deprecato. Usare invece [il metodo Execute.](../../../extensibility/debugger/reference/idebugprocess3-execute.md)

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
 Quando l'utente avvia l'esecuzione da uno stato arrestato nel thread di un altro programma, questo metodo viene chiamato su questo programma. Questo metodo viene chiamato anche quando l'utente seleziona il **comando Avvia** dal menu **Debug** nell'IDE. L'implementazione di questo metodo può essere semplice come chiamare il [metodo Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) sul thread corrente nel programma.

> [!WARNING]
> Non inviare un evento di arresto o un evento immediato (sincrono) a [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata. in caso contrario, il debugger potrebbe bloccarsi.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Riprendi](../../../extensibility/debugger/reference/idebugthread2-resume.md)
