---
title: 'IDebugExpressionEvaluator:: GetMethodProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ebcf24ee39505091ff79c1f2f31d505217f77efb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729513"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Questo metodo ottiene un oggetto Property che contiene le variabili locali, gli argomenti e altre proprietà di un metodo.

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

## <a name="parameters"></a>Parametri
`pSymbolProvider`\
in Provider di simboli da utilizzare, espresso come oggetto [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .

`pAddress`\
in Indirizzo nel codice, espresso come oggetto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) , che deve essere risolto nella funzione contenitore più vicina.

`pBinder`\
in Binder da usare, espresso come oggetto [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .

`fIncludeHiddenLocals`\
in Diverso da zero ( `TRUE` ) indica l'inclusione di variabili locali nascoste. zero ( `FALSE` ) indica di escludere variabili locali nascoste

`ppProperty`\
out Restituisce un oggetto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta il metodo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Le variabili locali nascoste sono in genere variabili generate dal compilatore.

## <a name="see-also"></a>Vedere anche
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
