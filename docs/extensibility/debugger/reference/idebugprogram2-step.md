---
description: Esegue un passaggio.
title: IDebugProgram2::Step | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 038c490fb9e889199193463f098e44386556b3fb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122071644"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Esegue un passaggio.

> [!NOTE]
> Questo metodo è deprecato. Usare invece [il metodo](../../../extensibility/debugger/reference/idebugprocess3-step.md) Step.

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
[in] Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread in fase di esecuzione.

`sk`\
[in] Valore [dell'enumerazione STEPKIND](../../../extensibility/debugger/reference/stepkind.md) che specifica il tipo di passaggio.

`step`\
[in] Valore [dell'enumerazione STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) che specifica l'unità di passaggio, ad esempio per istruzione o istruzione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Nel caso in cui sia presente una sincronizzazione dei thread o una comunicazione tra thread, gli altri thread nel programma devono essere eseguiti quando un thread specifico esegue istruzioni.

> [!WARNING]
> Non inviare un evento di arresto o un evento immediato (sincrono) a [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata. in caso contrario, il debugger potrebbe bloccarsi.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
