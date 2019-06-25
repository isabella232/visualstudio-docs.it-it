---
title: IDiaSegment::get_relativeVirtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_relativeVirtualAddress method
ms.assetid: b6a573a1-3671-4c1c-a5c2-2ab8f07fd510
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e6387b4e7cbf3ab100b641fe8694505c5e326fc8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827677"
---
# <a name="idiasegmentgetrelativevirtualaddress"></a>IDiaSegment::get_relativeVirtualAddress
Recupera l'indirizzo virtuale relativo (RVA) dell'inizio della sezione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_relativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce il RVA dell'inizio della sezione.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)