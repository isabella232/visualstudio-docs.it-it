---
description: Recupera la classificazione (numero di dimensioni) di una matrice multidimensionale RANKRAN.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 03c61eea4e46f1e9223ee296f8728e8f4284bf31
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105433"
---
# <a name="idiasymbolget_rank"></a>IDiaSymbol::get_rank
Recupera la classificazione (numero di dimensioni) di una matrice multidimensionale RANKRAN.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_rank ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il numero di dimensioni in una matrice multidimensionale DIRRAN.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Il valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Rank si riferisce al numero di dimensioni in una matrice in cui la matrice è dichiarata come `myarray[1,2,3]` . Questo esempio ha una classificazione di 3 e 3 dimensioni. La classificazione non si applica a C++ che usa il concetto di matrice di matrici per ogni dimensione ,ovvero `myarray[1][2][3]` .

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
