---
description: Recupera un segmento tramite un indice.
title: IDiaEnumSegments::Item | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 454f79260201fcf9929f85d53aa5d9a4699c7b55
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630143"
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
Recupera un segmento tramite un indice.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Item ( 
   DWORD         index,
   IDiaSegment** segment
);
```

#### <a name="parameters"></a>Parametri
 index

[in] Indice [dell'oggetto IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) da recuperare. L'indice è compreso nell'intervallo da 0 a -1, dove viene restituito dal metodo `count` `count` [IDiaEnumSegments::get_Count.](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)

 segment

[out] Restituisce un [oggetto IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) che rappresenta il segmento desiderato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
