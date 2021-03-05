---
description: Descrive una voce in una mappa indirizzi.
title: DiaAddressMapEntry | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bdac0233901ac8571bbfb2a5d6659adf69e35298
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149193"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Descrive una voce in una mappa indirizzi.

## <a name="syntax"></a>Sintassi

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>Elementi
`rva` Un indirizzo RVA (relativo Virtual Address) nell'immagine A.

`rvaTo` Viene eseguito il mapping dell'indirizzo virtuale relativo `rva` a nell'immagine B.

## <a name="remarks"></a>Commenti
Una mappa indirizzi fornisce una traduzione da un layout immagine (A) a un altro (B). Una matrice di `DiaAddressMapEntry` strutture ordinate in base a `rva` definisce una mappa degli indirizzi.

Per tradurre un indirizzo,, `addrA` nell'immagine a in un indirizzo, `addrB` , nell'immagine B, seguire questa procedura:

1. Eseguire una ricerca nella mappa per la voce, `e` , con il più grande `rva` minore o uguale a `addrA` .

2. Impostare `delta = addrA - e.rva`.

3. Impostare `addrB = e.rvaTo + delta`.

    Una matrice di `DiaAddressMapEntry` strutture viene passata al metodo [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .

## <a name="requirements"></a>Requisiti
Intestazione: dia2. h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
