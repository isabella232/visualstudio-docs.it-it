---
description: Specifica i flag per disassembly.
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d4640ee39a936318b5e200fc46135e1fc271c46b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122119997"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
Specifica i flag per disassembly.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
typedef DWORD DISASSEMBLY_FLAGS;
```

```csharp
public enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
```

## <a name="fields"></a>Campi
`DF_DOCUMENTCHANGE`\
Indica che questa istruzione si trova in un documento diverso da quello precedente.

`DF_DISABLED`\
Indica che questa istruzione non verrà eseguita.

`DF_INSTRUCTION_ACTIVE`\
Indica che questa istruzione è una delle istruzioni seguenti da eseguire (potrebbero essere presenti più istruzioni).

`DF_DATA`\
Indica che questa istruzione è realmente dati (non codice).

`DF_HASSOURCE`\
Indica che questa istruzione ha origine. Alcune istruzioni, ad esempio la profilatura o il codice di Garbage Collection, non hanno un'origine corrispondente.

`DF_DOCUMENT_CHECKSUM`\
Indica che il campo `bstrDocumentUrl` contiene dati di checksum dopo l'URL del documento. Vedere la sezione Osservazioni per la struttura [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) per informazioni sulla modalità di archiviazione dei dati di checksum.

## <a name="remarks"></a>Commenti
Utilizzato come `dwFlags` membro della struttura [DisassemblyData.](../../../extensibility/debugger/reference/disassemblydata.md)

Questi flag possono essere combinati con un oggetto bit per `OR` bit.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
