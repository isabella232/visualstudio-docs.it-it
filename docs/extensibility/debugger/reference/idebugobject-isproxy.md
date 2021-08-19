---
description: Determina se l'oggetto è un proxy trasparente.
title: IDebugObject::IsProxy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugObject::IsProxy
- IsProxy
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b44059371e45cd9c11ed0b81f0113934a05a3d8e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088392"
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
[out] `TRUE` se l'oggetto è un proxy trasparente; in caso contrario, `FALSE` .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene implementato dal motore di debug C++ predefinito.

## <a name="see-also"></a>Vedi anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
