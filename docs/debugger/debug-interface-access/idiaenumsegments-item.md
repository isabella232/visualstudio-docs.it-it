---
description: Recupera un segmento per mezzo di un indice.
title: 'IDiaEnumSegments:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a8714964bdf2e267e9f9c047fb1878655e58f489
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148850"
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
Recupera un segmento per mezzo di un indice.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Item ( 
   DWORD         index,
   IDiaSegment** segment
);
```

#### <a name="parameters"></a>Parametri
 indice

in Indice dell'oggetto [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) da recuperare. L'indice è compreso nell'intervallo tra 0 e `count` -1, dove `count` viene restituito dal metodo [IDiaEnumSegments:: get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md) .

 segment

out Restituisce un oggetto [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) che rappresenta il segmento desiderato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
