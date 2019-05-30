---
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b8080710b3225f025c329e0c5cb42331e1a059f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346798"
---
# <a name="moduleflags"></a>MODULE_FLAGS
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
 Non specifica nessun modulo.

 `MODULE_FLAG_SYSTEM`\
 Specifica un modulo di sistema.

 `MODULE_FLAG_SYMBOLS`\
 Specifica un modulo di simboli.

 `MODULE_FLAG_64BIT`\
 Specifica un modulo a 64 bit.

 `MODULE_FLAG_OPTIMIZED`\
 Specifica che il modulo è stato ottimizzato. Questo stato si riflette nel **moduli** finestra.

 `MODULE_FLAG_UNOPTIMIZED`\
 Specifica che il modulo non è stato ottimizzato. Questo stato si riflette nel **moduli** finestra. Questo è lo stato predefinito.

## <a name="remarks"></a>Note
 Utilizzato per il `m_dwModuleFlags` membro della [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struttura.

 Questi flag possono essere combinati con un bit per bit `OR`.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)