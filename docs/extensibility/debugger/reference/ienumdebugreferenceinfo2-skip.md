---
description: Ignora il numero specificato di DEBUG_REFERENCE_INFO elementi.
title: IEnumDebugReferenceInfo2::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2::Skip
helpviewer_keywords:
- IEnumDebugReferenceInfo2::Skip
ms.assetid: 12f07ed8-92bd-47b5-9113-f73fec5bdde6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 948fa317c298e0b13fcc9c8cc8fb6c35eae62083
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042907"
---
# <a name="ienumdebugreferenceinfo2skip"></a>IEnumDebugReferenceInfo2::Skip
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
 Se specifica un valore maggiore del numero di elementi rimanenti, l'enumerazione `celt` viene impostata sulla fine e viene `S_FALSE` restituito .

## <a name="see-also"></a>Vedi anche
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
