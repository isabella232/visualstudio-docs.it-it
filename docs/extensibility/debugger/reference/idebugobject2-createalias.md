---
description: Crea un ID o un alias univoco per questo oggetto o restituisce un alias esistente.
title: IDebugObject2::CreateAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::CreateAlias
helpviewer_keywords:
- IDebugObject2::CreateAlias method
ms.assetid: 54a05920-5d13-4f67-962b-d1a7f013dff9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce75ad8f1b6e8bac1cc61281fef8b7dbbb268a2cd5121644f40822334eda1d66
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417015"
---
# <a name="idebugobject2createalias"></a>IDebugObject2::CreateAlias
Crea un ID o un alias univoco per questo oggetto o restituisce un alias esistente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreateAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int CreateAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parametri
`ppAlias`\
[out] Alias nuovo (o esistente).

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Un alias è un'etichetta che rappresenta un particolare oggetto mentre l'oggetto è in memoria.

## <a name="see-also"></a>Vedi anche
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
