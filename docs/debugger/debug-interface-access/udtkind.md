---
title: UdtKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb649915179bc6e6b767970150df99caff306b4c
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317731"
---
# <a name="udtkind"></a>UdtKind
Descrive la varietà di tipo definito dall'utente (UDT).

## <a name="syntax"></a>Sintassi

```C++
enum UdtKind {
    UdtStruct,
    UdtClass,
    UdtUnion,
    UdtInterface
};
```

## <a name="elements"></a>Elementi
UdtStruct  
Tipo definito dall'utente è una struttura.

UdtClass  
Tipo definito dall'utente è una classe.

UdtUnion  
Tipo definito dall'utente è un'unione.

UdtInterface  
Tipo definito dall'utente è un'interfaccia.

## <a name="remarks"></a>Osservazioni
I valori di questa enumerazione vengono restituiti per il [Get_udtkind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) (metodo).

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedere anche
[Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
