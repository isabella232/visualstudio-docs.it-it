---
title: IEnumCodePaths2::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Skip
helpviewer_keywords:
- IEnumCodePaths2::Skip
ms.assetid: 356472d8-68b2-4b7e-b5f0-1f16d4ee80af
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef5b18ba54f3814469998ce0d60838e94beee6f7
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65223339"
---
# <a name="ienumcodepaths2skip"></a>IEnumCodePaths2::Skip
Ignora il numero specificato di elementi.

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

 [in] Numero di elementi da ignorare.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se `celt` è maggiore del numero di elementi rimanenti; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Se `celt` specifica un valore maggiore del numero di elementi rimanenti, l'enumerazione è impostata su Fine e `S_FALSE` viene restituito.

## <a name="see-also"></a>Vedere anche
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)