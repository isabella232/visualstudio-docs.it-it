---
description: Recupera i simboli precedenti nell'ordine in base all'indirizzo.
title: IDiaEnumSymbolsByAddr::Prev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 721eaf80e0bd7121d9e8286315b63422edbb745d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148640"
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
Recupera i simboli precedenti nell'ordine in base all'indirizzo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Prev ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>Parametri
 celt

in Numero di simboli nell'enumeratore da recuperare.

 rgelt

out Matrice che deve essere compilata con gli oggetti [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresentano i simboli desiderati.

 pceltFetched

out Restituisce il numero di simboli nell'enumeratore recuperato.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non sono presenti simboli precedenti. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo aggiorna la posizione dell'enumeratore in base al numero di elementi recuperati.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
