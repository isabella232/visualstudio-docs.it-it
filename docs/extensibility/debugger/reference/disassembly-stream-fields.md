---
title: DISASSEMBLY_STREAM_FIELDS . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d10f2143cbefa86442e4087ac098020f5f2bd6ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737358"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
Specifica le informazioni da recuperare su un campo di sassieme.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
typedef DWORD DISASSEMBLY_STREAM_FIELDS;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
```

## <a name="fields"></a>Campi
`DSF_ADDRESS`\
Inizializzare/utilizzare `bstrAddress` il campo.

`DSF_ADDRESSOFFSET`\
Inizializzare/utilizzare `bstrAddressOffset` il campo.

`DSF_CODEBYTES`\
Inizializzare/utilizzare `bstrCodeBytes` il campo.

`DSF_OPCODE`\
Inizializzare/utilizzare `bstrOpCode` il campo.

`DSF_OPERANDS`\
Inizializzare/utilizzare `bstrOperands` il campo.

`DSF_SYMBOL`\
Inizializzare/utilizzare `bstrSymbol` il campo.

`DSF_CODELOCATIONID`\
Inizializzare/utilizzare `uCodeLocationId` il campo.

`DSF_POSITION`\
Inizializzare/utilizzare `posBeg` `posEnd` i campi e .

`DSF_DOCUMENTURL`\
Inizializzare/utilizzare `bstrDocumentUrl` il campo.

`DSF_BYTEOFFSET`\
Inizializzare/utilizzare `dwByteOffset` il campo.

`DSF_FLAGS`\
Inizializzare/utilizzare `dwFlags` il campo ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)).

`DSF_OPERANDS_SYMBOLS`\
Includere i nomi `bstrOperands` dei simboli nel campo.

`DSF_ALL`\
Specifica tutti i campi per il flusso di disassembly.

## <a name="remarks"></a>Osservazioni
Passato come parametro al metodo [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) per indicare i campi della struttura [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) da inizializzare.

Utilizzato per `dwFields` il `DisassemblyData` membro della struttura per indicare i campi utilizzati e validi quando viene restituita la struttura.

Questi valori possono essere combinati `OR`con un oggetto .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Leggere](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
