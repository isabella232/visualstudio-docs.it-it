---
title: 'IDiaEnumTables:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 688652fe3915e1974d5d0e1d04fb1ac075863d8c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743737"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
Recupera un numero specificato di tabelle nella sequenza di enumerazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Next ( 
   ULONG       celt,
   IDiaTable** rgelt,
   ULONG*      pceltFetched
);
```

#### <a name="parameters"></a>Parametri
 `celt`

in Numero di tabelle nell'enumeratore da recuperare.

 `rgelt`

out Matrice che deve essere compilata con gli oggetti [IDiaTable](../../debugger/debug-interface-access/idiatable.md) che rappresentano le tabelle desiderate.

 `pceltFetched`

out Restituisce il numero di tabelle nell'enumeratore recuperato.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se non sono presenti altre tabelle. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)