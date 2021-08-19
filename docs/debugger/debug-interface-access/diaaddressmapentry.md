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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4c5ac207ec1fc66554264d14f2aa9f0dccbb3773
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036680"
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
`rva` Indirizzo virtuale relativo (RVA) nell'immagine A.

`rvaTo` L'indirizzo virtuale relativo `rva` viene mappato a nell'immagine B.

## <a name="remarks"></a>Commenti
Una mappa indirizzi fornisce una traduzione da un layout di immagine (A) a un altro (B). Una matrice di `DiaAddressMapEntry` strutture ordinate per `rva` definisce una mappa indirizzi.

Per convertire un indirizzo, `addrA` , nell'immagine A in un `addrB` indirizzo, nell'immagine B, seguire questa procedura:

1. Cercare nella mappa la voce `e` , con il valore più grande minore o uguale a `rva` `addrA` .

2. Impostare `delta = addrA - e.rva`.

3. Impostare `addrB = e.rvaTo + delta`.

    Una matrice di `DiaAddressMapEntry` strutture viene passata al [metodo IDiaAddressMap::set_addressMap.](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)

## <a name="requirements"></a>Requisiti
Intestazione: dia2.h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
