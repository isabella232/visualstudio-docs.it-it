---
title: Proprietà IDebugObject2::GetAlias . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 53c72182b497e2b24d41a784c405d169c3db195f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726278"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Ottiene l'alias associato a questo oggetto, se presente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int GetAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parametri
`ppAlias`\
[fuori] Restituisce un [oggetto IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) che rappresenta l'alias per questo oggetto; in caso contrario, restituisce un valore null.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Un alias per un oggetto viene creato con una chiamata al [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) metodo.

## <a name="see-also"></a>Vedere anche
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
