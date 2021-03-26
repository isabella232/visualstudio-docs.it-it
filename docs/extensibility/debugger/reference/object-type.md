---
description: Specifica il tipo di un oggetto dall'analizzatore di espressioni.
title: OBJECT_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 80ef6cce37967d61611ac48f60aaf5b2a1d184f1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082384"
---
# <a name="object_type"></a>Object_Type
Specifica il tipo di un oggetto dall'analizzatore di espressioni.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_OBJECT_TYPE { 
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
public enum enum_OBJECT_TYPE { 
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
 Indica che l'oggetto è una Unsigned Integer a un byte.

 `OBJECT_TYPE_I2`\
 Indica che l'oggetto è un intero con segno a 2 byte.

 `OBJECT_TYPE_U2`\
 Indica che l'oggetto è una Unsigned Integer a due byte.

 `OBJECT_TYPE_I4`\
 Indica che l'oggetto è un intero con segno a 4 byte.

 `OBJECT_TYPE_U4`\
 Indica che l'oggetto è un Unsigned Integer a quattro byte.

 `OBJECT_TYPE_I8`\
 Indica che l'oggetto è un intero con segno a otto byte.

 `OBJECT_TYPE_U8`\
 Indica che l'oggetto è un Unsigned Integer a otto byte.

 `OBJECT_TYPE_R4`\
 Indica che l'oggetto è un numero a virgola mobile a quattro byte.

 `OBJECT_TYPE_R8`\
 Indica che l'oggetto è un numero a virgola mobile a 8 byte.

 `OBJECT_TYPE_OBJECT`\
 Indica che l'oggetto è un oggetto.

 `OBJECT_TYPE_NULL`\
 Indica che l'oggetto è NULL.

 `OBJECT_TYPE_CLASS`\
 Indica che l'oggetto è una classe.

## <a name="remarks"></a>Commenti
 Passato come argomento ai metodi [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) e [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) .

## <a name="requirements"></a>Requisiti
 Intestazione: EE. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)
