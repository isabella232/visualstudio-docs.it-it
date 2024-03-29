---
description: Specifica il tipo stack frame dati.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 400a1db1f8a5ee5ffde7e00a428d83d170dc0d05
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097599"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Specifica il tipo stack frame dati.

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
`FrameTypeFPO` Puntatore ai frame omesso; Informazioni FPO disponibili.

`FrameTypeTrap` Frame trap kernel.

`FrameTypeTSS` Frame trap kernel.

`FrameTypeStandard` Standard EBP stack frame.

`FrameTypeFrameData` Puntatore ai frame omesso; Informazioni sui dati dei frame disponibili.

`FrameTypeUnknown` Frame senza informazioni di debug.

## <a name="remarks"></a>Commenti
I valori in questa enumerazione vengono restituiti da una chiamata al [metodo IDiaStackFrame::get_type.](../../debugger/debug-interface-access/idiastackframe-get-type.md)

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedi anche
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
