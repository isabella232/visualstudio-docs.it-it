---
title: DISASSEMBLY_STREAM_SCOPE . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fae1f22c6db22cd6cff93cfb1b98a28620a1537c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737263"
---
# <a name="disassembly_stream_scope"></a>DISASSEMBLY_STREAM_SCOPE
Specifica l'ambito del flusso di disassembly.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
typedef DWORD DISASSEMBLY_STREAM_SCOPE;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
```

## <a name="fields"></a>Campi
`DSS_HUGE`\
Specifica che il disassemblaggio del contesto del codice genererebbe più output di quello che un client in genere desidera recuperare in una singola chiamata.

`DSS_FUNCTION`\
Specifica che la funzione contenuta nel contesto del codice deve essere disassemblata. Specifica che il flusso di disassembly rappresenta una funzione, quando viene restituito dal [Metodo GetScope.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)

`DSS_MODULE`\
Quando viene restituito `IDebugDisassemblyStream2::GetScope` dal metodo , specifica che il flusso di disassembly rappresenta un modulo.

`DSS_ALL`\
Specifica il disassemblaggio per l'intero spazio degli indirizzi.

## <a name="remarks"></a>Osservazioni
Passato come argomento per il [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) metodo e restituito dal [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) metodo.

Questi valori possono essere combinati `OR`con un oggetto .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
