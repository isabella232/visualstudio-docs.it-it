---
description: Descrive la varietà di tipi definiti dall'utente (UDT).
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
ms.openlocfilehash: dbda75e668309318c4c4fe61c5c72f27629ea2cc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155278"
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
