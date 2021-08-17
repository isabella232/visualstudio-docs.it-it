---
description: IDebugProgram2::Continue continua l'esecuzione del programma da uno stato arrestato. Qualsiasi stato di esecuzione precedente, ad esempio un passaggio, viene mantenuto e l'esecuzione del programma viene avviata nuovamente.
title: IDebugProgram2::Continue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b29952af05a864a11e54c602afc559d03d5203faa354559f65079cb73a00cc43
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121416066"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Continua l'esecuzione del programma da uno stato arrestato. Qualsiasi stato di esecuzione precedente, ad esempio un passaggio, viene mantenuto e l'esecuzione del programma viene avviata nuovamente.

> [!NOTE]
> Questo metodo è deprecato. In [alternativa, usare](../../../extensibility/debugger/reference/idebugprocess3-continue.md) il metodo Continue.

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
`pThread` [in] Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato su questo programma indipendentemente dal numero di programmi di cui è in corso il debug o dal programma che ha generato l'evento di arresto. L'implementazione deve mantenere lo stato di esecuzione precedente (ad esempio un passaggio) e continuare l'esecuzione come se non fosse mai stata arrestata prima di completare l'esecuzione precedente. In altre parole, se un thread in questo programma stava eseguendo un'operazione di passaggio ed è stato arrestato perché un altro programma è stato arrestato e quindi è stato chiamato questo metodo, il programma deve completare l'operazione di passaggio originale.

> [!WARNING]
> Non inviare un evento di arresto o un evento immediato (sincrono) [all'evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; In caso contrario, il debugger potrebbe smettere di rispondere.

## <a name="see-also"></a>Vedi anche
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
