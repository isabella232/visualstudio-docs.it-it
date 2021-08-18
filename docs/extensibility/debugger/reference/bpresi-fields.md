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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d47be3c63724b18b92fac9d253878b25c72c68dc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120218"
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
Inizializzare/usare il campo (posizione di risoluzione del punto di `bpResLocation` [interruzione) della BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) struttura .

`BPRESI_PROGRAM`\
Inizializzare/usare `pProgram` il campo della struttura `BP_RESOLUTION_INFO` .

`BPRESI_THREAD`\
Inizializzare/usare `pThread` il campo della struttura `BP_RESOLUTION_INFO` .

`BPRESI_ALLFIELDS`\
Specifica tutti i campi.

## <a name="remarks"></a>Commenti
Passato al [metodo GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) per indicare quali campi della [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) devono essere inizializzati.

Questi flag vengono usati anche per indicare quali campi della struttura vengono usati e `BP_RESOLUTION_INFO` validi quando tale struttura viene restituita.

Questi valori possono essere combinati con un oggetto bit per `OR` bit.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
