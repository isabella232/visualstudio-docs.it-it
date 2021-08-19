---
description: Recupera informazioni sul fatto che il modulo rappresenti o meno il codice utente.
title: IDebugModule3::IsUserCode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 494f06ff4f5538ab9c12e80c7908b370fa21fcad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051014"
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
[out] Diverso da zero ( `TRUE` ) se il modulo rappresenta il codice utente, zero ( ) in caso `FALSE` contrario.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
