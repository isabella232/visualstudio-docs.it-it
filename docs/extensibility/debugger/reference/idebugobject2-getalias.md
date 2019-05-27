---
title: IDebugObject2::GetAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7e9a40db04342bcf75f6099c9143c38bf8b83482
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210042"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Ottiene l'alias associato all'oggetto, se presente.

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
[out] Restituisce un [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) dell'oggetto che rappresenta l'alias per questo oggetto; in caso contrario, restituisce un valore null.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Un alias per un oggetto viene creato con una chiamata per il [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)