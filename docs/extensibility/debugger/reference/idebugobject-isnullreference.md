---
description: Verifica se questo oggetto è un riferimento null.
title: Interfaccia IDebugObject::IsNullReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dbc163532bf1f41327d3d9615f6fdf9a1bd3b320
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088497"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Verifica se questo oggetto è un riferimento null.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT IsNullReference( 
   BOOL* pfIsNull
);
```

```csharp
int IsNullReference(
   out int pfIsNull
);
```

## <a name="parameters"></a>Parametri
`pfIsNull`\
[out] Restituisce un valore diverso da zero ( `TRUE` ) se l'oggetto è un riferimento Null; in caso contrario, restituisce zero ( `FALSE` ).

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Un riferimento Null indica un oggetto vuoto o un oggetto a cui non è stato assegnato .

## <a name="see-also"></a>Vedi anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
