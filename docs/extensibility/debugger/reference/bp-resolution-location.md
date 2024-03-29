---
description: Specifica la struttura della posizione di risoluzione del punto di interruzione.
title: BP_RESOLUTION_LOCATION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b433f7b58753408c916074539d9d0b6275d1ce17
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635227"
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

## <a name="members"></a>Members
`bpType`\
Valore dell'enumerazione [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) che specifica come interpretare `bpResLocation` l'unione o i `unionmemberX` membri.

`bpResLocation.bpresCode`\
[Solo C++] Contiene la [struttura BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) se `bpType`  =  `BPT_CODE` .

`bpResLocation.bpresData`\
[Solo C++] Contiene la [struttura BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) se `bpType`  =  `BPT_DATA` .

`bpResLocation.unused`\
[Solo C++] Segnaposto.

`unionmember1`\
[Solo C#] Vedere Osservazioni su come interpretare.

`unionmember2`\
[Solo C#] Vedere Osservazioni su come interpretare.

`unionmember3`\
[Solo C#] Vedere Osservazioni su come interpretare.

`unionmember4`\
[Solo C#] Vedere Osservazioni su come interpretare.

## <a name="remarks"></a>Commenti
Questa struttura è un membro delle [strutture BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) e [BP_RESOLUTION_INFO.](../../../extensibility/debugger/reference/bp-resolution-info.md)

 [Solo C#] I `unionmemberX` membri vengono interpretati in base alla tabella seguente. Cercare il valore nella colonna sinistra e quindi in per `bpType` determinare ciò che ogni `unionmemberX` membro rappresenta ed effettuare il marshalling di `unionmemberX` conseguenza. Vedere l'esempio per un modo per interpretare questa struttura in C#.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string` (espressione dati)|`string` (nome della funzione)|`string` (nome immagine)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>Esempio
Questo esempio illustra come interpretare la `BP_RESOLUTION_LOCATION` struttura in C#.

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

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
