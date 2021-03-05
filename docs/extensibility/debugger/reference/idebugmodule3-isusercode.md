---
description: Recupera informazioni sul fatto che il modulo rappresenti o meno il codice utente.
title: 'IDebugModule3:: IsUserCode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a936d4408b2d289477a860ffca3d53ca7b0ad61d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164838"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
Recupera informazioni sul fatto che il modulo rappresenti o meno il codice utente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT IsUserCode(
   BOOL* pfUser
);
```

```csharp
int IsUserCode(
   out int pfUser
);
```

## <a name="parameters"></a>Parametri
`pfUser`\
out Diverso da zero ( `TRUE` ) se il modulo rappresenta il codice utente, zero ( `FALSE` ) in caso contrario.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
