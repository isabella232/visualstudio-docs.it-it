---
description: Reimposta l'enumerazione dei percorsi del codice sul primo elemento.
title: 'IEnumCodePaths2:: Reset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Reset
helpviewer_keywords:
- IEnumCodePaths2::Reset
ms.assetid: 490c0e19-ff4b-4673-bd06-cdee996ac226
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 35e77450ca610f94d266617f1a972290d667e3f4
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227164"
---
# <a name="ienumcodepaths2reset"></a>IEnumCodePaths2::Reset
Reimposta l'enumerazione sul primo elemento.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Dopo la chiamata a questo metodo, la chiamata successiva al metodo [successivo](../../../extensibility/debugger/reference/ienumcodepaths2-next.md) restituisce il primo elemento dell'enumerazione.

## <a name="see-also"></a>Vedi anche
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
