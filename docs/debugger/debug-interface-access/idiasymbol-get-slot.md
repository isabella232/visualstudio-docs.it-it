---
description: Recupera il numero di slot della posizione.
title: IDiaSymbol::get_slot | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_slot method
ms.assetid: 97e405b8-483f-4da0-91e7-ca4d88251ecd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7bd3fcbcba541ada2fabeff134fe600940a81fd9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161795"
---
# <a name="idiasymbolget_slot"></a>IDiaSymbol::get_slot
Recupera il numero di slot della posizione. Utilizzare quando l' [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md) è `LocIsSlot` .

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_slot ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce il numero di slot della posizione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)
