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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 891af8c8f6196fcafa8f623fa0fd81c44548b81c9a3294001312c2a7c6e341d1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420367"
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
I valori di questa enumerazione vengono passati al metodo [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) per limitare l'accesso a diversi tipi di memoria.

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
