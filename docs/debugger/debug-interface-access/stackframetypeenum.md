---
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f83cdb163881366a1a0bede95a07e1dae1fc50a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85461098"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Specifica il tipo di stack frame.

## <a name="syntax"></a>Sintassi

```C++
enum StackFrameTypeEnum {
    FrameTypeFPO,
    FrameTypeTrap,
    FrameTypeTSS,
    FrameTypeStandard,
    FrameTypeFrameData,
    FrameTypeUnknown = -1
};
```

## <a name="elements"></a>Elementi
`FrameTypeFPO` Puntatore al frame omesso; Informazioni sulla Polinesia disponibili.

`FrameTypeTrap` Frame trap del kernel.

`FrameTypeTSS` Frame trap del kernel.

`FrameTypeStandard` Stack frame EBP standard.

`FrameTypeFrameData` Puntatore al frame omesso; Informazioni sui dati dei frame disponibili.

`FrameTypeUnknown` Frame senza informazioni di debug.

## <a name="remarks"></a>Osservazioni
I valori di questa enumerazione vengono restituiti da una chiamata al metodo [IDiaStackFrame:: get_Type](../../debugger/debug-interface-access/idiastackframe-get-type.md) .

## <a name="requirements"></a>Requisiti
Intestazione: cvconst. h

## <a name="see-also"></a>Vedere anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
