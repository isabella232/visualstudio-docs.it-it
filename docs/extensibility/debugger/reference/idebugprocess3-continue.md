---
description: Continua l'esecuzione di questo processo da uno stato arrestato. Qualsiasi stato di esecuzione precedente, ad esempio un passaggio, viene mantenuto e il processo inizia di nuovo l'esecuzione.
title: IDebugProcess3::Continue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ace819a6503525f6aa7c65dbcc60187492da3dd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126687"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Continua l'esecuzione di questo processo da uno stato arrestato. Qualsiasi stato di esecuzione precedente, ad esempio un passaggio, viene mantenuto e il processo inizia di nuovo l'esecuzione.

> [!NOTE]
> Questo metodo deve essere usato al posto di [Continue.](../../../extensibility/debugger/reference/idebugprogram2-continue.md)

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
`pThread`\
[in] Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread da continuare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato su questo processo indipendentemente dal numero di processi di cui è in corso il debug o dal processo che ha generato l'evento di arresto. L'implementazione deve mantenere lo stato di esecuzione precedente (ad esempio un passaggio) e continuare l'esecuzione come se non fosse mai stata arrestata prima di completare l'esecuzione precedente. In altre parole, se un thread in questo processo stava eseguendo un'operazione di passaggio ed è stato arrestato perché un altro processo è stato arrestato e quindi è stato chiamato, il thread specificato deve completare l'operazione di passaggio `Continue` originale.

 **Avviso** Non inviare un evento di arresto o un evento immediato (sincrono) [all'evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; In caso contrario, il debugger potrebbe smettere di rispondere.

## <a name="see-also"></a>Vedi anche
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
