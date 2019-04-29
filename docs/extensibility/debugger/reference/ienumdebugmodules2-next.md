---
title: IEnumDebugModules2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Next
helpviewer_keywords:
- IEnumDebugModules2::Next
ms.assetid: 46b7ccad-b07b-4ec0-b3ce-13981ffab7e8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c417847fc0c601f571e7bad23af07d2393f93f29
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62866907"
---
# <a name="ienumdebugmodules2next"></a>IEnumDebugModules2::Next
Restituisce il set successivo di elementi dall'enumerazione.

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

#### <a name="parameters"></a>Parametri
 `celt`

 [in] Il numero di elementi da recuperare. Specifica inoltre la dimensione massima del `rgelt` matrice.

 `rgelt`

 [in, out] Matrice di [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) elementi da compilare.

 `pceltFetched`

 [out] Restituisce il numero di elementi effettivamente restituiti nella `rgelt`.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se inferiore al numero richiesto di elementi potrebbe essere restituiti; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)