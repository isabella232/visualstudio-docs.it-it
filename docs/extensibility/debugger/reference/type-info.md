---
title: TYPE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bbb64acfd71a6208fde3a5c3f84d6c5886ece72f
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460731"
---
# <a name="typeinfo"></a>TYPE_INFO
Questa struttura consente di specificare vari tipi di informazioni sul tipo del campo.

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
 Un valore compreso il [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) enumerazione che determina come interpretare l'unione.

 `type.typeMeta`\

 [C++ solo] Contiene un [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) struttura se `dwKind` è `TYPE_KIND_METADATA`.

 `type.typePdb`\

 [C++ solo] Contiene un [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) struttura se `dwKind` è `TYPE_KIND_PDB`.

 `type.typeBuilt`\

 [C++ solo] Contiene un [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) struttura se `dwKind` è `TYPE_KIND_BUILT`.

 `type.unused`\
 Spaziatura interna inutilizzata.

 `type`\
 Nome dell'unione.

 `unionmember`\

 [C# solo] Effettuare il marshalling per il tipo di struttura appropriata in base `dwKind`.

## <a name="remarks"></a>Note
 Questa struttura viene passata per il [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) in cui viene compilato nel metodo. Come interpretare il contenuto della struttura di base di `dwKind` campo.

> [!NOTE]
> [C++ solo] Se `dwKind` è uguale a `TYPE_KIND_BUILT`, quindi è necessario rilasciare sottostante [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) dell'oggetto quando si eliminano i `TYPE_INFO` struttura. Questa operazione viene effettuata chiamando `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.

 [C# solo] Nella tabella seguente viene illustrato come interpretare il `unionmember` membro per ogni tipo di elemento. Nell'esempio viene illustrato come questa operazione viene eseguita per un tipo di elemento.

|`dwKind`|`unionmember` interpretato come|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Esempio
 In questo esempio viene illustrato come interpretare la `unionmember` membro del `TYPE_INFO` struttura nel linguaggio c#. Questo esempio illustra l'interpretazione di un solo tipo (`TYPE_KIND_METADATA`), ma gli altri vengono interpretati in esattamente allo stesso modo.

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
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)