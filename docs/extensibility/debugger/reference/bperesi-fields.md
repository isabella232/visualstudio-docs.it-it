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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34a12b0e86b5805e97a563374506962618bf7853
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145770"
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
Inizializzare/usare il `bpResLocation` campo (posizione di risoluzione del punto di interruzione) [della BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struttura .

`BPERESI_PROGRAM`\
Inizializzare/usare `pProgram` il campo della struttura `BP_ERROR_RESOLUTION_INFO` .

`BPERESI_THREAD`\
Inizializzare/usare `pThread` il campo della struttura `BP_ERROR_RESOLUTION_INFO` .

`BPERESI_MESSAGE`\
Inizializzare/usare `bstrMessage` il campo della struttura `BP_ERROR_RESOLUTION_INFO` .

`BPERESI_TYPE`\
Inizializzare/usare il `dwType` campo (tipo di punto di interruzione) della `BP_ERROR_RESOLUTION_INFO` struttura .

`BPERESI_ALLFIELDS`\
Inizializzare/usare tutti i campi della `BP_ERROR_RESOLUTION_INFO` struttura .

## <a name="remarks"></a>Commenti
Passato come parametro al [metodo GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) per indicare quali campi della [struttura](../../../extensibility/debugger/reference/bp-error-resolution-info.md) BP_ERROR_RESOLUTION_INFO devono essere inizializzati.

Questi valori vengono usati anche per indicare quali campi della struttura vengono usati e `BP_ERROR_RESOLUTION_INFO` validi quando viene restituita tale struttura.

Questi valori possono essere combinati con un bit per `OR` bit.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
