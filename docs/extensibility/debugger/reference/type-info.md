---
title: proprietà TYPE_INFO . Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
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
 Valore dell'enumerazione [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) che determina come interpretare l'unione.

 `type.typeMeta`\
 [Solo C) Contiene una struttura `dwKind` `TYPE_KIND_METADATA` [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) se è .

 `type.typePdb`\
 [Solo C) Contiene una struttura `dwKind` `TYPE_KIND_PDB` [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) se è .

 `type.typeBuilt`\
 [Solo C) Contiene una struttura `dwKind` `TYPE_KIND_BUILT` [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) se è .

 `type.unused`\
 Spaziatura interna inutilizzata.

 `type`\
 Nome dell'unione.

 `unionmember`\
 [Solo In Cè] Eseguire il marshalling del `dwKind`tipo di struttura appropriato in base a .

## <a name="remarks"></a>Osservazioni
 Questa struttura viene passata al [metodo GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) in cui viene compilata. Il modo in cui il contenuto `dwKind` della struttura viene interpretato si basa sul campo.

> [!NOTE]
> [Solo C) Se `dwKind` è `TYPE_KIND_BUILT`uguale a , è necessario rilasciare l'oggetto [sottostante IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto quando si distrugge la `TYPE_INFO` struttura. Questa operazione viene effettuata chiamando `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.

 [Solo In Cè] Nella tabella seguente viene `unionmember` illustrato come interpretare il membro per ogni tipo di tipo. L'esempio mostra come questa operazione viene eseguita per un tipo di tipo.

|`dwKind`|`unionmember`interpretato come|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Esempio
 In questo esempio viene `unionmember` illustrato `TYPE_INFO` come interpretare il membro della struttura in C . In questo esempio viene illustrato`TYPE_KIND_METADATA`come interpretare un solo tipo ( ) ma gli altri vengono interpretati esattamente nello stesso modo.

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
- [Informazioni su GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
