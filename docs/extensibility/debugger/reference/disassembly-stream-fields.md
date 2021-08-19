---
description: Specifica le informazioni da recuperare su un campo disassembly.
title: DISASSEMBLY_STREAM_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a43ce4836e761e2660d52d634672f878a86bc66
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080078"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
Specifica le informazioni da recuperare su un campo disassembly.

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
Inizializzare/usare il `bstrAddress` campo .

`DSF_ADDRESSOFFSET`\
Inizializzare/usare il `bstrAddressOffset` campo .

`DSF_CODEBYTES`\
Inizializzare/usare il `bstrCodeBytes` campo .

`DSF_OPCODE`\
Inizializzare/usare il `bstrOpCode` campo .

`DSF_OPERANDS`\
Inizializzare/usare il `bstrOperands` campo .

`DSF_SYMBOL`\
Inizializzare/usare il `bstrSymbol` campo .

`DSF_CODELOCATIONID`\
Inizializzare/usare il `uCodeLocationId` campo .

`DSF_POSITION`\
Inizializzare/usare `posBeg` i campi e `posEnd` .

`DSF_DOCUMENTURL`\
Inizializzare/usare il `bstrDocumentUrl` campo .

`DSF_BYTEOFFSET`\
Inizializzare/usare il `dwByteOffset` campo .

`DSF_FLAGS`\
Inizializzare/usare `dwFlags` il campo ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)).

`DSF_OPERANDS_SYMBOLS`\
Includere i nomi dei simboli nel `bstrOperands` campo.

`DSF_ALL`\
Specifica tutti i campi per il flusso disassembly.

## <a name="remarks"></a>Commenti
Passato come parametro al [metodo Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) per indicare quali campi della [struttura DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) devono essere inizializzati.

Utilizzato per il membro della struttura per indicare quali campi vengono utilizzati e `dwFields` `DisassemblyData` validi quando viene restituita la struttura .

Questi valori possono essere combinati con un oggetto bit per `OR` bit.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
