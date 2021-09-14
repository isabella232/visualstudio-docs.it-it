---
description: Recupera i simboli successivi in ordine in base all'indirizzo.
title: IDiaEnumSymbolsByAddr::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Next method
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b509c84c9ee0fe81a7c9532bbc6f218af277df5d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629994"
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
Recupera i simboli successivi in ordine in base all'indirizzo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Next ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>Parametri
 celt

[in] Numero di simboli nell'enumeratore da recuperare.

 Rgelt

[out] Matrice che deve essere compilata con [l'oggetto IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta i simboli desiderati.

 pceltFetched

[out] Restituisce il numero di simboli nell'enumeratore recuperato.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non sono presenti altri simboli. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo aggiorna la posizione dell'enumeratore in base al numero di elementi recuperati.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
