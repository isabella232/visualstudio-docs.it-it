---
description: Questo metodo ottiene un oggetto proprietà che contiene le variabili locali, gli argomenti e altre proprietà di un metodo.
title: IDebugExpressionEvaluator::GetMethodProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d6ecc116719d37337e127c56a2a026ce5af21c7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122118710"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Questo metodo ottiene un oggetto proprietà che contiene le variabili locali, gli argomenti e altre proprietà di un metodo.

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
[in] Provider di simboli da utilizzare, espresso come oggetto [IDebugSymbolProvider.](../../../extensibility/debugger/reference/idebugsymbolprovider.md)

`pAddress`\
[in] Indirizzo nel codice, espresso come oggetto [IDebugAddress,](../../../extensibility/debugger/reference/idebugaddress.md) che deve essere risolto nella funzione contenitore più vicina.

`pBinder`\
[in] Binder da usare, espresso come oggetto [IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)

`fIncludeHiddenLocals`\
[in] Diverso da zero ( `TRUE` )significa includere le variabili locali nascoste; zero ( ) significa non includere `FALSE` le variabili locali nascoste

`ppProperty`\
[out] Restituisce un [oggetto IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta il metodo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Le variabili locali nascoste sono in genere variabili generate dal compilatore.

## <a name="see-also"></a>Vedi anche
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
