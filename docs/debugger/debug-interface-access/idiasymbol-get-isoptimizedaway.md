---
title: IDiaSymbol::get_isOptimizedAway | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c18b1e38-b152-4a13-aba0-59faded5b2e6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43ab9598262ba8dd73d6c0725e7bc8450f6ec218
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740156"
---
# <a name="idiasymbolget_isoptimizedaway"></a>IDiaSymbol::get_isOptimizedAway
Specifica se la variabile è ottimizzata.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isOptimizedAway(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Puntatore a un `BOOL` che specifica se la variabile è ottimizzata.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)