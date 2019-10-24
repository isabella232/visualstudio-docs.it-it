---
title: IDiaSymbol::get_numberOfColumns | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 64834351-e2c9-4f1c-9dc0-2abb5478bc63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca99493f136c1a932f45fe719c52a9d85a1a852e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739684"
---
# <a name="idiasymbolget_numberofcolumns"></a>IDiaSymbol::get_numberOfColumns
Recupera il numero di colonne nella matrice.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_numberOfColumns(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Puntatore a un `DWORD` che include il numero di colonne nella matrice.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)