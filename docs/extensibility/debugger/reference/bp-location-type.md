---
title: BP_LOCATION_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 781aa55f26fbd332b901dacdb3b4ac12d85579cf
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318511"
---
# <a name="bplocationtype"></a>BP_LOCATION_TYPE
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

## <a name="members"></a>Membri
BPLT_NONE  
Non specifica nessuna posizione punto di interruzione.

BPLT_FILE_LINE  
Specifica il tipo di posizione del punto di interruzione come un file di riga.

BPLT_FUNC_OFFSET  
Specifica il tipo di posizione del punto di interruzione come un offset di funzione.

BPLT_CONTEXT  
Specifica il tipo di posizione del punto di interruzione come un contesto.

BPLT_STRING  
Specifica il tipo di posizione del punto di interruzione sotto forma di stringa.

BPLT_ADDRESS  
Specifica il tipo di posizione del punto di interruzione come un indirizzo.

BPLT_RESOLUTION  
Specifica il tipo di posizione del punto di interruzione come una risoluzione.

BPLT_CODE_FILE_LINE  
Specifica il tipo di posizione del punto di interruzione come una riga di codice sorgente.

BPLT_CODE_FUNC_OFFSET  
Specifica il tipo di posizione del punto di interruzione come un offset di funzione di codice.

BPLT_CODE_CONTEXT  
Specifica il tipo di posizione del punto di interruzione come un contesto del codice.

BPLT_CODE_STRING  
Specifica il tipo di posizione del punto di interruzione come una stringa di codice.

BPLT_CODE_ADDRESS  
Specifica il tipo di posizione del punto di interruzione come un indirizzo di codice.

BPLT_DATA_STRING  
Specifica il tipo di posizione del punto di interruzione come una stringa di dati.

BPLT_TYPE_MASK  
Specifica una maschera di bit, in modo che il tipo di punto di interruzione possa essere estratti dal valore.

BPLT_LOCATION_TYPE_MASK  
Specifica una maschera di bit, in modo che il tipo di posizione del punto di interruzione possa essere estratti dal valore.

## <a name="remarks"></a>Note
Passato come parametro per il [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) (metodo).

Un tipo di posizione del punto di interruzione è costituito da un tipo di punto di interruzione e un tipo di posizione. Ciò significa che un tipo di posizione del punto di interruzione non è solo un tipo di punto di interruzione (ad esempio, `BPT_CODE`) o un tipo di posizione (ad esempio, `BPLT_FILE_LINE`). Le costanti predefinite per tutti i tipi di posizione punto di interruzione attualmente supportati sono inclusi in questa enumerazione (`BPLT_CODE_FILE_LINE` tramite `BPLT_DATA_STRING`).

`BPT_CODE` e `BPT_DATA` appartengono le [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) enumerazione.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
[Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)  
[BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
