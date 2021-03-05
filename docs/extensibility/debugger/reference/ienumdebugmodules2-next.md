---
description: Restituisce il set successivo di elementi dall'enumerazione modules.
title: 'IEnumDebugModules2:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Next
helpviewer_keywords:
- IEnumDebugModules2::Next
ms.assetid: 46b7ccad-b07b-4ec0-b3ce-13981ffab7e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7c1d627579faea8bb4871feb310db79d6e5eea0
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226397"
---
# <a name="ienumdebugmodules2next"></a>IEnumDebugModules2::Next
Restituisce il successivo set di elementi dall'enumerazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Next(
   ULONG           celt,
   IDebugModule2** rgelt,
   ULONG*          pceltFetched
);
```

```csharp
int Next(
   uint            celt,
   IDebugModule2[] rgelt,
   ref uint        pceltFetched
);
```

## <a name="parameters"></a>Parametri
`celt`\
[in] Numero di elementi da recuperare. Specifica inoltre la dimensione massima della `rgelt` matrice.

`rgelt`\
[in, out] Matrice di elementi [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) da compilare.

`pceltFetched`\
out Restituisce il numero di elementi effettivamente restituiti in `rgelt` .

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se è possibile che venga restituito un numero di elementi inferiore al numero richiesto; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
