---
description: Ottiene il risultato della valutazione dell'espressione.
title: IDebugExpressionEvaluationCompleteEvent2::GetResult | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
ms.assetid: d9ad3e22-b6b2-421e-9a43-6bb8c70d12a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a34f3eabf5206210c09edc5a2f3719a9d8f9074963b75ff5175b01e0bbdb5ba9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121307544"
---
# <a name="idebugexpressionevaluationcompleteevent2getresult"></a>IDebugExpressionEvaluationCompleteEvent2::GetResult
Ottiene il risultato della valutazione dell'espressione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetResult( 
   IDebugProperty2** ppResult
);
```

```csharp
int GetResult( 
   out IDebugProperty2 ppResult
);
```

## <a name="parameters"></a>Parametri
`ppResult` [out] Restituisce un [oggetto IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta il risultato della valutazione dell'espressione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 [L'oggetto IDebugProperty2 restituito](../../../extensibility/debugger/reference/idebugproperty2.md) contiene il valore dell'espressione valutata. Si noti che questo valore può essere un valore complesso, ad esempio una matrice, ma il risultato finale deve essere un valore numerico o stringa visualizzato all'utente.

## <a name="see-also"></a>Vedi anche
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
