---
title: DataKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bab3bc1c79b6444e75ab75e3d25e8bc395c1be86
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857321"
---
# <a name="datakind"></a>DataKind
Indica l'ambito specifico di un valore di dati.

## <a name="syntax"></a>Sintassi

```C++
enum DataKind {
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
Non è possibile determinare il simbolo di dati DataIsUnknown.

L'elemento dati DataIsLocal è una variabile locale.

L'elemento dati DataIsStaticLocal è una variabile locale statica.

L'elemento dati DataIsParam è un parametro formale.

L'elemento dati DataIsObjectPtr è un puntatore a oggetto ( `this` ).

L'elemento dati DataIsFileStatic è una variabile con ambito file.

L'elemento dati DataIsGlobal è una variabile globale.

L'elemento dati DataIsMember è una variabile membro oggetto.

L'elemento dati DataIsStaticMember è una variabile statica di classe.

L'elemento dati DataIsConstant è un valore costante.

## <a name="remarks"></a>Commenti
I valori di questa enumerazione vengono restituiti dal metodo [IDiaSymbol:: get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) .

## <a name="requirements"></a>Requisiti
Intestazione: cvconst. h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
