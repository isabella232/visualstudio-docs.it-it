---
description: Ignora il numero specificato di elementi nell'enumerazione delle porte.
title: 'IEnumDebugPorts2:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Skip
helpviewer_keywords:
- IEnumDebugPorts2::Skip
ms.assetid: a837383f-7b39-4e06-b336-f1715b073dbe
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04ff77835470e4eb495de0af992ec6563cb3fba6
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224473"
---
# <a name="ienumdebugports2skip"></a>IEnumDebugPorts2::Skip
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

## <a name="remarks"></a>Commenti
 Se `celt` specifica un valore maggiore del numero di elementi rimanenti, l'enumerazione viene impostata sulla fine e `S_FALSE` viene restituito.

## <a name="see-also"></a>Vedi anche
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
