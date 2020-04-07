---
title: Proprietà IDebugProgram2::Execute . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f34ebea67ff95d1da6d777cdd828604f4a2f56e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722976"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Continua l'esecuzione del programma da uno stato arrestato. Qualsiasi stato di esecuzione precedente (ad esempio un passaggio) viene cancellato e il programma viene avviato nuovamente l'esecuzione.

> [!NOTE]
> Questo metodo è deprecato. Utilizzare invece il metodo [Execute.](../../../extensibility/debugger/reference/idebugprocess3-execute.md)

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

## <a name="remarks"></a>Osservazioni
 Quando l'utente avvia l'esecuzione da uno stato arrestato nel thread di un altro programma, questo metodo viene chiamato su questo programma. Questo metodo viene chiamato anche quando l'utente seleziona il **start** comando dal **Debug** menu nell'IDE. L'implementazione di questo metodo può essere semplice come chiamare il [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) metodo sul thread corrente nel programma.

> [!WARNING]
> Non inviare un evento di arresto o un evento immediato (sincrona) [all'evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; in caso contrario, il debugger potrebbe bloccarsi.

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Riprendi](../../../extensibility/debugger/reference/idebugthread2-resume.md)
