---
description: IDebugProgram2::Continue continua l'esecuzione del programma da uno stato arrestato. Qualsiasi stato di esecuzione precedente, ad esempio un passaggio, viene mantenuto e l'esecuzione del programma viene avviata di nuovo.
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
ms.openlocfilehash: 60d9e3d62c49def63ea49592e8cfee1e651a6c78
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159802"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Continua l'esecuzione del programma da uno stato arrestato. Qualsiasi stato di esecuzione precedente, ad esempio un passaggio, viene mantenuto e l'esecuzione del programma viene avviata di nuovo.

> [!NOTE]
> Questo metodo è deprecato. Usare invece [il metodo Continue.](../../../extensibility/debugger/reference/idebugprocess3-continue.md)

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
 Questo metodo viene chiamato su questo programma indipendentemente dal numero di programmi in fase di debug o dal programma che ha generato l'evento di arresto. L'implementazione deve mantenere lo stato di esecuzione precedente (ad esempio un passaggio) e continuare l'esecuzione come se non fosse mai stata arrestata prima di completare l'esecuzione precedente. In altre parole, se un thread in questo programma stava eseguendo un'operazione di passaggio ed è stato arrestato perché un altro programma è stato arrestato e quindi è stato chiamato questo metodo, il programma deve completare l'operazione di passaggio originale.

> [!WARNING]
> Non inviare un evento di arresto o un evento immediato (sincrono) a [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata. in caso contrario, il debugger potrebbe bloccarsi.

## <a name="see-also"></a>Vedi anche
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
