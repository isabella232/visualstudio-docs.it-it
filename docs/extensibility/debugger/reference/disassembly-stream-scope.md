---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54773ee6f770855122992f49bebad44fa1f6129a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870298"
---
# <a name="disassembly_stream_scope"></a>DISASSEMBLY_STREAM_SCOPE
Specifica l'ambito del flusso di Disassembly.

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
Specifica che il disassemblaggio del contesto del codice genererebbe un output maggiore di quello che un client in genere vuole recuperare in un'unica chiamata.

`DSS_FUNCTION`\
Specifica che la funzione contenuta nel contesto del codice deve essere disassemblata. Specifica che il flusso di Disassembly rappresenta una funzione, se restituita dal metodo [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) .

`DSS_MODULE`\
Quando viene restituito dal `IDebugDisassemblyStream2::GetScope` metodo, specifica che il flusso di Disassembly rappresenta un modulo.

`DSS_ALL`\
Specifica il disassembly per l'intero spazio degli indirizzi.

## <a name="remarks"></a>Commenti
Passato come argomento al metodo [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) e restituito dal metodo [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) .

Questi valori possono essere combinati con un bit per bit `OR` .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
