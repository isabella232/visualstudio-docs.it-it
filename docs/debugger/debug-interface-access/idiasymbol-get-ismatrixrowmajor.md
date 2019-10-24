---
title: IDiaSymbol::get_isMatrixRowMajor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 36b1e881-ea76-48b0-b67f-e9eb0d19bec7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a685093bca4190c73c955c48665a14e494ac97c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740198"
---
# <a name="idiasymbolget_ismatrixrowmajor"></a>IDiaSymbol::get_isMatrixRowMajor
Specifica se la matrice è la riga principale.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isMatrixRowMajor(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Puntatore a un `BOOL` che specifica se la matrice è la riga principale.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)