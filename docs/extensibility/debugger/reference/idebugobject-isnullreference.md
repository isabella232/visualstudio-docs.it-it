---
description: Verifica se l'oggetto è un riferimento null.
title: 'IDebugObject:: IsNullReference | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba037f995c97a3bfbf059f51bfb4f8777803a172
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054075"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Verifica se l'oggetto è un riferimento null.

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
out Restituisce un valore diverso da zero ( `TRUE` ) se l'oggetto è un riferimento null; in caso contrario, restituisce zero ( `FALSE` ).

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Un riferimento null indica un oggetto vuoto o un oggetto a cui non è stato assegnato.

## <a name="see-also"></a>Vedi anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
