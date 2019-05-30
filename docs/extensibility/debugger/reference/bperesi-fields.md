---
title: BPERESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f9db96713ba8bb0f3cd421c48ef602e25c2d25a1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350527"
---
# <a name="bperesifields"></a>BPERESI_FIELDS
Specifica le informazioni da recuperare su una risoluzione non riuscita di un punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
typedef DWORD BPERESI_FIELDS;
```

```csharp
public enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Campi
`PERESI_BPRESLOCATION`\
Initialize/usare la `bpResLocation` campo (punto di interruzione risoluzione percorso) della finestra di [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struttura.

`BPERESI_PROGRAM`\
Initialize/usare la `pProgram` campo il `BP_ERROR_RESOLUTION_INFO` struttura.

`BPERESI_THREAD`\
Initialize/usare la `pThread` campo il `BP_ERROR_RESOLUTION_INFO` struttura.

`BPERESI_MESSAGE`\
Initialize/usare la `bstrMessage` campo il `BP_ERROR_RESOLUTION_INFO` struttura.

`BPERESI_TYPE`\
Initialize/usare la `dwType` valore del campo (tipo di punto di interruzione) il `BP_ERROR_RESOLUTION_INFO` struttura.

`BPERESI_ALLFIELDS`\
Tutti i campi di inizializzazione/usare la `BP_ERROR_RESOLUTION_INFO` struttura.

## <a name="remarks"></a>Note
Passato come parametro per il [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) metodo per indicare quali campi della [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struttura devono essere inizializzate.

Questi valori vengono usati anche per indicare quali campi nel `BP_ERROR_RESOLUTION_INFO` struttura siano usati e validi quando viene restituita tale struttura.

Questi valori possono essere combinati con un bit per bit `OR`.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
