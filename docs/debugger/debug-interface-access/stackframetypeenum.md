---
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 20b0c9dd106e5744a369ddaa6cb870788f7464d3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738549"
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
puntatore del frame di `FrameTypeFPO` omesso; Informazioni sulla Polinesia disponibili.

frame trap del kernel `FrameTypeTrap`.

frame trap del kernel `FrameTypeTSS`.

`FrameTypeStandard` stack frame EBP standard.

puntatore del frame di `FrameTypeFrameData` omesso; Informazioni sui dati dei frame disponibili.

`FrameTypeUnknown` frame privo di informazioni di debug.

## <a name="remarks"></a>Note
I valori di questa enumerazione vengono restituiti da una chiamata al metodo [IDiaStackFrame:: get_Type](../../debugger/debug-interface-access/idiastackframe-get-type.md) .

## <a name="requirements"></a>Requisiti
Intestazione: cvconst. h

## <a name="see-also"></a>Vedere anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
