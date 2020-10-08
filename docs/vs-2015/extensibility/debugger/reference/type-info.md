---
title: TYPE_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12102c297c34649c753cf1c811994f9e750b9605
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2020
ms.locfileid: "91838509"
---
# <a name="type_info"></a>TYPE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa struttura specifica vari tipi di informazioni sul tipo di un campo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
struct _tagTYPE_INFO_UNION {  
   dwTYPE_KIND dwKind;  
   union {  
      METADATA_TYPE typeMeta;  
      PDB_TYPE      typePdb;  
      BUILT_TYPE    typeBuilt;  
      DWORD         unused;  
   } type;  
} TYPE_INFO;  
```  
  
```csharp  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### <a name="parameters"></a>Parametri  
 dwKind  
 Valore dell'enumerazione [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) che determina come interpretare l'Unione.  
  
 digitare. typeMeta  
 [Solo C++] Contiene una struttura [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) se `dwKind` è `TYPE_KIND_METADATA` .  
  
 digitare. typePdb  
 [Solo C++] Contiene una struttura [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) se `dwKind` è `TYPE_KIND_PDB` .  
  
 digitare. typeBuilt  
 [Solo C++] Contiene una struttura [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) se `dwKind` è `TYPE_KIND_BUILT` .  
  
 tipo. non utilizzato  
 Spaziatura inutilizzata.  
  
 type  
 Nome dell'Unione.  
  
 unionmember  
 [Solo C#] Eseguire il marshalling di questo oggetto nel tipo di struttura appropriato in base a `dwKind` .  
  
## <a name="remarks"></a>Osservazioni  
 Questa struttura viene passata al metodo [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) in cui è compilata. Il modo in cui il contenuto della struttura viene interpretato è basato sul `dwKind` campo.  
  
> [!NOTE]
> [Solo C++] Se è `dwKind` uguale `TYPE_KIND_BUILT` a, è necessario rilasciare l'oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) sottostante quando si elimina la `TYPE_INFO` struttura. Questa operazione viene effettuata chiamando `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.  
  
 [Solo C#] Nella tabella seguente viene illustrato come interpretare il `unionmember` membro per ogni tipo di tipo. Nell'esempio viene illustrato come eseguire questa operazione per un tipo di tipo.  
  
|`dwKind`|`unionmember` interpretato come|  
|--------------|----------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## <a name="example"></a>Esempio  
 Questo esempio illustra come interpretare il `unionmember` membro della `TYPE_INFO` struttura in C#. Questo esempio illustra l'interpretazione di un solo tipo ( `TYPE_KIND_METADATA` ), ma gli altri vengono interpretati esattamente allo stesso modo.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(TYPE_INFO ti)  
        {  
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)  
            {  
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,  
                                               typeof(METADATA_TYPE));  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
