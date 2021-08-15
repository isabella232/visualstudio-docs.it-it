---
description: Questo metodo determina se lo stato di Modifica e continuazione di questo oggetto o del contenitore padre non è aggiornato.
title: IDebugObject2::IsEncOutdated | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0293ebb0d83d0201c669a2d7c8ce1ac7773ec40dffae53d1e2b274def4a75bb0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121307180"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Questo metodo determina se lo stato di Modifica e continuazione di questo oggetto o del contenitore padre non è aggiornato. Un analizzatore di espressioni personalizzato non implementa questo metodo e restituisce sempre `E_NOTIMPL` .

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
[out] Diverso da zero ( ) se lo stato di Modifica e continuazione non è `TRUE` aggiornato, zero ( `FALSE` ) in caso contrario.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

> [!NOTE]
> Un analizzatore di espressioni personalizzato deve restituire sempre `E_NOTIMPL` .

## <a name="see-also"></a>Vedi anche
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
