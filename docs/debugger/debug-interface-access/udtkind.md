---
description: Descrive l'ampia gamma di tipi definiti dall'utente (UDT).
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
ms.openlocfilehash: a8f9a065ceb5fce06f01c1e64c6d5acf48959539
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052165"
---
# <a name="udtkind"></a>UdtKind
Descrive l'ampia gamma di tipi definiti dall'utente (UDT).

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
I valori in questa enumerazione vengono restituiti dal [metodo IDiaSymbol::get_udtKind.](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
