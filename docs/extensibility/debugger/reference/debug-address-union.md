---
description: Vengono descritti i diversi tipi di indirizzi.
title: DEBUG_ADDRESS_UNION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea2999e85c721ce2582a781b8914241076470710
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170705"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
Vengono descritti i diversi tipi di indirizzi.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagDEBUG_ADDRESS_UNION {
   ADDRESS_KIND dwKind;
   union {
      NATIVE_ADDRESS                  addrNative;
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;
      METADATA_ADDRESS_METHOD         addrMethod;
      METADATA_ADDRESS_FIELD          addrField;
      METADATA_ADDRESS_LOCAL          addrLocal;
      METADATA_ADDRESS_PARAM          addrParam;
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;
      METADATA_ADDRESS_RETVAL         addrRetVal;
      DWORD                           unused;
   } addr;
} DEBUG_ADDRESS_UNION;
```

```csharp
public struct DEBUG_ADDRESS_UNION {
   public ADDRESS_KIND dwKind;
   public IntPtr       unionmember;
}
```

## <a name="members"></a>Members
`dwKind`\
Valore dell'enumerazione [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) , che specifica come interpretare l'Unione.

`addr.addrNative`\
[Solo C++] Contiene la struttura [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) se `dwKind` = ADDRESS_KIND_NATIVE.

`addr.addrThisRel`\
[Solo C++] Contiene la struttura[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) se `dwKind` = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.

`addr.addUPhysical`\
[Solo C++] Contiene la struttura[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) se `dwKind` = ADDRESS_KIND_UNMANAGED_PHYSICAL.

`addr.addrMethod`\
[Solo C++] Contiene la struttura[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) se `dwKind` = ADDRESS_KIND_METHOD.

`addr.addrField`\
[Solo C++] Contiene la struttura[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) se `dwKind` = ADDRESS_KIND_FIELD.

`addr.addrLocal`\
[Solo C++] Contiene la struttura[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) se `dwKind` = ADDRESS_KIND_LOCAL.

`addr.addrParam`\
[Solo C++] Contiene la struttura[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) se `dwKind` = ADDRESS_KIND_PARAM.

`addr.addrArrayElem`\
[Solo C++] Contiene la struttura[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) se `dwKind` = ADDRESS_KIND_ARRAYELEM.

`addr.addrRetVal`\
[Solo C++] Contiene la struttura[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) se `dwKind` = ADDRESS_KIND_RETVAL.

`addr.unused`\
[Solo C++] spaziatura interna.

`addr`\
[Solo C++] Nome dell'Unione.

`unionmember`\
[Solo C#] È necessario effettuare il marshalling di questo valore al tipo di struttura appropriato in base a `dwKind` . Vedere la sezione Osservazioni per l'associazione tra `dwKind` e l'interpretazione dell'Unione.

## <a name="remarks"></a>Commenti
Questa struttura fa parte della struttura [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) e rappresenta uno dei diversi tipi di indirizzi (la `DEBUG_ADDRESS` struttura viene compilata da una chiamata al metodo [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) ).

 [Solo C#] Nella tabella seguente viene illustrato come interpretare il `unionmember` membro per ogni tipo di indirizzo. Nell'esempio viene illustrato come eseguire questa operazione per un tipo di indirizzo.

|`dwKind`|`unionmember` interpretato come|
|--------------|----------------------------------|
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|

## <a name="example"></a>Esempio
Questo esempio illustra come interpretare un tipo di indirizzo ( `METADATA_ADDRESS_ARRAYELEM` ) della `DEBUG_ADDRESS_UNION` struttura in C#. Gli elementi rimanenti possono essere interpretati esattamente allo stesso modo.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(DEBUG_ADDRESS_UNION dau)
        {
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)
            {
                 METADATA_ADDRESS_ARRAYELEM arrayElem =
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,
                                 typeof(METADATA_ADDRESS_ARRAYELEM));
            }
        }
    }
}
```

## <a name="requirements"></a>Requisiti
Intestazione: sh. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
