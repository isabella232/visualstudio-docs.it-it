---
title: IDiaSymbol::get_rank | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: da00422a5a12a12f99cf706b0bf7bb2ce623d76f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853681"
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
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Rank indica il numero di dimensioni in una matrice in cui la matrice viene dichiarata come `myarray[1,2,3]` . Questo esempio ha un rango di 3 e 3 dimensioni. Rank non si applica a C++ che usa il concetto di matrice di matrici per ogni dimensione (ovvero `myarray[1][2][3]` ).

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)