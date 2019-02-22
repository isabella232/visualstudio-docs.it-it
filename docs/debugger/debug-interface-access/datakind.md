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
ms.openlocfilehash: bf8e59bf79355b4e610091ac8662b8d2a01af322
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318680"
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
DataIsUnknown  
Non è possibile determinare il simbolo dei dati.

DataIsLocal  
Elemento dati è una variabile locale.

DataIsStaticLocal  
Elemento dati è una variabile locale statica.

DataIsParam  
Elemento dati è un parametro formale.

DataIsObjectPtr  
Elemento dati è un puntatore a oggetto (`this`).

DataIsFileStatic  
Elemento di dati è una variabile con ambito file.

DataIsGlobal  
Elemento dati è una variabile globale.

DataIsMember  
Elemento dati è una variabile membro oggetto.

DataIsStaticMember  
Elemento dati è una variabile di classe statici.

DataIsConstant  
Elemento dati è un valore costante.

## <a name="remarks"></a>Osservazioni
I valori di questa enumerazione vengono restituiti per il [Get_datakind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) (metodo).

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedere anche
[Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
