---
title: IDebugAlias::GetObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetObject
helpviewer_keywords:
- IDebugAlias::GetObject method
ms.assetid: 97bc3af6-6e55-4940-8a6d-692c61257806
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92d2265a6b3a17b632716729be12d92c96b65f03
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338144"
---
# <a name="idebugaliasgetobject"></a>IDebugAlias::GetObject
Ottiene l'oggetto di questo alias.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetObject(
   IDebugObject2** ppObject
);
```

```csharp
int GetObject(
   Out IDebugObject2 ppObject
)
```

## <a name="parameters"></a>Parametri
`ppObject`\
[out] Il [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) questo alias rappresenta.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)