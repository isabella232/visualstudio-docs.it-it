---
title: TYPE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82796c1d82dc3ca77151abcec3e1dd6ce13ac59d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713323"
---
# <a name="type_info"></a>TYPE_INFO
Questa struttura specifica vari tipi di informazioni sul tipo di un campo.

## <a name="syntax"></a>Sintassi

```cpp
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

## <a name="members"></a>Membri
 `dwKind`\
 Valore dell'enumerazione [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) che determina come interpretare l'Unione.

 `type.typeMeta`\
 [Solo C++] Contiene una struttura [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) se `dwKind` è `TYPE_KIND_METADATA` .

 `type.typePdb`\
 [Solo C++] Contiene una struttura [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) se `dwKind` è `TYPE_KIND_PDB` .

 `type.typeBuilt`\
 [Solo C++] Contiene una struttura [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) se `dwKind` è `TYPE_KIND_BUILT` .

 `type.unused`\
 Spaziatura inutilizzata.

 `type`\
 Nome dell'Unione.

 `unionmember`\
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
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
