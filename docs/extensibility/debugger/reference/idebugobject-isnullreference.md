---
title: Proprietà IDebugObject::IsNullReference . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e4b6e5f2d28d27deb5e4e1ff8278a071ff9110fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726523"
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
[fuori] Restituisce diverso`TRUE`da zero ( ) se questo oggetto è un riferimento null; in caso contrario, restituisce zero (`FALSE`).

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Un riferimento null indica un oggetto vuoto o un oggetto a cui non è stato assegnato.

## <a name="see-also"></a>Vedere anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
