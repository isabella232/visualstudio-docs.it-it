---
title: proprietà BP_RESOLUTION_LOCATION . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b11d80e90daec19a14ca509e5a4b9bdb2d1ced4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737819"
---
# <a name="bp_resolution_location"></a>BP_RESOLUTION_LOCATION
Specifica la struttura della posizione di risoluzione del punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
struct _BP_RESOLUTION_LOCATION {
    BP_TYPE bpType;
    union {
        BP_RESOLUTION_CODE bpresCode;
        BP_RESOLUTION_DATA bpresData;
        int                unused;
    } bpResLocation;
} BP_RESOLUTION_LOCATION;
```

```csharp
public struct BP_RESOLUTION_LOCATION {
    public uint   bpType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public uint   unionmember4;
};
```

## <a name="members"></a>Membri
`bpType`\
Valore dell'enumerazione [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) che specifica `bpResLocation` come `unionmemberX` interpretare l'unione o i membri.

`bpResLocation.bpresCode`\
[Solo C) Contiene [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) la struttura `bpType`  =  `BPT_CODE`BP_RESOLUTION_CODE se .

`bpResLocation.bpresData`\
[Solo C) Contiene [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) la struttura `bpType`  =  `BPT_DATA`BP_RESOLUTION_DATA se .

`bpResLocation.unused`\
[Solo C) Segnaposto.

`unionmember1`\
[Solo In Cè] Vedere Osservazioni su come interpretare.

`unionmember2`\
[Solo In Cè] Vedere Osservazioni su come interpretare.

`unionmember3`\
[Solo In Cè] Vedere Osservazioni su come interpretare.

`unionmember4`\
[Solo In Cè] Vedere Osservazioni su come interpretare.

## <a name="remarks"></a>Osservazioni
Questa struttura è un membro del [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) e [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) strutture.

 [Solo In Cè] I `unionmemberX` membri vengono interpretati in base alla tabella seguente. Cercare la colonna di `bpType` sinistra per il `unionmemberX` valore quindi attraverso `unionmemberX` per determinare ciò che ogni membro rappresenta ed effettuare il marshalling di di conseguenza. Vedere l'esempio per un modo per interpretare questa struttura in C .

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string`(espressione dati)|`string`(nome funzione)|`string`(nome immagine)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>Esempio
In questo esempio viene `BP_RESOLUTION_LOCATION` illustrato come interpretare la struttura in C.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_RESOLUTION_LOCATION bprl)
        {
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)
            {
                IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);
            }
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)
            {
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);
                string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);
                enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;
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
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
