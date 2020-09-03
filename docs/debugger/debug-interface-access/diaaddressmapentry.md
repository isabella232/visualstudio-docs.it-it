---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cae8159c893229f02e9598e932d7bc19efc2f4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468679"
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

## <a name="remarks"></a>Osservazioni
Una mappa indirizzi fornisce una traduzione da un layout immagine (A) a un altro (B). Una matrice di `DiaAddressMapEntry` strutture ordinate in base a `rva` definisce una mappa degli indirizzi.

Per tradurre un indirizzo,, `addrA` nell'immagine a in un indirizzo, `addrB` , nell'immagine B, seguire questa procedura:

1. Eseguire una ricerca nella mappa per la voce, `e` , con il più grande `rva` minore o uguale a `addrA` .

2. Impostare `delta = addrA - e.rva`.

3. Impostare `addrB = e.rvaTo + delta`.

    Una matrice di `DiaAddressMapEntry` strutture viene passata al metodo [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .

## <a name="requirements"></a>Requisiti
Intestazione: dia2. h

## <a name="see-also"></a>Vedere anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
