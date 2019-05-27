---
title: IDebugProgram2::Continue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0b92f5b3c1e60c58bebb21fde5612e4fffc0340
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200423"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Continua l'esecuzione di questo programma da uno stato arrestato. Qualsiasi stato di esecuzione precedente (ad esempio, un passaggio) viene mantenuto, e il programma inizia l'esecuzione anche in questo caso.

> [!NOTE]
> Metodo deprecato. Usare la [continuazione](../../../extensibility/debugger/reference/idebugprocess3-continue.md) metodo invece.

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
`pThread` [in] Un' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) oggetto che rappresenta il thread.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo viene chiamato su questo programma, indipendentemente dal modo molti programmi sono in fase di debug o programma che viene generato l'evento stopping. L'implementazione deve mantenere lo stato di esecuzione precedente (ad esempio, un passaggio) e l'esecuzione continua come se non aveva mai arrestato prima di completare l'esecuzione precedente. Vale a dire, se un thread in questo programma stava eseguendo un'operazione dell'istruzione / routine ed è stato arrestato perché un altro programma arrestato e quindi è stato chiamato questo metodo, il programma deve completare l'operazione di routine / istruzione originale.

> [!WARNING]
> Non inviare un evento di arresto o di un evento (sincrono) immediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; in caso contrario, il debugger potrebbe bloccarsi.

## <a name="see-also"></a>Vedere anche
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)