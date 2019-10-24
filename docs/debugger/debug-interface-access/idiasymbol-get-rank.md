---
title: IDiaSymbol::get_rank | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5cff86464a4034ad869cdfe231a88ad128dbf52
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739494"
---
# <a name="idiasymbolget_rank"></a>IDiaSymbol::get_rank
Recupera il rango (numero di dimensioni) di una matrice multidimensionale FORTRAN.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_rank ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce il numero di dimensioni in una matrice multidimensionale FORTRAN.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Note
 Rank indica il numero di dimensioni in una matrice in cui la matrice viene dichiarata come `myarray[1,2,3]`. Questo esempio ha un rango di 3 e 3 dimensioni. Rank non si applica a C++ che usa il concetto di matrice di matrici per ogni dimensione (ovvero `myarray[1][2][3]`).

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)