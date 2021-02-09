---
title: 'IDebugPointerField:: GetDereferencedField | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b502b83ec793733ef642585b6ded260f72aa1be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869661"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Questo metodo restituisce il tipo di oggetto a cui punta l'oggetto puntatore.

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
out Restituisce un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che descrive il tipo di oggetto di destinazione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Se, ad esempio, l'oggetto [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) punta a un Integer, il tipo [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) restituito da questo metodo descrive tale tipo Integer.

## <a name="see-also"></a>Vedi anche
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
