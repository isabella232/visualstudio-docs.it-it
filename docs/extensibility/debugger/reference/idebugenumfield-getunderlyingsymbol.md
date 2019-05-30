---
title: IDebugEnumField::GetUnderlyingSymbol | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 353b6d6f2a448cb7ac1bfdc98cc489688db9ee74
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345028"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
Questo metodo restituisce un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta il nome dell'enumerazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetUnderlyingSymbol(
   IDebugField** ppField
);
```

```csharp
int GetUnderlyingSymbol(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parametri
`ppField`\
[out] Restituisce il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che descriva il nome di questa enumerazione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Il nome dell'enumerazione contiene anche il tipo di enumerazione, che è associato a una posizione di memoria usando [associare](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="see-also"></a>Vedere anche
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)