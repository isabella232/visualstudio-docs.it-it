---
title: 'IDiaSegment:: get_virtualAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_virtualAddress method
ms.assetid: 30073dd0-c864-4c4a-8863-80f243419f6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd06959a382c56a888d8d39da0c40b39a028ed28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465944"
---
# <a name="idiasegmentget_virtualaddress"></a>IDiaSegment::get_virtualAddress
Recupera l'indirizzo virtuale (VA) dell'inizio della sezione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_virtualAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce l'oggetto VA dell'inizio della sezione.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)