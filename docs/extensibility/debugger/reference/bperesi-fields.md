---
title: proprietà BPERESI_FIELDS . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af2f20e7d3abd79261dc18753a7eb940666fc186
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737762"
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
Inizializzare/utilizzare `bpResLocation` il campo (posizione di risoluzione dei punti di interruzione) della struttura [BP_ERROR_RESOLUTION_INFO.](../../../extensibility/debugger/reference/bp-error-resolution-info.md)

`BPERESI_PROGRAM`\
Inizializzare/utilizzare `pProgram` il `BP_ERROR_RESOLUTION_INFO` campo della struttura.

`BPERESI_THREAD`\
Inizializzare/utilizzare `pThread` il `BP_ERROR_RESOLUTION_INFO` campo della struttura.

`BPERESI_MESSAGE`\
Inizializzare/utilizzare `bstrMessage` il `BP_ERROR_RESOLUTION_INFO` campo della struttura.

`BPERESI_TYPE`\
Inizializzare/utilizzare `dwType` il campo (tipo `BP_ERROR_RESOLUTION_INFO` di punto di interruzione) della struttura.

`BPERESI_ALLFIELDS`\
Inizializzare/utilizzare tutti `BP_ERROR_RESOLUTION_INFO` i campi della struttura.

## <a name="remarks"></a>Osservazioni
Passato come parametro al metodo [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) per indicare i campi della struttura [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) devono essere inizializzati.

Questi valori vengono utilizzati anche `BP_ERROR_RESOLUTION_INFO` per indicare quali campi nella struttura vengono utilizzati e validi quando tale struttura viene restituita.

Questi valori possono essere combinati `OR`con un oggetto .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
