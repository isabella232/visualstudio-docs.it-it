---
description: Questo metodo ignora il numero specificato di elementi nell'enumerazione dei campi.
title: IEnumDebugFields::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Skip
helpviewer_keywords:
- IEnumDebugFields::Skip method
ms.assetid: b3bc51c4-21ae-4913-800c-c2ca9dc18443
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f924209cb09c3280a8d9182fb0bfdb2b89ef9493
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122070522"
---
# <a name="ienumdebugfieldsskip"></a>IEnumDebugFields::Skip
Questo metodo ignora il numero specificato di elementi.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Skip(
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>Parametri
`celt`\
[in]Numero di elementi da ignorare.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se è maggiore del numero di elementi `celt` rimanenti; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Se specifica un valore maggiore del numero di elementi rimanenti, l'enumerazione `celt` viene impostata sulla fine e viene `S_FALSE` restituito .

## <a name="see-also"></a>Vedi anche
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
