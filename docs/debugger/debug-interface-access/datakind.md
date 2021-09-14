---
description: Indica l'ambito specifico di un valore di dati.
title: Oggetto DataKind | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: fbf8d7f40f1cd3c14bd6b830a65526921f1c6ece
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630653"
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
Impossibile determinare il simbolo dataIsUnknown Data.

DataIsLocal Data è una variabile locale.

DataIsStaticLocal Data è una variabile locale statica.

Elemento di dati DataIsParam è un parametro formale.

L'elemento di dati DataIsObjectPtr è un puntatore a oggetto ( `this` ).

Elemento di dati DataIsFileStatic è una variabile con ambito file.

DataIsGlobal Data item è una variabile globale.

Elemento di dati DataIsMember è una variabile membro dell'oggetto.

Elemento di dati DataIsStaticMember è una variabile statica di classe.

DataIsConstant Data item è un valore costante.

## <a name="remarks"></a>Commenti
I valori di questa enumerazione vengono restituiti dal [metodo IDiaSymbol::get_dataKind.](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
