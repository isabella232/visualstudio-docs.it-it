---
description: Specifica il tipo di memoria a cui accedere.
title: MemoryTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 557991a66f7e70dedcd7dad2a05d7e25fd0cd6b2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155369"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Specifica il tipo di memoria a cui accedere.

## <a name="syntax"></a>Sintassi

```C++
enum MemoryTypeEnum {
    MemTypeCode,
    MemTypeData,
    MemTypeStack,
    MemTypeAny = -1
};
```

#### <a name="parameters"></a>Parametri
`MemTypeCode` Accede solo alla memoria del codice.

`MemTypeData` Accede ai dati o alla memoria dello stack.

`MemTypeStack` Accede solo alla memoria dello stack.

`MemTypeAny` Accede a qualsiasi tipo di memoria.

## <a name="remarks"></a>Commenti
I valori di questa enumerazione vengono passati al metodo [IDiaStackWalkHelper:: ReadMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) per limitare l'accesso a diversi tipi di memoria.

## <a name="requirements"></a>Requisiti
Intestazione: cvconst. h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
