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
ms.openlocfilehash: 54b326116b1e1b677a997b264cf0c168a93febb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745257"
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
`rva` un indirizzo RVA (relativo Virtual Address) nell'immagine A.

`rvaTo` l'indirizzo virtuale relativo `rva` è mappato a nell'immagine B.

## <a name="remarks"></a>Note
Una mappa indirizzi fornisce una traduzione da un layout immagine (A) a un altro (B). Una matrice di strutture di `DiaAddressMapEntry` ordinate per `rva` definisce una mappa degli indirizzi.

Per tradurre un indirizzo, `addrA` nell'immagine a in un indirizzo `addrB`, nell'immagine B, seguire questa procedura:

1. Eseguire una ricerca nella mappa per la voce `e`, con il `rva` più grande minore o uguale a `addrA`.

2. Impostare `delta = addrA - e.rva`.

3. Impostare `addrB = e.rvaTo + delta`.

    Una matrice di strutture di `DiaAddressMapEntry` viene passata al metodo [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .

## <a name="requirements"></a>Requisiti
Intestazione: dia2. h

## <a name="see-also"></a>Vedere anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
