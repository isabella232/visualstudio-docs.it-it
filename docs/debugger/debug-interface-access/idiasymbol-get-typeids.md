---
description: Recupera una matrice di valori di identificatore di tipo specifici del compilatore per questo simbolo.
title: IDiaSymbol::get_typeIds | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04a39af21ebb8a409656bd8b8ae0b4323da33c60
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155614"
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

out Restituisce il numero di `typeIds` scritti, o, se `typeIds` è `NULL` , il numero totale di identificatori di tipo disponibili.

 `typeIds[]`

out Matrice da compilare con gli identificatori di tipo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
