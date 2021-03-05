---
description: Specifica le informazioni da recuperare su un contesto di memoria.
title: CONTEXT_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 401195d5b03f87ba1ea5c66811570a720e53bdae
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170770"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
Specifica le informazioni da recuperare su un contesto di memoria.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
typedef DWORD CONTEXT_INFO_FIELDS;
```

```csharp
public enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
```

## <a name="fields"></a>Campi
`CIF_MODULEURL`\
Inizializza/usa il `bstrModuleUrl` campo della struttura [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) .

`CIF_FUNCTION`\
Inizializza/usa il `bstrFunction` campo della `CONTEXT_INFO` struttura.

`CIF_FUNCTIONOFFSET`\
Inizializza/usa il `posFunctionOffset` campo della `CONTEXT_INFO` struttura.

`CIF_ADDRESS`\
Inizializza/usa il `bstrAddress` campo della `CONTEXT_INFO` struttura.

`CIF_ADDRESSOFFSET`\
Inizializza/usa il `bstrAddressOffset` campo della `CONTEXT_INFO` struttura.

`CIF_ALLFIELDS`\
Inizializza/usa tutti i campi della `CONTEXT_INFO` struttura.

## <a name="remarks"></a>Commenti
A questi valori viene passato un parametro al metodo [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) per indicare quali campi della struttura [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) devono essere inizializzati.

Questi flag vengono usati anche per indicare quali campi della `CONTEXT_INFO` struttura vengono usati e validi quando viene restituita la struttura.

Questi valori possono essere combinati con un OR bit per bit.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
