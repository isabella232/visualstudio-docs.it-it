---
description: Restituisce il set successivo di elementi dall'enumerazione dei contesti di codice.
title: IEnumDebugCodeContexts2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::Next
helpviewer_keywords:
- IEnumDebugCodeContexts2::Next
ms.assetid: 0d8aa2db-0994-4166-b364-2e25d936fffc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16ae7e40e860964ec520af92c17b6a82be10006e79473a51bf315b63f8f874e9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389384"
---
# <a name="ienumdebugcodecontexts2next"></a>IEnumDebugCodeContexts2::Next
Restituisce il successivo set di elementi dall'enumerazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Next(
   ULONG                celt,
   IDebugCodeContext2** rgelt,
   ULONG*               pceltFetched
);
```

```csharp
int Next(
   uint                 celt,
   IDebugCodeContext2[] rgelt,
   ref uint             pceltFetched
);
```

## <a name="parameters"></a>Parametri
`celt`\
[in] Numero di elementi da recuperare. Specifica anche le dimensioni massime della `rgelt` matrice.

`rgelt`\
[in, out] Matrice di [elementi IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) da riempire.

`pceltFetched`\
[out] Restituisce il numero di elementi effettivamente restituiti in `rgelt` .

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce se è possibile restituire un numero inferiore al numero di elementi richiesto. In `S_FALSE` caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
