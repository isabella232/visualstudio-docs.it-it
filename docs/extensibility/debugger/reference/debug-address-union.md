---
title: DEBUG_ADDRESS_UNION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f3efd78d5e3c84f9d23068be62efdf751767dd1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715069"
---
# <a name="debugaddressunion"></a>DEBUG_ADDRESS_UNION
Descrive i diversi tipi di indirizzi.

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

## <a name="terms"></a>Termini
dwKind un valore di [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumerazione che specifica come interpretare l'unione.

addr.addrNative

 [Solo C++] Contiene il [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) struttura se `dwKind` = ADDRESS_KIND_NATIVE.

addr.addrThisRel

 [Solo C++] Contiene il[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) struttura se `dwKind` = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.

addr.addUPhysical

 [Solo C++] Contiene il[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) struttura se `dwKind` = ADDRESS_KIND_UNMANAGED_PHYSICAL.

addr.addrMethod

 [Solo C++] Contiene il[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) struttura se `dwKind` = ADDRESS_KIND_METHOD.

addr.addrField

 [Solo C++] Contiene il[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) struttura se `dwKind` = ADDRESS_KIND_FIELD.

addr.addrLocal

 [Solo C++] Contiene il[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) struttura se `dwKind` = ADDRESS_KIND_LOCAL.

addr.addrParam

 [Solo C++] Contiene il[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) struttura se `dwKind` = ADDRESS_KIND_PARAM.

addr.addrArrayElem

 [Solo C++] Contiene il[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) struttura se `dwKind` = ADDRESS_KIND_ARRAYELEM.

addr.addrRetVal

 [Solo C++] Contiene il[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) struttura se `dwKind` = ADDRESS_KIND_RETVAL.

addr.unused

 Spaziatura interna [C++ solo].

addr

 [Solo C++] Il nome dell'unione.

UnionMember

 [C# solo] Questo valore deve essere sottoposto a marshalling per il tipo di struttura appropriata in base `dwKind`. Vedere la sezione Osservazioni per l'associazione tra `dwKind` e l'interpretazione dell'unione.

## <a name="remarks"></a>Note
Questa struttura è parte del [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) strutturare e rappresenta uno dei numerosi tipi diversi di indirizzi (le `DEBUG_ADDRESS` struttura viene compilata tramite una chiamata ai [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) (metodo)).


 [C# solo] Nella tabella seguente viene illustrato come interpretare il `unionmember` membro per ogni tipo di indirizzo. Nell'esempio viene illustrato come questa operazione viene eseguita per un tipo di indirizzo.

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
In questo esempio viene illustrato come interpretare un tipo di indirizzo (`METADATA_ADDRESS_ARRAYELEM`) del `DEBUG_ADDRESS_UNION` struttura nel linguaggio c#. Gli elementi rimanenti possono essere interpretati nello stesso modo.

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
