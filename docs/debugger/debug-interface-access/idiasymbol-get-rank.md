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
ms.openlocfilehash: c38962ab5915a4235201e76e1828f84a56af1333
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2019
ms.locfileid: "64830788"
---
# <a name="idiasymbolgetrank"></a>IDiaSymbol::get_rank
Recupera la classificazione (numero di dimensioni) di una matrice multidimensionale di FORTRAN.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_rank ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il numero di dimensioni in una matrice multidimensionale di FORTRAN.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Note
 Numero di dimensioni si riferisce al numero di dimensioni nella matrice in cui la matrice viene dichiarata come `myarray[1,2,3]`. Questo esempio è presente un rango pari a 3 e 3 dimensioni. Numero di dimensioni non si applica a C++ che usa il concetto di una matrice di matrici per ogni dimensione (vale a dire `myarray[1][2][3]`).

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)