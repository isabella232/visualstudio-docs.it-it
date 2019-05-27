---
title: IDebugProgram2::Step | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 37ff30958d0f8343c5dc77c441087334524d3cd1
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212557"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Esegue un passaggio.

> [!NOTE]
> Metodo deprecato. Usare la [passaggio](../../../extensibility/debugger/reference/idebugprocess3-step.md) metodo invece.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Step( 
   IDebugThread2*  pThread,
   STEPKIND        sk,
   STEPUNIT        step
);
```

```csharp
int Step( 
   IDebugThread2  pThread,
   enum_STEPKIND  sk,
   enum_STEPUNIT  step
);
```

## <a name="parameters"></a>Parametri
`pThread`\
[in] Un' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) oggetto che rappresenta il thread in corso rientri.

`sk`\
[in] Un valore compreso il [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) enumerazione che specifica il tipo di passaggio.

`step`\
[in] Un valore compreso il [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) enumerazione che specifica l'unità del passaggio (ad esempio, di istruzione o dell'istruzione).

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 In caso di qualsiasi sincronizzazione dei thread o comunicazione tra thread, altri thread nel programma deve essere eseguito quando un thread specifico è l'esecuzione di istruzioni.

> [!WARNING]
> Non inviare un evento di arresto o di un evento (sincrono) immediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; in caso contrario, il debugger potrebbe bloccarsi.

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)