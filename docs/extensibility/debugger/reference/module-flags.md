---
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78c7f24d64ffca667706c3b2fcebeffad16a9d85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714261"
---
# <a name="module_flags"></a>MODULE_FLAGS
Usato per descrivere un modulo.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
typedef DWORD MODULE_FLAGS;
```

```csharp
public enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
```

## <a name="fields"></a>Campi
 `MODULE_FLAG_NONE`\
 Non specifica alcun modulo.

 `MODULE_FLAG_SYSTEM`\
 Specifica un modulo di sistema.

 `MODULE_FLAG_SYMBOLS`\
 Specifica un modulo di simboli.

 `MODULE_FLAG_64BIT`\
 Specifica un modulo a 64 bit.

 `MODULE_FLAG_OPTIMIZED`\
 Specifica che il modulo è stato ottimizzato. Questo stato viene riflesso nella finestra **moduli** .

 `MODULE_FLAG_UNOPTIMIZED`\
 Specifica che il modulo non è stato ottimizzato. Questo stato viene riflesso nella finestra **moduli** . Questo è lo stato predefinito.

## <a name="remarks"></a>Osservazioni
 Utilizzato per il `m_dwModuleFlags` membro della struttura [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) .

 Questi flag possono essere combinati con un bit per bit `OR` .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
