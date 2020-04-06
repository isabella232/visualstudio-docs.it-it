---
title: Proprietà IDebugObject::IsProxy . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugObject::IsProxy
- IsProxy
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6cab0d0d0f5f1c2e491c9aa0fe9efd26b39e51df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726482"
---
# <a name="idebugobjectisproxy"></a>IDebugObject::IsProxy
Determina se l'oggetto è un proxy trasparente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT IsProxy (
   BOOL* pfIsProxy
);
```

```csharp
int IsProxy (
   out bool pfIsProxy
);
```

## <a name="parameters"></a>Parametri
`pfIsProxy`\
[fuori] `TRUE` se l'oggetto è un proxy trasparente; in `FALSE`caso contrario, .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo viene implementato dal motore di debug predefinito di C.

## <a name="see-also"></a>Vedere anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
