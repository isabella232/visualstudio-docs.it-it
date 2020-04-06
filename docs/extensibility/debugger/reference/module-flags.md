---
title: proprietà MODULE_FLAGS . Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714261"
---
# <a name="module_flags"></a>MODULE_FLAGS
Utilizzato per descrivere un modulo.

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
 Specifica un modulo di simbolo.

 `MODULE_FLAG_64BIT`\
 Specifica un modulo a 64 bit.

 `MODULE_FLAG_OPTIMIZED`\
 Specifica che il modulo è stato ottimizzato. Questo stato si riflette nella finestra **Moduli.**

 `MODULE_FLAG_UNOPTIMIZED`\
 Specifica che il modulo non è stato ottimizzato. Questo stato si riflette nella finestra **Moduli.** Questo è lo stato predefinito.

## <a name="remarks"></a>Osservazioni
 Utilizzato per `m_dwModuleFlags` il membro della [struttura MODULE_INFO.](../../../extensibility/debugger/reference/module-info.md)

 Questi flag possono essere combinati `OR`con un oggetto .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
