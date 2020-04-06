---
title: Proprietà IDebugProperty2::SetValueAsReference . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 73d00ccedc6985061448170735e9ebcaac42f530
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721260"
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
[in] Matrice di argomenti da passare al setter di proprietà del codice gestito. Se il setter di proprietà non accetta argomenti o se questo [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) oggetto non fa riferimento a tale setter di proprietà, `rgpArgs` deve essere un valore null. Questo parametro è in genere un valore null.

`dwArgCount`\
[in] Numero di argomenti `rgpArgs` nella matrice.

`pValue`\
[in] Un riferimento, sotto forma di un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) oggetto, al valore da utilizzare per impostare questa proprietà.

`dwTimeout`\
[in] Quanto tempo ci vuole per impostare il valore, in millisecondi. Un valore `INFINITE`tipico è . Ciò influisce sul periodo di tempo che può richiedere ogni possibile valutazione.

## <a name="return-value"></a>Valore restituito
 Se ha `S_OK`esito positivo, restituisce ; in caso contrario restituisce un codice di errore, in genere uno dei seguenti:

|Errore|Descrizione|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|L'impostazione del valore da un riferimento non è supportata.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Il valore non può essere impostato, poiché questa proprietà fa riferimento a un metodo.|
|`E_SETVALUE_VALUE_IS_READONLY`|Il valore è di sola lettura e non può essere impostato.|
|`E_NOTIMPL`|Il metodo non è implementato.|

## <a name="see-also"></a>Vedere anche
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
