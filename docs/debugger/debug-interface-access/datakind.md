---
title: DataKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21630bea3022769d18748190c2a2d24c0e519a3c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554922"
---
# <a name="datakind"></a>DataKind
Indica l'ambito specifico di un valore di dati.

## <a name="syntax"></a>Sintassi

```C++
enum DataKind {
    DataIsUnknown,
    DataIsLocal,
    DataIsStaticLocal,
    DataIsParam,
    DataIsObjectPtr,
    DataIsFileStatic,
    DataIsGlobal,
    DataIsMember,
    DataIsStaticMember,
    DataIsConstant
};
```

## <a name="elements"></a>Elementi
Non è possibile determinare il simbolo DataIsUnknown dei dati.

Elemento dati DataIsLocal è una variabile locale.

Elemento dati DataIsStaticLocal è una variabile locale statica.

Elemento dati DataIsParam è un parametro formale.

Elemento dati DataIsObjectPtr è un puntatore a oggetto (`this`).

Elemento dati DataIsFileStatic è una variabile con ambito file.

Elemento dati DataIsGlobal è una variabile globale.

Elemento dati DataIsMember è una variabile membro oggetto.

Elemento dati DataIsStaticMember è una variabile di classe statici.

Elemento dati DataIsConstant è un valore costante.

## <a name="remarks"></a>Note
I valori di questa enumerazione vengono restituiti per il [Get_datakind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) (metodo).

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedere anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
