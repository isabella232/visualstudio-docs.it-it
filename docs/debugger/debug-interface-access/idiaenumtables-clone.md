---
title: 'IDiaEnumTables:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Clone method
ms.assetid: beb21109-b12c-44d8-8c1f-a332216b3713
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68727c09b03ba8cf53f865c51698256b60742410
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467575"
---
# <a name="idiaenumtablesclone"></a>IDiaEnumTables::Clone
Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Clone ( 
   IDiaEnumTables** ppenum
);
```

#### <a name="parameters"></a>Parametri
 `ppenum`

out Restituisce un oggetto [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) che contiene un duplicato dell'enumeratore. Le tabelle non vengono duplicate, ma solo l'enumeratore.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)