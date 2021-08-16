---
description: Questo metodo converte la posizione e l'offset di un metodo in un indirizzo di memoria.
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8313366d5a2a1439f022a74a6c070f57598e77c00dcf33ac95fd74e868beeef6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360495"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Questo metodo converte la posizione e l'offset di un metodo in un indirizzo di memoria.

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
[in] Posizione e offset del metodo, espressi come stringa.

`pSymbolProvider`\
[in] Provider di simboli espresso come oggetto [IDebugSymbolProvider.](../../../extensibility/debugger/reference/idebugsymbolprovider.md)

`pAddress`\
[in] Indirizzo all'interno del metodo, espresso come [oggetto IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

`pBinder`\
[in] Il binder espresso come oggetto [IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)

`ppProperty`\
[out] Restituisce [un'interfaccia IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta l'indirizzo di memoria.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'indirizzo restituito può essere usato, ad esempio, per impostare un punto di interruzione.

 Nonostante il nome `upstrFullyQualifiedMethodPlusOffset` , a questo parametro può essere passato un nome di metodo parzialmente qualificato. In tal caso, il metodo selezionato è quello che racchiude `pAddress` . La modalità di interpretazione di questo parametro è in base all'implementazione dell'analizzatore di espressioni e al linguaggio che supporta.

## <a name="see-also"></a>Vedi anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
