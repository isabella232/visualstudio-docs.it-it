---
title: MemoryTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0710ec5cdfcfcb59407d18b43b885603f017fdb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738624"
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
`MemTypeCode` accede solo alla memoria del codice.

`MemTypeData` accede ai dati o alla memoria dello stack.

`MemTypeStack` accede solo alla memoria dello stack.

`MemTypeAny` accede a qualsiasi tipo di memoria.

## <a name="remarks"></a>Note
I valori di questa enumerazione vengono passati al metodo [IDiaStackWalkHelper:: ReadMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) per limitare l'accesso a diversi tipi di memoria.

## <a name="requirements"></a>Requisiti
Intestazione: cvconst. h

## <a name="see-also"></a>Vedere anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
