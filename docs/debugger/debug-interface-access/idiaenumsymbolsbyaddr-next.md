---
title: IDiaEnumSymbolsByAddr::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Next method
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 424924f3fab62cf862420d58c947bba16343141d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743888"
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
Recupera i simboli successivi nell'ordine in base all'indirizzo.

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

in Numero di simboli nell'enumeratore da recuperare.

 rgelt

out Matrice che deve essere compilata con l'oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta i simboli desiderati.

 pceltFetched

out Restituisce il numero di simboli nell'enumeratore recuperato.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non sono presenti altri simboli. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo aggiorna la posizione dell'enumeratore in base al numero di elementi recuperati.

## <a name="see-also"></a>Vedere anche
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)