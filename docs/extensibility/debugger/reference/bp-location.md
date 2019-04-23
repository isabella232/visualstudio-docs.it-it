---
title: BP_LOCATION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 85f8c915f5c0d6d81214220f78c7db0544777cda
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59663323"
---
# <a name="bplocation"></a>BP_LOCATION
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
`bpLocationType` Un valore compreso il [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) enumerazione utilizzata per interpretare il `bpLocation` union o `unionmemberX` membri.

`bpLocation`.`bplocCodeFileLine`

 [C++ solo] Contiene il [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) struttura se `bpLocationType`  =  `BPLT_CODE_FILE_LINE`.

`bpLocation.bplocCodeFuncOffset`

 [C++ solo] Contiene il [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) struttura se `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET`.

`bpLocation.bplocCodeContext`

 [C++ solo] Contiene il [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) struttura se `bpLocationType`  =  `BPLT_CODE_CONTEXT`.

`bpLocation.bplocCodeString`

 [C++ solo] Contiene il [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) struttura se `bpLocationType`  =  `BPLT_CODE_STRING`.

`bpLocation.bplocCodeAddress`

 [C++ solo] Contiene il [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) struttura se `bpLocationType`  =  `BPLT_CODE_ADDRESS`.

`bpLocation.bplocDataString`

 [C++ solo] Contiene il [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) struttura se `bpLocationType`  =  `BPLT_DATA_STRING`.

`bpLocation.bplocResolution`

 [C++ solo] Contiene il [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) struttura se `bpLocationType`  =  `BPLT_RESOLUTION`.

`unionmember1`

 [C# solo] Vedere la sezione Osservazioni sull'interpretazione.

`unionmember2`

 [C# solo] Vedere la sezione Osservazioni sull'interpretazione.

`unionmember3`

 [C# solo] Vedere la sezione Osservazioni sull'interpretazione.

`unionmember4`

 [C# solo] Vedere la sezione Osservazioni sull'interpretazione.

## <a name="remarks"></a>Note
Questa struttura è un membro del [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) strutture.

 [C# solo] Il `unionmemberX` membri vengono interpretati in base alla tabella riportata di seguito. Cerca nella colonna a sinistra per la `bpLocationType` valore per poi passare tra le altre colonne per determinare quali ognuno `unionmemberX` membro rappresenta ed effettuare il marshalling di `unionmemberX` conseguenza. Vedere l'esempio di un modo per interpretare una parte di questa struttura in c#.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string` (a context)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string` (a context)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string` (a context)|`string` (espressione condizionale)|-|-|
|`BPLT_CODE_ADDRESS`|`string` (a context)|`string` (modulo URL)|`string` (nome della funzione)|`string` (indirizzo)|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` (a context)|`string` (espressione di dati)|`uint` (numero di elementi)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>Esempio
In questo esempio viene illustrato come interpretare la `BP_LOCATION` struttura in c# per il `BPLT_DATA_STRING` tipo. Questo tipo particolare di seguito viene illustrato come interpretare tutte e quattro `unionmemberX` membri in tutti i formati possibili (oggetto, stringa e numero).

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
