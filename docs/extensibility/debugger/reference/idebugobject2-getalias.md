---
description: Ottiene l'alias associato a questo oggetto, se presente.
title: 'IDebugObject2:: getAlias | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c2cbf4a84af4001519617a7e6306c4139e763aea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053789"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Ottiene l'alias associato a questo oggetto, se presente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int GetAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parametri
`ppAlias`\
out Restituisce un oggetto [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) che rappresenta l'alias per questo oggetto. in caso contrario, restituisce un valore null.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Viene creato un alias per un oggetto con una chiamata al metodo [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
