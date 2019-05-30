---
title: IDebugPointerField::GetDereferencedField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fef8ee4e584703338afd09e5303ac184f28b3a49
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331618"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Questo metodo restituisce il tipo di oggetto a cui fa riferimento questo oggetto del puntatore.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetDereferencedField(
   IDebugField** ppField
);
```

```csharp
int GetDereferencedField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parametri
`ppField`\
[out] Restituisce un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che descrive il tipo di oggetto di destinazione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Se, ad esempio, il [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) oggetto punta a un numero intero, il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) tipo restituito da questo metodo descrive il tipo integer.

## <a name="see-also"></a>Vedere anche
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)