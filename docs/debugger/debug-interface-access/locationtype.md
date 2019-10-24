---
title: LocationType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc40cc6cc8e821db7c28a4647e36e7bad241b29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738640"
---
# <a name="locationtype"></a>LocationType
Indica il tipo di informazioni sulla posizione contenute in un simbolo.

## <a name="syntax"></a>Sintassi

```C++
enum LocationType {
    LocIsNull,
    LocIsStatic,
    LocIsTLS,
    LocIsRegRel,
    LocIsThisRel,
    LocIsEnregistered,
    LocIsBitField,
    LocIsSlot,
    LocIsIlRel,
    LocInMetaData,
    LocIsConstant,
    LocTypeMax
};
```

## <a name="elements"></a>Elementi
le informazioni sul percorso `LocIsNull` non sono disponibili.

il percorso del `LocIsStatic` è statico.

il percorso del `LocIsTLS` è nell'archiviazione thread-local.

`LocIsRegRel` percorso è relativo al registro.

il percorso `LocIsThisRel` è relativo `this`.

il percorso `LocIsEnregistered` si trova in un registro.

il percorso del `LocIsBitField` è in un campo di bit.

`LocIsSlot` percorso è uno slot Microsoft Intermediate Language (MSIL).

`LocIsIlRel` percorso è relativo a MSIL.

il percorso del `LocInMetaData` è nei metadati.

il percorso del `LocIsConstant` è in un valore costante.

`LocTypeMax` il numero di tipi di posizione in questa enumerazione.

## <a name="remarks"></a>Note
Le proprietà disponibili per l'interfaccia [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) dipendono dalla posizione del simbolo all'interno del file di immagine. Per ulteriori informazioni, vedere [posizioni dei simboli](../../debugger/debug-interface-access/symbol-locations.md).

I valori di questa enumerazione vengono restituiti da una chiamata al metodo [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) .

## <a name="requirements"></a>Requisiti
Intestazione: cvconst. h

## <a name="see-also"></a>Vedere anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)
