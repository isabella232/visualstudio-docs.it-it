---
title: 'IEnumDebugPorts2:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Next
helpviewer_keywords:
- IEnumDebugPorts2::Next
ms.assetid: 3f43d18c-6bd1-4ddd-95ef-9550abd2ad09
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08d48b2c99c30a23d1c534d8c732b5abe18438e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956984"
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
[in] Numero di elementi da recuperare. Specifica inoltre la dimensione massima della `rgelt` matrice.

`rgelt`\
[in, out] Matrice di elementi [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) da compilare.

`pceltFetched`\
out Restituisce il numero di elementi effettivamente restituiti in `rgelt` .

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se è possibile che venga restituito un numero di elementi inferiore al numero richiesto; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
