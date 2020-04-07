---
title: PROPRIETÀ BP_LOCATION . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c98fde516a3e836302cd7eb2c73abd730d5cc8c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737936"
---
# <a name="bp_location"></a>BP_LOCATION
Specifica il tipo di struttura utilizzata per descrivere la posizione del punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _BP_LOCATION {
    BP_LOCATION_TYPE bpLocationType;
    union {
        BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;
        BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;
        BP_LOCATION_CODE_CONTEXT     bplocCodeContext;
        BP_LOCATION_CODE_STRING      bplocCodeString;
        BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;
        BP_LOCATION_DATA_STRING      bplocDataString;
        BP_LOCATION_RESOLUTION       bplocResolution;
        DWORD                        unused;
    } bpLocation;
} BP_LOCATION;
```

```csharp
public struct BP_LOCATION {
    public uint   bpLocationType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public IntPtr unionmember4;
};
```

## <a name="members"></a>Membri
`bpLocationType`\
Valore dell'enumerazione [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) utilizzato `bpLocation` per `unionmemberX` interpretare l'unione o i membri.

`bpLocation`.`bplocCodeFileLine`\
[Solo C) Contiene [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) la struttura `bpLocationType`  =  `BPLT_CODE_FILE_LINE`BP_LOCATION_CODE_FILE_LINE se .

`bpLocation.bplocCodeFuncOffset`\
[Solo C) Contiene [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) la struttura `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET`BP_LOCATION_CODE_FUNC_OFFSET se .

`bpLocation.bplocCodeContext`\
[Solo C) Contiene [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) la struttura `bpLocationType`  =  `BPLT_CODE_CONTEXT`BP_LOCATION_CODE_CONTEXT se .

`bpLocation.bplocCodeString`\
[Solo C) Contiene [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) la struttura `bpLocationType`  =  `BPLT_CODE_STRING`BP_LOCATION_CODE_STRING se .

`bpLocation.bplocCodeAddress`\
[Solo C) Contiene [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) la struttura `bpLocationType`  =  `BPLT_CODE_ADDRESS`BP_LOCATION_CODE_ADDRESS se .

`bpLocation.bplocDataString`\
[Solo C) Contiene [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) la struttura `bpLocationType`  =  `BPLT_DATA_STRING`BP_LOCATION_DATA_STRING se .

`bpLocation.bplocResolution`\
[Solo C) Contiene [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) la struttura `bpLocationType`  =  `BPLT_RESOLUTION`BP_LOCATION_RESOLUTION se .

`unionmember1`\
[Solo In Cè] Vedere Osservazioni su come interpretare.

`unionmember2`\
[Solo In Cè] Vedere Osservazioni su come interpretare.

`unionmember3`\
[Solo In Cè] Vedere Osservazioni su come interpretare.

`unionmember4`\
[Solo In Cè] Vedere Osservazioni su come interpretare.

## <a name="remarks"></a>Osservazioni
Questa struttura è un membro del [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) strutture.

 [Solo In Cè] I `unionmemberX` membri vengono interpretati in base alla tabella seguente. Cercare la colonna di `bpLocationType` sinistra per il valore, quindi `unionmemberX` cercare tra `unionmemberX` le altre colonne per determinare ciò che ogni membro rappresenta ed effettuare il marshalling di di conseguenza. Vedere l'esempio per un modo per interpretare una parte di questa struttura in C .

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string`(un contesto)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string`(un contesto)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string`(un contesto)|`string`(espressione condizionale)|-|-|
|`BPLT_CODE_ADDRESS`|`string`(un contesto)|`string`(URL modulo)|`string`(nome funzione)|`string`(indirizzo)|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string`(un contesto)|`string`(espressione dati)|`uint`(numero di elementi)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>Esempio
In questo esempio viene `BP_LOCATION` illustrato come interpretare la struttura in C ' per il `BPLT_DATA_STRING` tipo. Questo particolare tipo mostra come `unionmemberX` interpretare tutti e quattro i membri in tutti i formati possibili (oggetto, stringa e numero).

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_LOCATION bp)
        {
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)
            {
                IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);
                string context = Marshal.PtrToStringBSTR(bp.unionmember2);
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);
            }
        }
    }
}
```

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)
- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)
- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)
- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)
- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)
