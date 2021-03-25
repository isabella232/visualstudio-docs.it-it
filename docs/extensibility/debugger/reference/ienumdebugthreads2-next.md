---
description: Restituisce il set successivo di elementi dall'enumerazione dei thread.
title: 'IEnumDebugThreads2:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Next
helpviewer_keywords:
- IEnumDebugThreads2::Next
ms.assetid: bcffd954-3c67-4867-96f3-041ddb3e34d4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 373cccd0b03efe1e4d65d1910b5b06f60ecb4ea1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082673"
---
# <a name="ienumdebugthreads2next"></a>IEnumDebugThreads2::Next
Restituisce il successivo set di elementi dall'enumerazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Next(
   ULONG           celt,
   IDebugThread2** rgelt,
   ULONG*          pceltFetched
);
```

```csharp
int Next(
   uint            celt,
   IDebugThread2[] rgelt,
   ref uint        pceltFetched
);
```

## <a name="parameters"></a>Parametri
`celt`\
[in] Numero di elementi da recuperare. Specifica inoltre la dimensione massima della `rgelt` matrice.

`rgelt`\
[in, out] Matrice di elementi [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) da compilare.

`pceltFetched`\
out Restituisce il numero di elementi effettivamente restituiti in `rgelt` .

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se è possibile che venga restituito un numero di elementi inferiore al numero richiesto; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
