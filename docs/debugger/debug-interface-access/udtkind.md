---
description: Viene descritta l'ampia gamma di tipi definiti dall'utente (UDT).
title: UdtKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a4b3ae98b911b7e5a7026740afe574044a49fdf5d8b8b96be05f2e4546cbdb4e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391568"
---
# <a name="udtkind"></a>UdtKind
Viene descritta l'ampia gamma di tipi definiti dall'utente (UDT).

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
UdtStruct UDT è una struttura.

UdtClass UDT è una classe.

UdtUnion UDT è un'unione.

UdtInterface UDT è un'interfaccia.

## <a name="remarks"></a>Commenti
I valori di questa enumerazione vengono restituiti dal [metodo IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) .

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
