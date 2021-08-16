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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 95ca1e9e65a1fac9a9171bed1bfef90b011c44a1308f2a6eb01b9a029d1acbc3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360898"
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
Inizializzare/usare `bstrModuleUrl` il campo della [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) struttura .

`CIF_FUNCTION`\
Inizializzare/usare `bstrFunction` il campo della struttura `CONTEXT_INFO` .

`CIF_FUNCTIONOFFSET`\
Inizializzare/usare `posFunctionOffset` il campo della struttura `CONTEXT_INFO` .

`CIF_ADDRESS`\
Inizializzare/usare `bstrAddress` il campo della struttura `CONTEXT_INFO` .

`CIF_ADDRESSOFFSET`\
Inizializzare/usare `bstrAddressOffset` il campo della struttura `CONTEXT_INFO` .

`CIF_ALLFIELDS`\
Inizializzare/usare tutti i campi della `CONTEXT_INFO` struttura .

## <a name="remarks"></a>Commenti
A questi valori viene passato un parametro al [metodo GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) per indicare [quali](../../../extensibility/debugger/reference/context-info.md) campi della struttura CONTEXT_INFO devono essere inizializzati.

Questi flag vengono usati anche per indicare quali campi della struttura vengono usati e `CONTEXT_INFO` validi quando viene restituita la struttura .

Questi valori possono essere combinati con un'operazione OR bit per bit.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
