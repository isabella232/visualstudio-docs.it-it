---
description: Specifica le informazioni da recuperare sulla risoluzione corretta di un punto di interruzione.
title: BPRESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91fa2a8b973149cb9365d817e14ac877bfc9f617
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171031"
---
# <a name="bpresi_fields"></a>BPRESI_FIELDS
Specifica le informazioni da recuperare sulla risoluzione corretta di un punto di interruzione.

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
Inizializzare/utilizzare il `bpResLocation` campo (percorso risoluzione punto di interruzione) della struttura [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) .

`BPRESI_PROGRAM`\
Inizializza/usa il `pProgram` campo della `BP_RESOLUTION_INFO` struttura.

`BPRESI_THREAD`\
Inizializza/usa il `pThread` campo della `BP_RESOLUTION_INFO` struttura.

`BPRESI_ALLFIELDS`\
Specifica tutti i campi.

## <a name="remarks"></a>Commenti
Passato al metodo [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) per indicare quali campi della struttura [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) devono essere inizializzati.

Questi flag vengono usati anche per indicare quali campi della `BP_RESOLUTION_INFO` struttura vengono usati e validi quando viene restituita tale struttura.

Questi valori possono essere combinati con un bit per bit `OR` .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
