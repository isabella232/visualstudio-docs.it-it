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
ms.openlocfilehash: dab674576655df3b4a695d97fdfdb42df2ffa449
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227264"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Specifica il tipo di frame dello stack.

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
`FrameTypeFPO`  
Puntatore ai frame omessi. Info FPO disponibile.

`FrameTypeTrap`  
Frame Trap kernel.

`FrameTypeTSS`  
Frame Trap kernel.

`FrameTypeStandard`  
Frame dello stack EBP standard.

`FrameTypeFrameData`  
Puntatore ai frame omessi. Informazioni sui dati di intervallo disponibile.

`FrameTypeUnknown`  
Frame che non ha le informazioni di debug.

## <a name="remarks"></a>Osservazioni
I valori di questa enumerazione vengono restituiti da una chiamata per il [Idiastackframe](../../debugger/debug-interface-access/idiastackframe-get-type.md) (metodo).

## <a name="requirements"></a>Requisiti
Intestazione: cvconst.h

## <a name="see-also"></a>Vedere anche
[Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
