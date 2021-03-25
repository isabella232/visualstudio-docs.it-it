---
description: Specifica le informazioni da recuperare su una risoluzione non riuscita di un punto di interruzione.
title: BPERESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8164f377e56c884149fb0711286d7702fe92eb82
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067686"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
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
Inizializzare/utilizzare il `bpResLocation` campo (percorso risoluzione punto di interruzione) della struttura [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) .

`BPERESI_PROGRAM`\
Inizializza/usa il `pProgram` campo della `BP_ERROR_RESOLUTION_INFO` struttura.

`BPERESI_THREAD`\
Inizializza/usa il `pThread` campo della `BP_ERROR_RESOLUTION_INFO` struttura.

`BPERESI_MESSAGE`\
Inizializza/usa il `bstrMessage` campo della `BP_ERROR_RESOLUTION_INFO` struttura.

`BPERESI_TYPE`\
Inizializza/usa il `dwType` campo (tipo di punto di interruzione) della `BP_ERROR_RESOLUTION_INFO` struttura.

`BPERESI_ALLFIELDS`\
Inizializza/usa tutti i campi della `BP_ERROR_RESOLUTION_INFO` struttura.

## <a name="remarks"></a>Commenti
Passato come parametro al metodo [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) per indicare quali campi della struttura [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) devono essere inizializzati.

Questi valori vengono usati anche per indicare quali campi della `BP_ERROR_RESOLUTION_INFO` struttura vengono usati e validi quando viene restituita tale struttura.

Questi valori possono essere combinati con un bit per bit `OR` .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
