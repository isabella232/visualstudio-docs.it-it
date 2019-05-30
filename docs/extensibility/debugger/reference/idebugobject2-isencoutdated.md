---
title: IDebugObject2::IsEncOutdated | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b2d26b49f3d2597e12e11a323a9281bd5c676fa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317411"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Questo metodo determina se lo stato di modifica e continuazione di questo oggetto o del contenitore padre non è aggiornato. Un analizzatore di espressioni personalizzato non implementa questo metodo e restituisce sempre `E_NOTIMPL`.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT IsEncOutdated(
   BOOL* pfEncOutdated
);
```

```csharp
int IsEncOutdated(
   out int pfEncOutdated
);
```

## <a name="parameters"></a>Parametri
`pfEncOutdated`\
[out] Diverso da zero (`TRUE`) se lo stato di modifica e continuazione non è aggiornato, zero (`FALSE`) in caso contrario.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

> [!NOTE]
> Un analizzatore di espressioni personalizzato deve sempre restituire `E_NOTIMPL`.

## <a name="see-also"></a>Vedere anche
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)