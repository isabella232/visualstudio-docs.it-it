---
title: DiaAddressMapEntry | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: b472c52934353e6324d72077f8ea878467159cbd
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318641"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Descrive una voce in una mappa di indirizzo.

## <a name="syntax"></a>Sintassi

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>Elementi
`rva`  
Un indirizzo virtuale relativo (RVA) nell'immagine A.

`rvaTo`  
L'indirizzo virtuale relativo `rva` viene mappato a nella figura B.

## <a name="remarks"></a>Osservazioni
Una mappa indirizzo fornisce una conversione dal layout di un'immagine (A) in un'altra (B). Matrice di `DiaAddressMapEntry` strutture vengono ordinate `rva` definisce un mapping di indirizzi.

Per convertire un indirizzo `addrA`, nell'immagine A un indirizzo, `addrB`, nella figura B, eseguire la procedura seguente:

1. Eseguire la ricerca della mappa per la voce `e`, con la più grande `rva` minore o uguale a `addrA`.

2. Impostare `delta = addrA - e.rva`.

3. Impostare `addrB = e.rvaTo + delta`.

    Matrice di `DiaAddressMapEntry` strutture viene passato per il [Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) (metodo).

## <a name="requirements"></a>Requisiti
Intestazione: dia2.h

## <a name="see-also"></a>Vedere anche
[Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
