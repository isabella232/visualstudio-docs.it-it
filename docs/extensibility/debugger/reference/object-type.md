---
title: OBJECT_TYPE . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ffb85a14e42dd57c345481285eb1f776b3866d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714134"
---
# <a name="object_type"></a>Object_Type
Specifica il tipo di un oggetto dall'analizzatore di espressioni.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
typedef DWORD OBJECT_TYPE;
```

```csharp
public enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
```

## <a name="fields"></a>Campi
 `OBJECT_TYPE_BOOLEAN`\
 Indica che l'oggetto è un valore booleano.

 `OBJECT_TYPE_CHAR`\
 Indica che l'oggetto è un carattere.

 `OBJECT_TYPE_I1`\
 Indica che l'oggetto è un intero con segno a un byte.

 `OBJECT_TYPE_U1`\
 Indica che l'oggetto è un intero senza segno a un byte.

 `OBJECT_TYPE_I2`\
 Indica che l'oggetto è un intero con segno a due byte.

 `OBJECT_TYPE_U2`\
 Indica che l'oggetto è un intero senza segno a due byte.

 `OBJECT_TYPE_I4`\
 Indica che l'oggetto è un intero con segno a quattro byte.

 `OBJECT_TYPE_U4`\
 Indica che l'oggetto è un intero senza segno a quattro byte.

 `OBJECT_TYPE_I8`\
 Indica che l'oggetto è un intero con segno a otto byte.

 `OBJECT_TYPE_U8`\
 Indica che l'oggetto è un intero senza segno a otto byte.

 `OBJECT_TYPE_R4`\
 Indica che l'oggetto è un numero a virgola mobile a quattro byte.

 `OBJECT_TYPE_R8`\
 Indica che l'oggetto è un numero a virgola mobile a otto byte.

 `OBJECT_TYPE_OBJECT`\
 Indica che l'oggetto è un oggetto.

 `OBJECT_TYPE_NULL`\
 Indica che l'oggetto è NULL.

 `OBJECT_TYPE_CLASS`\
 Indica che l'oggetto è una classe.

## <a name="remarks"></a>Osservazioni
 Passato come argomento per il [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) e [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) metodi.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)
