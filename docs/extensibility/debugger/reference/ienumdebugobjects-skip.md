---
title: Proprietà IEnumDebugObjects::Skip . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Skip
helpviewer_keywords:
- IEnumDebugObjects::Skip method
ms.assetid: 957cead8-0a9c-4403-b190-b9fbadc49d42
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 80d2ae53ea7732a2120cf0431f33f929a0a6bc05
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716280"
---
# <a name="ienumdebugobjectsskip"></a>IEnumDebugObjects::Skip
Questo metodo ignora il numero di elementi specificato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Skip(
   [in] ULONG celt
);
```

```csharp
int Skip(
   [In] uint celt
);
```

## <a name="parameters"></a>Parametri
`celt`\
[in]Numero di elementi da ignorare.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. `S_FALSE` Restituisce `celt` if è maggiore del numero di elementi rimanenti; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Se `celt` specifica un valore maggiore del numero di elementi rimanenti, `S_FALSE` l'enumerazione viene impostata alla fine e viene restituita.

## <a name="see-also"></a>Vedere anche
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
