---
description: Recupera un flag che specifica se il simbolo pubblico fa riferimento a una funzione.
title: IDiaSymbol::get_function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_function method
ms.assetid: 48b3a318-3211-410f-8570-c02ee210f0a5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c436777b8a84bc16e7356805aa2faedc2e18e5a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162138"
---
# <a name="idiasymbolget_function"></a>IDiaSymbol::get_function
Recupera un flag che specifica se il simbolo pubblico fa riferimento a una funzione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_function ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce un oggetto `TRUE` se il simbolo fa riferimento a una funzione; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
