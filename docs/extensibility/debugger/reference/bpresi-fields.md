---
title: BPRESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82a286bea92c778ab150cacdc80d79f8ac283469
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350476"
---
# <a name="bpresifields"></a>BPRESI_FIELDS
Specifica le informazioni da recuperare sulla corretta risoluzione di un punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
typedef DWORD BPRESI_FIELDS;
```

```csharp
public enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
```

## <a name="fields"></a>Campi
`BPRESI_BPRESLOCATION`\
Initialize/usare la `bpResLocation` campo (punto di interruzione risoluzione percorso) della finestra di [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) struttura.

`BPRESI_PROGRAM`\
Initialize/usare la `pProgram` campo il `BP_RESOLUTION_INFO` struttura.

`BPRESI_THREAD`\
Initialize/usare la `pThread` campo il `BP_RESOLUTION_INFO` struttura.

`BPRESI_ALLFIELDS`\
Specifica tutti i campi.

## <a name="remarks"></a>Note
Passato per il [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) metodo per indicare quali campi della [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) struttura devono essere inizializzate.

Questi flag vengono usanti anche per indicare quali campi del `BP_RESOLUTION_INFO` struttura siano usati e validi quando viene restituita tale struttura.

Questi valori possono essere combinati con un bit per bit `OR`.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
