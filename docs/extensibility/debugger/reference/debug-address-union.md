---
title: DEBUG_ADDRESS_UNION . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad531ee10914e404459632c98aae4a9bbda8e437
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737534"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
Descrive diversi tipi di indirizzi.

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

## <a name="members"></a>Membri
`dwKind`\
Valore dell'enumerazione [ADDRESS_KIND,](../../../extensibility/debugger/reference/address-kind.md) che specifica come interpretare l'unione.

`addr.addrNative`\
[Solo C) Contiene la struttura `dwKind` [NATIVE_ADDRESS,](../../../extensibility/debugger/reference/native-address.md) se ADDRESS_KIND_NATIVE.

`addr.addrThisRel`\
[Solo C) Contiene la struttura `dwKind` [del UNMANAGED_ADDRESS_THIS_RELATIVE,](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) se ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.

`addr.addUPhysical`\
[Solo C) Contiene la struttura `dwKind` [UNMANAGED_ADDRESS_PHYSICAL,](../../../extensibility/debugger/reference/unmanaged-address-physical.md) se ADDRESS_KIND_UNMANAGED_PHYSICAL.

`addr.addrMethod`\
[Solo C) Contiene la struttura `dwKind` [del METADATA_ADDRESS_METHOD,](../../../extensibility/debugger/reference/metadata-address-method.md) se ADDRESS_KIND_METHOD.

`addr.addrField`\
[Solo C) Contiene la struttura `dwKind` [METADATA_ADDRESS_FIELD,](../../../extensibility/debugger/reference/metadata-address-field.md) se ADDRESS_KIND_FIELD.

`addr.addrLocal`\
[Solo C) Contiene la struttura `dwKind` [METADATA_ADDRESS_LOCAL,](../../../extensibility/debugger/reference/metadata-address-local.md) se ADDRESS_KIND_LOCAL.

`addr.addrParam`\
[Solo C) Contiene la struttura `dwKind` [METADATA_ADDRESS_PARAM,](../../../extensibility/debugger/reference/metadata-address-param.md) se ADDRESS_KIND_PARAM.

`addr.addrArrayElem`\
[Solo C) Contiene la struttura `dwKind` [METADATA_ADDRESS_ARRAYELEM,](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) se ADDRESS_KIND_ARRAYELEM.

`addr.addrRetVal`\
[Solo C) Contiene la struttura `dwKind` [METADATA_ADDRESS_RETVAL,](../../../extensibility/debugger/reference/metadata-address-retval.md) se ADDRESS_KIND_RETVAL.

`addr.unused`\
[Solo Cè] imbottitura.

`addr`\
[Solo C) Nome dell'unione.

`unionmember`\
[Solo In Cè] È necessario eseguire il marshalling di questo `dwKind`valore nel tipo di struttura appropriato in base a . Vedere Osservazioni per `dwKind` l'associazione e l'interpretazione dell'unione.

## <a name="remarks"></a>Osservazioni
Questa struttura fa parte della [struttura DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) e rappresenta uno dei `DEBUG_ADDRESS` diversi tipi di indirizzi (la struttura viene compilata da una chiamata al [metodo GetAddress).](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)

 [Solo In Cè] Nella tabella seguente viene `unionmember` illustrato come interpretare il membro per ogni tipo di indirizzo. L'esempio mostra come questa operazione viene eseguita per un tipo di indirizzo.

|`dwKind`|`unionmember`interpretato come|
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
In questo esempio viene illustrato come`METADATA_ADDRESS_ARRAYELEM`interpretare `DEBUG_ADDRESS_UNION` un tipo di indirizzo ( ) della struttura in C. Gli elementi rimanenti possono essere interpretati esattamente nello stesso modo.

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
Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
