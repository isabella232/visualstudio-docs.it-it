---
title: 'IEnumDebugThreads2:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Skip
helpviewer_keywords:
- IEnumDebugThreads2::Skip
ms.assetid: eab068d4-1f8d-44cd-bc54-92a10fe23de6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2039f0b45d6d36c8ff439bdbced746f04aae01a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715099"
---
# <a name="ienumdebugthreads2skip"></a>IEnumDebugThreads2::Skip
Ignora il numero di elementi specificato.

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
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se `celt` è maggiore del numero di elementi rimanenti; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Se `celt` specifica un valore maggiore del numero di elementi rimanenti, l'enumerazione viene impostata sulla fine e `S_FALSE` viene restituito.

## <a name="see-also"></a>Vedere anche
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
