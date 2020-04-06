---
title: Proprietà IEnumDebugPorts2::Next . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Next
helpviewer_keywords:
- IEnumDebugPorts2::Next
ms.assetid: 3f43d18c-6bd1-4ddd-95ef-9550abd2ad09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 66cb525157d5902b43a9924291d7c10260b40309
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716174"
---
# <a name="ienumdebugports2next"></a>IEnumDebugPorts2::Next
Restituisce il successivo set di elementi dall'enumerazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Next(
   ULONG         celt,
   IDebugPort2** rgelt,
   ULONG*        pceltFetched
);
```

```csharp
int Next(
   uint          celt,
   IDebugPort2[] rgelt,
   ref uint      pceltFetched
);
```

## <a name="parameters"></a>Parametri
`celt`\
[in] Numero di elementi da recuperare. Specifica anche la dimensione `rgelt` massima della matrice.

`rgelt`\
[in, out] Matrice di elementi [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) da compilare.

`pceltFetched`\
[fuori] Restituisce il numero di `rgelt`elementi effettivamente restituiti in .

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se è possibile restituire un numero di elementi inferiore al numero richiesto; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
