---
title: IDiaSymbol::get_types | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19642e6875e81220cb20109ce45e8dca40777a63
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2019
ms.locfileid: "64786570"
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
Recupera una matrice di tipi specifici del compilatore per questo simbolo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_types ( 
   DWORD       cTypes,
   DWORD*      pcTypes,
   IDiaSymbol* types[]
);
```

#### <a name="parameters"></a>Parametri
 `cTypes`

[in] Dimensione del buffer per contenere i dati.

 `pcTypes`

[out] Restituisce il numero di tipi scritti, oppure, se il `types` parametro è `NULL`, quindi il numero totale dei tipi disponibili.

 `types[]`

[out] Matrice che deve essere compilato con il [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) gli oggetti che rappresentano tutti i tipi per questo simbolo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)