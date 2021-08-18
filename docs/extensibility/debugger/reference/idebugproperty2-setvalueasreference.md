---
description: Imposta il valore di questa proprietà sul valore del riferimento specificato.
title: IDebugProperty2::SetValueAsReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e515a70a90440eae1277688aab2b98df8ced787b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110982"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Imposta il valore di questa proprietà sul valore del riferimento specificato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetValueAsReference(
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```csharp
int SetValueAsReference(
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Parametri
`rgpArgs`\
[in] Matrice di argomenti da passare al setter di proprietà del codice gestito. Se il setter di proprietà non accetta argomenti o se questo oggetto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) non fa riferimento a tale setter di proprietà, deve `rgpArgs` essere un valore Null. Questo parametro è in genere un valore Null.

`dwArgCount`\
[in] Numero di argomenti nella `rgpArgs` matrice.

`pValue`\
[in] Riferimento, sotto forma di oggetto [IDebugReference2,](../../../extensibility/debugger/reference/idebugreference2.md) al valore da usare per impostare questa proprietà.

`dwTimeout`\
[in] Tempo necessario per impostare il valore, espresso in millisecondi. Un valore tipico è `INFINITE` . Ciò influisce sul tempo che può richiedere qualsiasi valutazione possibile.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce ; in caso contrario, `S_OK` restituisce un codice di errore, in genere uno dei seguenti:

|Errore|Descrizione|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|L'impostazione del valore da un riferimento non è supportata.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Il valore non può essere impostato, poiché questa proprietà fa riferimento a un metodo.|
|`E_SETVALUE_VALUE_IS_READONLY`|Il valore è di sola lettura e non può essere impostato.|
|`E_NOTIMPL`|Il metodo non è implementato.|

## <a name="see-also"></a>Vedi anche
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
