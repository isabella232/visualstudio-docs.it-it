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
ms.workload:
- multiple
ms.openlocfilehash: 7f111e269f0a61e827a6d1334aee8b9250f3f46f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155383"
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

`LocIsStatic` Il percorso è statico.

`LocIsTLS` Il percorso si trova nell'archiviazione thread-local.

`LocIsRegRel` Il percorso è relativo al registro.

`LocIsThisRel` Il percorso è `this` relativo.

`LocIsEnregistered` Il percorso si trova in un registro.

`LocIsBitField` Il percorso si trova in un campo di bit.

`LocIsSlot` Location è uno slot MSIL (Microsoft Intermediate Language).

`LocIsIlRel` Il percorso è relativo a MSIL.

`LocInMetaData` Il percorso è nei metadati.

`LocIsConstant` Il percorso è in un valore costante.

`LocTypeMax` Numero di tipi di posizione in questa enumerazione.

## <a name="remarks"></a>Commenti
Le proprietà disponibili per l'interfaccia [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) dipendono dalla posizione del simbolo all'interno del file di immagine. Per ulteriori informazioni, vedere [posizioni dei simboli](../../debugger/debug-interface-access/symbol-locations.md).

I valori di questa enumerazione vengono restituiti da una chiamata al metodo [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) .

## <a name="requirements"></a>Requisiti
Intestazione: cvconst. h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)
