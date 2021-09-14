---
description: Recupera l'indirizzo RVA (Relative Virtual Address) dell'inizio della sezione.
title: IDiaSegment::get_relativeVirtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_relativeVirtualAddress method
ms.assetid: b6a573a1-3671-4c1c-a5c2-2ab8f07fd510
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a00183c422de17dcf46ec1bec763c7dedb0c0524
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629297"
---
# <a name="idiasegmentget_relativevirtualaddress"></a>IDiaSegment::get_relativeVirtualAddress
Recupera l'indirizzo RVA (Relative Virtual Address) dell'inizio della sezione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_relativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce l'RVA dell'inizio della sezione.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
