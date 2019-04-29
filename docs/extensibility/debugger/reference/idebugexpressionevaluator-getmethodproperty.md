---
title: IDebugExpressionEvaluator::GetMethodProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd13939a4c469c41d1d0726bb60aa443ab8fb9e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62919919"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Questo metodo ottiene un oggetto di proprietà che contiene le variabili locali, argomenti e altre proprietà di un metodo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetMethodProperty( 
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BOOL                  fIncludeHiddenLocals,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodProperty(
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   int                  fIncludeHiddenLocals,
   out IDebugProperty2  ppProperty
);
```

#### <a name="parameters"></a>Parametri
 `pSymbolProvider`

 [in] Il provider di simboli da utilizzare, espresse come una [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) oggetto.

 `pAddress`

 [in] L'indirizzo nel codice, espresso come un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) oggetto, che deve essere risolta nel più vicino che contiene funzioni.

 `pBinder`

 [in] Lo strumento di associazione da utilizzare, espresse come una [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) oggetto.

 `fIncludeHiddenLocals`

 [in] Diverso da zero (`TRUE`) significa che includere variabili locali nascosti; zero (`FALSE`) significa che non inserire nascosti variabili locali

 `ppProperty`

 [out] Restituisce un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oggetto che rappresenta il metodo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Variabili locali nascosti sono in genere le variabili che vengono generate dal compilatore.

## <a name="see-also"></a>Vedere anche
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)