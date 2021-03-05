---
description: Questo metodo restituisce il tipo di oggetto a cui punta l'oggetto puntatore.
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
ms.openlocfilehash: 765ad40be87b7700ca1087745bef43ff0575dfa6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169704"
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
