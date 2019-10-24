---
title: IDiaSymbol::get_typeIds | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4db7c1d7e3ed19268d94b28a7f0500788f7d21f5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739077"
---
# <a name="idiasymbolget_typeids"></a>IDiaSymbol::get_typeIds
Recupera una matrice di valori di identificatore di tipo specifici del compilatore per questo simbolo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_typeIds ( 
   DWORD  cTypeIds,
   DWORD* pcTypeIds,
   DWORD  typeIds[]
);
```

#### <a name="parameters"></a>Parametri
 `cTypeIds`

in Dimensione del buffer in cui memorizzare i dati.

 `pcTypeIds`

out Restituisce il numero di `typeIds` scritti o, se `typeIds` è `NULL`, il numero totale di identificatori di tipo disponibili.

 `typeIds[]`

out Matrice da compilare con gli identificatori di tipo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)