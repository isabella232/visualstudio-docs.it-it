---
description: Specifica se il punto di interruzione si trova in una posizione del codice, è un percorso dati o è un altro tipo di punto di interruzione.
title: BP_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_TYPE
helpviewer_keywords:
- BP_TYPE enumeration
ms.assetid: ef07191e-7966-43ab-96fb-1a0b1db3115d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15f4cd96377ea76db064e5a1eda6f0f9d35ef902
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635212"
---
# <a name="bp_type"></a>BP_TYPE
Specifica se il punto di interruzione si trova in una posizione del codice, è un percorso dati o è un altro tipo di punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
typedef DWORD BP_TYPE;
```

```csharp
public enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
```

## <a name="fields"></a>Campi
`BPT_NONE`\
Non specifica alcun tipo di punto di interruzione.

`BPT_CODE`\
Specifica un punto di interruzione del codice.

`BPT_DATA`\
Specifica un punto di interruzione dei dati.

`BPT_SPECIAL`\
Specifica un punto di interruzione che non è né un codice né un tipo di dati. Questo tipo è deprecato e non deve essere usato.

## <a name="remarks"></a>Commenti
Passato come parametro ai [metodi GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) [e GetBreakpointType.](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)
