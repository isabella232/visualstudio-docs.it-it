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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e26b5a7285c2e5c9135429777b4b58f35252e550
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162524"
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
