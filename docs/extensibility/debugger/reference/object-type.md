---
title: OBJECT_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f0aafc5b41d9020c80cd2b86c9048db1d333bfd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62865440"
---
# <a name="objecttype"></a>OBJECT_TYPE
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

## <a name="members"></a>Membri
 OBJECT_TYPE_BOOLEAN indica che l'oggetto è un valore booleano.

 OBJECT_TYPE_CHAR indica che l'oggetto è un carattere.

 OBJECT_TYPE_I1 indica che l'oggetto è un intero con segno a 1 byte.

 OBJECT_TYPE_U1 indica che l'oggetto è un intero senza segno a 1 byte.

 OBJECT_TYPE_I2 indica che l'oggetto è un intero con segno a due byte.

 OBJECT_TYPE_U2 indica che l'oggetto è un intero senza segno a due byte.

 OBJECT_TYPE_I4 indica che l'oggetto è un intero con segno a quattro byte.

 OBJECT_TYPE_U4 indica che l'oggetto è un intero senza segno a quattro byte.

 OBJECT_TYPE_I8 indica che l'oggetto è un intero con segno a 8 byte.

 OBJECT_TYPE_U8 indica che l'oggetto è un intero senza segno a 8 byte.

 OBJECT_TYPE_R4 indica che l'oggetto è un numero a virgola mobile a quattro byte.

 OBJECT_TYPE_R8 indica che l'oggetto è un numero a virgola mobile a 8 byte.

 OBJECT_TYPE_OBJECT indica che l'oggetto è un oggetto.

 OBJECT_TYPE_NULL indica che l'oggetto è NULL.

 OBJECT_TYPE_CLASS indica che l'oggetto è una classe.

## <a name="remarks"></a>Note
 Passato come argomento per il [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) e [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) metodi.

## <a name="requirements"></a>Requisiti
 Intestazione: ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)