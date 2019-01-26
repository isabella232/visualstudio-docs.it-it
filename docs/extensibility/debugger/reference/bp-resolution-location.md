---
title: BP_RESOLUTION_LOCATION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 295fc99fcaaaf784c4055922407e69cbf2856dbf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54985172"
---
# <a name="bpresolutionlocation"></a>BP_RESOLUTION_LOCATION
Specifica la struttura del percorso di risoluzione dei punti di interruzione.  
  
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
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## <a name="members"></a>Membri  
 `bpType`  
 Un valore compreso il [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) enumerazione che specifica come interpretare le `bpResLocation` union o `unionmemberX` membri.  
  
 `bpResLocation.bpresCode`  
 [Solo C++] Contiene il [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) struttura se `bpType`  =  `BPT_CODE`.  
  
 `bpResLocation.bpresData`  
 [Solo C++] Contiene il [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) struttura se `bpType`  =  `BPT_DATA`.  
  
 `bpResLocation.unused`  
 [Solo C++] Un segnaposto.  
  
 `unionmember1`  
 [C# solo] Vedere la sezione Osservazioni sull'interpretazione.  
  
 `unionmember2`  
 [C# solo] Vedere la sezione Osservazioni sull'interpretazione.  
  
 `unionmember3`  
 [C# solo] Vedere la sezione Osservazioni sull'interpretazione.  
  
 `unionmember4`  
 [C# solo] Vedere la sezione Osservazioni sull'interpretazione.  
  
## <a name="remarks"></a>Note  
 Questa struttura è un membro del [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) e [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) strutture.  
  
 [C# solo] Il `unionmemberX` membri vengono interpretati in base alla tabella riportata di seguito. Cerca nella colonna a sinistra per la `bpType` tra valore quindi per determinare quali ognuno `unionmemberX` membro rappresenta ed effettuare il marshalling il `unionmemberX` conseguenza. Vedere l'esempio di un modo per interpretare questa struttura in c#.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPT_DATA`|`string` (espressione di dati)|`string` (nome della funzione)|`string` (nome immagine)|`enum_BP_RES_DATA_FLAGS`|  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come interpretare il `BP_RESOLUTION_LOCATION` struttura nel linguaggio c#.  
  
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
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)