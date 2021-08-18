---
description: Specifica i tipi di indirizzi.
title: ADDRESS_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77bc222e5d884fcbc464734654eca1e1535c6f0f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030412"
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
Indirizzo nativo, rappresentato dalla struttura [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) specificata.

`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`\
Indirizzo non gestito relativo a un `this` puntatore ( `Me` in Visual Basic) e rappresentato dalla [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) struttura .

`ADDRESS_KIND_UNMANAGED_PHYSICAL`\
Indirizzo fisico non gestito, rappresentato dalla struttura [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) gestita.

`ADDRESS_KIND_METHOD`\
Metodo di una classe, rappresentato dalla struttura [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) struttura .

`ADDRESS_KIND_FIELD`\
Campo di una classe, rappresentato dalla struttura [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) struttura .

`ADDRESS_KIND_LOCAL`\
L'indirizzo è per una variabile locale ed è rappresentato dalla [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) struttura .

`ADDRESS_KIND_PARAM`\
Un metodo o un parametro di funzione, rappresentato dalla [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) struttura .

`ADDRESS_KIND_ARRAYELEM`\
Elemento di matrice, rappresentato dalla [struttura METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) struttura .

`ADDRESS_KIND_RETVAL`\
Valore restituito, rappresentato dalla struttura [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) specificata.

## <a name="remarks"></a>Commenti
Il [metodo GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) restituisce la [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) che contiene un'unione di possibili strutture, la [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struttura. Il `dwKind` campo della struttura contiene il valore e descrive come interpretare il campo `DEBUG_ADDRESS_UNION` `ADDRESS_KIND` unione.

## <a name="requirements"></a>Requisiti
Intestazione: sh.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
