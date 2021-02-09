---
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
ms.workload:
- multiple
ms.openlocfilehash: 44c543d09a360bfb7eadad11d7fca84764bb2006
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873394"
---
# <a name="udtkind"></a>UdtKind
Descrive la varietà di tipi definiti dall'utente (UDT).

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
Il tipo definito dall'utente UdtStruct è una struttura.

Il tipo definito dall'utente UdtClass è una classe.

Il tipo definito dall'utente UdtUnion è un'Unione.

Il tipo definito dall'utente UdtInterface è un'interfaccia.

## <a name="remarks"></a>Commenti
I valori di questa enumerazione vengono restituiti dal metodo [IDiaSymbol:: get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) .

## <a name="requirements"></a>Requisiti
Intestazione: cvconst. h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
