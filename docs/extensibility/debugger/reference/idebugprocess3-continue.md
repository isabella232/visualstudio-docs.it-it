---
description: Continua l'esecuzione di questo processo da uno stato arrestato. Qualsiasi stato di esecuzione precedente, ad esempio un passaggio, viene mantenuto e l'esecuzione del processo viene avviata di nuovo.
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
ms.openlocfilehash: 8e0dc621ce834582ee5a19a9124d856f94adaf2f706987176ff707c0c11fbd83
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121416235"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Continua l'esecuzione di questo processo da uno stato arrestato. Qualsiasi stato di esecuzione precedente, ad esempio un passaggio, viene mantenuto e l'esecuzione del processo viene avviata di nuovo.

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
 Questo metodo viene chiamato su questo processo indipendentemente dal numero di processi in fase di debug o dal processo che ha generato l'evento di arresto. L'implementazione deve mantenere lo stato di esecuzione precedente (ad esempio un passaggio) e continuare l'esecuzione come se non fosse mai stata arrestata prima di completare l'esecuzione precedente. In altre parole, se un thread in questo processo stava eseguendo un'operazione di passaggio ed è stato arrestato perché un altro processo è stato arrestato e quindi è stato chiamato, il thread specificato deve completare l'operazione di `Continue` passaggio originale.

 **Avviso** Non inviare un evento di arresto o un evento immediato (sincrono) a [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; in caso contrario, il debugger potrebbe bloccarsi.

## <a name="see-also"></a>Vedi anche
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
