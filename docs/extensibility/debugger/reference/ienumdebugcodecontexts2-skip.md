---
description: Ignora il numero specificato di elementi nell'enumerazione dei contesti di codice.
title: IEnumDebugCodeContexts2::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::Skip
helpviewer_keywords:
- IEnumDebugCodeContexts2::Skip
ms.assetid: 3451a3eb-bf5b-4ec5-acc9-aa5a24363801
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78454cc7f92648be75c5d00862fdf8d7382e77b64a84d612e3c3662c21e358e5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389371"
---
# <a name="ienumdebugcodecontexts2skip"></a>IEnumDebugCodeContexts2::Skip
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
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se è maggiore del numero di elementi `celt` rimanenti; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Se `celt` specifica un valore maggiore del numero di elementi rimanenti, l'enumerazione viene impostata sulla fine e viene `S_FALSE` restituito .

## <a name="see-also"></a>Vedi anche
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
