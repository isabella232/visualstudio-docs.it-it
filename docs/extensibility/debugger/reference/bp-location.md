---
description: Specifica il tipo di struttura utilizzato per descrivere la posizione del punto di interruzione.
title: BP_LOCATION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c8f1a59f252f2fd1eb22bc289f3bc9982d3ba92
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120439"
---
# <a name="bp_location"></a>BP_LOCATION
Specifica il tipo di struttura utilizzato per descrivere la posizione del punto di interruzione.

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

## <a name="members"></a>Members
`bpLocationType`\
Valore dell'enumerazione [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) utilizzata per interpretare l'unione `bpLocation` o i `unionmemberX` membri.

`bpLocation`.`bplocCodeFileLine`\
[Solo C++] Contiene la [struttura BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) se `bpLocationType`  =  `BPLT_CODE_FILE_LINE` .

`bpLocation.bplocCodeFuncOffset`\
[Solo C++] Contiene la [struttura BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) se `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET` .

`bpLocation.bplocCodeContext`\
[Solo C++] Contiene la [struttura BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) se `bpLocationType`  =  `BPLT_CODE_CONTEXT` .

`bpLocation.bplocCodeString`\
[Solo C++] Contiene la [struttura BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) se `bpLocationType`  =  `BPLT_CODE_STRING` .

`bpLocation.bplocCodeAddress`\
[Solo C++] Contiene la [struttura BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) se `bpLocationType`  =  `BPLT_CODE_ADDRESS` .

`bpLocation.bplocDataString`\
[Solo C++] Contiene la [struttura BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) se `bpLocationType`  =  `BPLT_DATA_STRING` .

`bpLocation.bplocResolution`\
[Solo C++] Contiene la [struttura BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) se `bpLocationType`  =  `BPLT_RESOLUTION` .

`unionmember1`\
[Solo C#] Vedere Osservazioni su come interpretare.

`unionmember2`\
[Solo C#] Vedere Osservazioni su come interpretare.

`unionmember3`\
[Solo C#] Vedere Osservazioni su come interpretare.

`unionmember4`\
[Solo C#] Vedere Osservazioni su come interpretare.

## <a name="remarks"></a>Commenti
Questa struttura è un membro delle [strutture BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

 [Solo C#] I `unionmemberX` membri vengono interpretati in base alla tabella seguente. Cercare il valore nella colonna a sinistra, quindi esaminare le altre colonne per determinare ciò che ogni membro rappresenta ed effettuare il `bpLocationType` `unionmemberX` marshalling `unionmemberX` di conseguenza. Vedere l'esempio per un modo per interpretare una parte di questa struttura in C#.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string` (un contesto)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string` (un contesto)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string` (un contesto)|`string` (espressione condizionale)|-|-|
|`BPLT_CODE_ADDRESS`|`string` (un contesto)|`string` (URL del modulo)|`string` (nome della funzione)|`string` (indirizzo)|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` (un contesto)|`string` (espressione dati)|`uint` (numero di elementi)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>Esempio
In questo esempio viene illustrato come interpretare `BP_LOCATION` la struttura in C# per il tipo `BPLT_DATA_STRING` . Questo particolare tipo illustra come interpretare tutti e quattro `unionmemberX` i membri in tutti i formati possibili (oggetto, stringa e numero).

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

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)
- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)
- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)
- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)
- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)
