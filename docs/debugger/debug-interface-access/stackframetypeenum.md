---
description: Specifica il tipo di stack frame.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b84ad19ec31cd1fae65913827b8ee381711f6534
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155306"
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

## <a name="remarks"></a>Commenti
I valori di questa enumerazione vengono restituiti da una chiamata al metodo [IDiaStackFrame:: get_Type](../../debugger/debug-interface-access/idiastackframe-get-type.md) .

## <a name="requirements"></a>Requisiti
Intestazione: cvconst. h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
