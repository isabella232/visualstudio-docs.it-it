---
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: faa2767e54e9821c7b3270fa60f5be232a2c232f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325773"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Questo metodo converte un percorso di metodo e l'offset in un indirizzo di memoria.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetMethodLocationProperty( 
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodLocationProperty(
   string               upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>Parametri
`upstrFullyQualifiedMethodPlusOffset`\
[in] Il percorso di metodo e l'offset, espresso come stringa.

`pSymbolProvider`\
[in] Il provider di simboli espresso come un [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) oggetto.

`pAddress`\
[in] Un indirizzo all'interno del metodo, espresso come un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) oggetto.

`pBinder`\
[in] Lo strumento di associazione espressa come un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) oggetto.

`ppProperty`\
[out] Restituisce un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaccia che rappresenta l'indirizzo di memoria.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 L'indirizzo restituito è utilizzabile per impostare un punto di interruzione, ad esempio.

 Nonostante il nome `upstrFullyQualifiedMethodPlusOffset`, questo parametro può essere passato un nome di metodo parziali. In tal caso, il metodo selezionato sia quello che racchiude `pAddress`. Modalità di interpretazione di questo parametro è compito l'implementazione dell'analizzatore di espressioni e la lingua supportata.

## <a name="see-also"></a>Vedere anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)