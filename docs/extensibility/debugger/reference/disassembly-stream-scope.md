---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 724e32f83cfec31c2bacdab661407983af87efe6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318252"
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
Specifica l'ambito del flusso di disassemblaggio.

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
Specifica che il contesto del codice di disassemblaggio sarebbe generare più output di un client in genere è necessario recuperare in una singola chiamata.

`DSS_FUNCTION`\
Specifica che la funzione contenuta dal contesto del codice deve essere disassemblata. Specifica che il flusso disassembly rappresenta una funzione, quando restituiti per il [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) (metodo).

`DSS_MODULE`\
Quando restituisce il `IDebugDisassemblyStream2::GetScope` metodo, specifica che il flusso disassembly rappresenta un modulo.

`DSS_ALL`\
Specifica il disassembly per l'intero spazio indirizzi.

## <a name="remarks"></a>Note
Passato come argomento per il [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) metodo e restituito dalle [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) (metodo).

Questi valori possono essere combinati con un bit per bit `OR`.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
