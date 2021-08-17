---
description: Recupera una matrice di tipi specifici del compilatore per questo simbolo.
title: IDiaSymbol::get_types | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e0dacb8d9fa997c3509015d1824d88ebf152863c461fad299906a235d4541f16
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391616"
---
# <a name="idiasymbolget_types"></a>IDiaSymbol::get_types
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

[in] Dimensioni del buffer per contenere i dati.

 `pcTypes`

[out] Restituisce il numero di tipi scritti oppure, se il `types` parametro è , il numero totale di tipi `NULL` disponibili.

 `types[]`

[out] Matrice che deve essere compilata con gli oggetti [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresentano tutti i tipi per questo simbolo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
