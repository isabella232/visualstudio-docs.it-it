---
title: IDebugProcess3::Step | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 686e8dfbd94fc3fddbc5e696fc6e943184357c02
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711527"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Fa sì che il processo eseguire un'istruzione o istruzione.

> [!NOTE]
>  Questo metodo deve essere usato al posto di [passaggio](../../../extensibility/debugger/reference/idebugprogram2-step.md).

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Step(
   IDebugThread2* pThread,
   STEPKIND       sk,
   STEPUNIT       step,
);
```

```csharp
int Step(
   IDebugThread2 pThread,
   enum_STEPKIND sk,
   enum_STEPUNIT step
);
```

#### <a name="parameters"></a>Parametri
 `pThread`

 [in] Un' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) oggetto che rappresenta il thread in corso rientri.

 `sk`

 [in] Uno dei [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) valori.

 `step`

 [in] Uno dei [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) valori.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Note
 In caso di qualsiasi sincronizzazione dei thread o comunicazione tra thread, gli altri thread nel processo deve essere eseguito quando un thread specifico è l'esecuzione di istruzioni.

 **Avviso** non invia un evento di arresto o di un evento (sincrono) immediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; in caso contrario, il debugger potrebbe bloccarsi.

## <a name="see-also"></a>Vedere anche
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)
- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)