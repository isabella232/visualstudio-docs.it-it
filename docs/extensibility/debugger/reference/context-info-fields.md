---
title: CONTEXT_INFO_FIELDS . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b398e7ee549026750cbdff7b7fede8522116f346
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737600"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
Specifica le informazioni da recuperare su un contesto di memoria.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_CONTEXT_INFO_FIELDS {
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
Inizializzare/utilizzare `bstrModuleUrl` il campo della [struttura CONTEXT_INFO.](../../../extensibility/debugger/reference/context-info.md)

`CIF_FUNCTION`\
Inizializzare/utilizzare `bstrFunction` il `CONTEXT_INFO` campo della struttura.

`CIF_FUNCTIONOFFSET`\
Inizializzare/utilizzare `posFunctionOffset` il `CONTEXT_INFO` campo della struttura.

`CIF_ADDRESS`\
Inizializzare/utilizzare `bstrAddress` il `CONTEXT_INFO` campo della struttura.

`CIF_ADDRESSOFFSET`\
Inizializzare/utilizzare `bstrAddressOffset` il `CONTEXT_INFO` campo della struttura.

`CIF_ALLFIELDS`\
Inizializzare/utilizzare tutti `CONTEXT_INFO` i campi della struttura.

## <a name="remarks"></a>Osservazioni
A questi valori viene passato un parametro al metodo [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) per indicare i campi della struttura [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) da inizializzare.

Questi flag vengono utilizzati anche `CONTEXT_INFO` per indicare quali campi della struttura vengono utilizzati e validi quando viene restituita la struttura.

Questi valori possono essere combinati con un OR bit per bit.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
