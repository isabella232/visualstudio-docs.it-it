---
title: ADDRESS_KIND . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1298df79bbe34b240d6e7b186f42e20b3d1a89de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738152"
---
# <a name="address_kind"></a>ADDRESS_KIND
Specifica i tipi di indirizzi.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
typedef DWORD ADDRESS_KIND;
```

```csharp
public enum enum_ADDRESS_KIND {
    ADDRESS_KIND_NATIVE                  = 0x0001,
    ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,
    ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,
    ADDRESS_KIND_METADATA_METHOD         = 0x0010,
    ADDRESS_KIND_METADATA_FIELD          = 0x0011,
    ADDRESS_KIND_METADATA_LOCAL          = 0x0012,
    ADDRESS_KIND_METADATA_PARAM          = 0x0013,
    ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,
    ADDRESS_KIND_METADATA_RETVAL         = 0x0015,
};
```

## <a name="fields"></a>Campi
`ADDRESS_KIND_NATIVE`\
Indirizzo nativo, rappresentato dalla struttura [NATIVE_ADDRESS.](../../../extensibility/debugger/reference/native-address.md)

`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`\
Indirizzo non gestito relativo a un `this` puntatore (`Me` in Visual Basic) e rappresentato dalla struttura [UNMANAGED_ADDRESS_THIS_RELATIVE.](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)

`ADDRESS_KIND_UNMANAGED_PHYSICAL`\
Indirizzo fisico non gestito, rappresentato dalla struttura [UNMANAGED_ADDRESS_PHYSICAL.](../../../extensibility/debugger/reference/unmanaged-address-physical.md)

`ADDRESS_KIND_METHOD`\
Metodo di una classe, rappresentato dalla struttura [METADATA_ADDRESS_METHOD.](../../../extensibility/debugger/reference/metadata-address-method.md)

`ADDRESS_KIND_FIELD`\
Campo di una classe, rappresentato dalla struttura [METADATA_ADDRESS_FIELD.](../../../extensibility/debugger/reference/metadata-address-field.md)

`ADDRESS_KIND_LOCAL`\
L'indirizzo è per una variabile locale ed è rappresentato dalla [struttura METADATA_ADDRESS_LOCAL.](../../../extensibility/debugger/reference/metadata-address-local.md)

`ADDRESS_KIND_PARAM`\
Parametro di metodo o funzione, rappresentato dalla struttura [METADATA_ADDRESS_PARAM.](../../../extensibility/debugger/reference/metadata-address-param.md)

`ADDRESS_KIND_ARRAYELEM`\
Elemento della matrice, rappresentato dalla struttura [METADATA_ADDRESS_ARRAYELEM.](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)

`ADDRESS_KIND_RETVAL`\
Valore restituito, rappresentato dalla [struttura METADATA_ADDRESS_RETVAL.](../../../extensibility/debugger/reference/metadata-address-retval.md)

## <a name="remarks"></a>Osservazioni
Il [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) metodo restituisce la [struttura DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) che contiene un'unione di strutture possibili, la struttura [DEBUG_ADDRESS_UNION.](../../../extensibility/debugger/reference/debug-address-union.md) Il `dwKind` campo `DEBUG_ADDRESS_UNION` della struttura `ADDRESS_KIND` contiene il valore e descrive come interpretare il campo unione.

## <a name="requirements"></a>Requisiti
Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
