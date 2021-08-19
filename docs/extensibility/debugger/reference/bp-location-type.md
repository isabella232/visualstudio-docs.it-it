---
description: Specifica il tipo di posizione del punto di interruzione per una richiesta di punto di interruzione.
title: BP_LOCATION_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 794da0fdccdeee1da47181e5d243bd22734602b5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120452"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
Specifica il tipo di posizione del punto di interruzione per una richiesta di punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
typedef DWORD BP_LOCATION_TYPE;
```

```csharp
public enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
```

## <a name="fields"></a>Campi
`BPLT_NONE`\
Non specifica la posizione del punto di interruzione.

`BPLT_FILE_LINE`\
Specifica il tipo di posizione del punto di interruzione come riga di file.

`BPLT_FUNC_OFFSET`\
Specifica il tipo di posizione del punto di interruzione come offset della funzione.

`BPLT_CONTEXT`\
Specifica il tipo di posizione del punto di interruzione come contesto.

`BPLT_STRING`\
Specifica il tipo di posizione del punto di interruzione come stringa.

`BPLT_ADDRESS`\
Specifica il tipo di posizione del punto di interruzione come indirizzo.

`BPLT_RESOLUTION`\
Specifica il tipo di posizione del punto di interruzione come risoluzione.

`BPLT_CODE_FILE_LINE`\
Specifica il tipo di posizione del punto di interruzione come riga di codice sorgente.

`BPLT_CODE_FUNC_OFFSET`\
Specifica il tipo di posizione del punto di interruzione come offset della funzione di codice.

`BPLT_CODE_CONTEXT`\
Specifica il tipo di posizione del punto di interruzione come contesto del codice.

`BPLT_CODE_STRING`\
Specifica il tipo di posizione del punto di interruzione come stringa di codice.

`BPLT_CODE_ADDRESS`\
Specifica il tipo di posizione del punto di interruzione come indirizzo del codice.

`BPLT_DATA_STRING`\
Specifica il tipo di posizione del punto di interruzione come stringa di dati.

`BPLT_TYPE_MASK`\
Specifica una maschera di bit, in modo che il tipo di punto di interruzione possa essere estratto dal valore.

`BPLT_LOCATION_TYPE_MASK`\
Specifica una maschera di bit, in modo che il tipo di posizione del punto di interruzione possa essere estratto dal valore.

## <a name="remarks"></a>Commenti
Passato come parametro al [metodo GetLocationType.](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)

Un tipo di posizione del punto di interruzione è costituito da un tipo di punto di interruzione e da un tipo di posizione. Ciò significa che un tipo di posizione del punto di interruzione non è mai solo un tipo di punto di interruzione (ad esempio, ) o un tipo di posizione `BPT_CODE` (ad esempio, `BPLT_FILE_LINE` ). Le costanti predefinite per tutti i tipi di posizione dei punti di interruzione attualmente supportati sono incluse in questa enumerazione `BPLT_CODE_FILE_LINE` (da a `BPLT_DATA_STRING` ).

`BPT_CODE`e `BPT_DATA` sono membri [dell'enumerazione BP_TYPE.](../../../extensibility/debugger/reference/bp-type.md)

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
