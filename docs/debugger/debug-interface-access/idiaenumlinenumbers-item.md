---
description: Recupera un numero di riga tramite un indice.
title: IDiaEnumLineNumbers::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Item method
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e49593578efb94feb9fc5f9da2152b9008a4d8ba
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630234"
---
# <a name="idiaenumlinenumbersitem"></a>IDiaEnumLineNumbers::Item
Recupera un numero di riga tramite un indice.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Item ( 
   DWORD            index,
   IDiaLineNumber** lineNumber
);
```

#### <a name="parameters"></a>Parametri
 index

[in] Indice [dell'oggetto IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) da recuperare. L'indice è compreso nell'intervallo da 0 a -1, dove viene restituito dal metodo `count` `count` [IDiaEnumLineNumbers::get_Count.](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md)

 lineNumber

[out] Restituisce un [oggetto IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) che rappresenta il numero di riga desiderato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
