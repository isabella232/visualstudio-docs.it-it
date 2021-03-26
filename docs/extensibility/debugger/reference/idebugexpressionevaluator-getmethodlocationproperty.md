---
description: Questo metodo converte il percorso e l'offset di un metodo in un indirizzo di memoria.
title: 'IDebugExpressionEvaluator:: GetMethodLocationProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ddc9c17b90be6d65786d58ff2bf585461c4fc69f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092189"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Questo metodo converte il percorso e l'offset di un metodo in un indirizzo di memoria.

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
in Posizione e offset del metodo, espressi sotto forma di stringa.

`pSymbolProvider`\
in Il provider di simboli espresso come oggetto [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .

`pAddress`\
in Un indirizzo all'interno del metodo, espresso come un oggetto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`pBinder`\
in Binder espresso come oggetto [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .

`ppProperty`\
out Restituisce un'interfaccia [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta l'indirizzo di memoria.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'indirizzo restituito può essere utilizzato per impostare un punto di interruzione, ad esempio.

 Nonostante il nome `upstrFullyQualifiedMethodPlusOffset` , è possibile passare un nome di metodo parzialmente qualificato a questo parametro. In tal caso, il metodo selezionato è quello che racchiude `pAddress` . Il modo in cui questo parametro viene interpretato dipende dall'implementazione dell'analizzatore di espressioni e dal linguaggio supportato.

## <a name="see-also"></a>Vedi anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
