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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 707b22693afe83f82a30055f0c59ff89272b5bc3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862290"
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
