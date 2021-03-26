---
description: Recupera una matrice di identificatori univoci per i motori di debug disponibili.
title: 'IDebugProcess3:: GetEngineFilter | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetEngineFilter
- IDebugProcess3::GetEngineFilter
ms.assetid: ccb7ecb0-f189-4e80-b5b2-221a095e01f5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c2628424f4f5e9446c763324dfcf9ced4f1896e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076563"
---
# <a name="idebugprocess3getenginefilter"></a>IDebugProcess3::GetEngineFilter
Recupera una matrice di identificatori univoci per i motori di debug disponibili.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetEngineFilter(
   GUID_ARRAY *pEngineArray
);
```

```csharp
public int GetEngineFilter(
   out GUID_ARRAY[] pEngineArray
);
```

## <a name="parameters"></a>Parametri
`pEngineArray`\
out Riferimento a una struttura che contiene identificatori univoci per i motori di debug.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)
