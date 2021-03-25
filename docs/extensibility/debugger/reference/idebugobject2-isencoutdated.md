---
description: Questo metodo determina se lo stato di modifica e continuazione di questo oggetto o del contenitore padre è obsoleto.
title: 'IDebugObject2:: IsEncOutdated | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e9b78eb0295d039d4f5d8ca3169cb77d04321aaf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053737"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Questo metodo determina se lo stato di modifica e continuazione di questo oggetto o del contenitore padre è obsoleto. Un analizzatore di espressioni personalizzato non implementa questo metodo e restituisce sempre `E_NOTIMPL` .

## <a name="syntax"></a>Sintassi

```cpp
HRESULT IsEncOutdated(
   BOOL* pfEncOutdated
);
```

```csharp
int IsEncOutdated(
   out int pfEncOutdated
);
```

## <a name="parameters"></a>Parametri
`pfEncOutdated`\
out Diverso da zero ( `TRUE` ) se lo stato di modifica e continuazione non è aggiornato, in caso contrario, zero ( `FALSE` ).

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

> [!NOTE]
> Un analizzatore di espressioni personalizzato deve sempre restituire `E_NOTIMPL` .

## <a name="see-also"></a>Vedi anche
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
