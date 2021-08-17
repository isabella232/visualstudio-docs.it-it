---
description: Indica il tipo di informazioni sulla posizione contenute in un simbolo.
title: LocationType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d68e541060c07a523af001558f2804eed35d498d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097636"
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
`LocIsNull` Le informazioni sulla posizione non sono disponibili.

`LocIsStatic` La posizione è statica.

`LocIsTLS` La posizione si trova nell'archiviazione locale dei thread.

`LocIsRegRel` La posizione è relativa al registro.

`LocIsThisRel` La posizione è `this` -relative.

`LocIsEnregistered` La posizione si trova in un registro.

`LocIsBitField` La posizione è in un campo di bit.

`LocIsSlot` Location è uno slot MSIL (Microsoft Intermediate Language).

`LocIsIlRel` La posizione è relativa a MSIL.

`LocInMetaData` La posizione è nei metadati.

`LocIsConstant` La posizione è in un valore costante.

`LocTypeMax` Numero di tipi di posizione in questa enumerazione.

## <a name="remarks"></a>Commenti
Le proprietà disponibili per [l'interfaccia IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) dipendono dalla posizione del simbolo all'interno del file di immagine. Per altre informazioni, vedere [Posizioni dei simboli](../../debugger/debug-interface-access/symbol-locations.md).

I valori in questa enumerazione vengono restituiti da una chiamata al [metodo IDiaSymbol::get_locationType.](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)
