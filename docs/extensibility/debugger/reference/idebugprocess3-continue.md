---
title: 'IDebugProcess3:: continue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60ac7109b9f92a4ed7eecf57095c44fc4208b9f0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891059"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Continua l'esecuzione di questo processo da uno stato interrotto. Qualsiasi stato di esecuzione precedente (ad esempio un passaggio) viene mantenuto e il processo inizia a eseguire nuovamente l'esecuzione.

> [!NOTE]
> Questo metodo deve essere usato anziché [continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md).

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
in Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread da continuare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato su questo processo indipendentemente dal numero di processi di cui è in corso il debug o dal processo che ha generato l'evento di arresto. L'implementazione deve mantenere lo stato di esecuzione precedente (ad esempio un passaggio) e continuare l'esecuzione come se non fosse mai stata arrestata prima del completamento dell'esecuzione precedente. Ovvero, se un thread in questo processo stava eseguendo un'operazione Step-over ed è stato interrotto perché un altro processo è stato interrotto e quindi `Continue` è stato chiamato, il thread specificato deve completare l'operazione di passaggio a quella originale.

 **Avviso** di Non inviare un evento di arresto o un evento immediato (sincrono) a [un evento durante](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) la gestione della chiamata; in caso contrario, il debugger potrebbe smettere di rispondere.

## <a name="see-also"></a>Vedi anche
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
