---
description: Ottiene il nome dell'alias.
title: IDebugAlias::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetName
helpviewer_keywords:
- IDebugAlias::GetName method
ms.assetid: ac2d8891-56b5-40ef-9866-ed74f18bb043
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63179ad1ca7c6e5f3c2a8173439bb5a4e2c915f6e4ae22578003b18a63259df6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403130"
---
# <a name="idebugaliasgetname"></a>IDebugAlias::GetName
Ottiene il nome dell'alias.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetName(
   BSTR* pbstrName
);
```

```csharp
int GetName(
   out string pbstrName
);
```

## <a name="parameters"></a>Parametri
`pbstrName`\
[out] Nome dell'alias.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
