---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e03c01efb9f2dca13009a7dc7eeb8282b5c9082c
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468044"
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