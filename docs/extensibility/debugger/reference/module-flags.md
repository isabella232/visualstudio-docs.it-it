---
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32b0e89a69bc39e43d4ff4fbc4e8f4d5816565ad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975387"
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
  
## <a name="members"></a>Membri  
 MODULE_FLAG_NONE  
 Non specifica nessun modulo.  
  
 MODULE_FLAG_SYSTEM  
 Specifica un modulo di sistema.  
  
 MODULE_FLAG_SYMBOLS  
 Specifica un modulo di simboli.  
  
 MODULE_FLAG_64BIT  
 Specifica un modulo a 64 bit.  
  
 MODULE_FLAG_OPTIMIZED  
 Specifica che il modulo è stato ottimizzato. Questo stato si riflette nel **moduli** finestra.  
  
 MODULE_FLAG_UNOPTIMIZED  
 Specifica che il modulo non è stato ottimizzato. Questo stato si riflette nel **moduli** finestra. Questo è lo stato predefinito.  
  
## <a name="remarks"></a>Note  
 Utilizzato per il `m_dwModuleFlags` membro della [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struttura.  
  
 Questi flag possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)