---
title: PROVIDER_FIELDS . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FIELDS
helpviewer_keywords:
- PROVIDER_FIELDS enumeration
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 37f64b455ab0331f9b8f08da1f29a3e2c1b82fdf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713796"
---
# <a name="provider_fields"></a>PROVIDER_FIELDS
Specifica le proprietà associate a un provider di programmi.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_PROVIDER_FIELDS {
   PFIELD_PROGRAM_NODES       = 0x01,
   PFIELD_IS_DEBUGGER_PRESENT = 0x02
};
typedef DWORD PROVIDER_FIELDS;
```

```csharp
public enum enum_PROVIDER_FIELDS {
   PFIELD_PROGRAM_NODES       = 0x01,
   PFIELD_IS_DEBUGGER_PRESENT = 0x02
};
```

## <a name="fields"></a>Campi
 `PFIELD_PROGRAM_NODES`\
 Il `ProgramNodes` campo è valido.

 `PFIELD_IS_DEBUGGER_PRESENT`\
 Il `fIsDebuggerPresent` campo è valido.

## <a name="remarks"></a>Osservazioni
 Questi valori vengono restituiti nel `Fields` membro della struttura [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) per indicare quali campi della struttura sono stati compilati in modo esplicito.

 Questi valori possono essere combinati `OR`con un file bit per bit.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
