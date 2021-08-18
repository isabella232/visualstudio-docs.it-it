---
description: Restituisce il set successivo di elementi dall'enumerazione dei percorsi di codice.
title: IEnumCodePaths2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Next
helpviewer_keywords:
- IEnumCodePaths2::Next
ms.assetid: c7a8fe97-2abc-4cee-8aef-64f1daa93b5c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 536c793ae93c2b697d0eb420e82a60172570bc73
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125829"
---
# <a name="ienumcodepaths2next"></a>IEnumCodePaths2::Next
Restituisce il successivo set di elementi dall'enumerazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Next(
   ULONG       celt,
   CODE_PATH** rgelt,
   ULONG*      pceltFetched
);
```

```csharp
int Next(
   uint        celt,
   CODE_PATH[] rgelt,
   ref uint    pceltFetched
);
```

## <a name="parameters"></a>Parametri
`celt`\
[in] Numero di elementi da recuperare. Specifica anche le dimensioni massime della `rgelt` matrice.

`rgelt`\
[in, out] Matrice di [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) elementi da riempire.

`pceltFetched`\
[out] Restituisce il numero di elementi effettivamente restituiti in `rgelt` .

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce se è possibile restituire un numero inferiore al numero di `S_FALSE` elementi richiesto; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)
