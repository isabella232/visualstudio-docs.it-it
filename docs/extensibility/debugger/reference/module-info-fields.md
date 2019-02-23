---
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4302a911e58a23bdcd58bb054c1fc90c389fed6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708385"
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
Specifica i flag per le informazioni del modulo di debug.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
typedef DWORD MODULE_INFO_FIELDS;
```

```csharp
public enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
```

## <a name="members"></a>Membri
 MIF_NONE Initialize/usare nessuno dei campi nella struttura.

 MIF_NAME Initialize/usare la `m_bstrName` campo le [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struttura.

 MIF_URL Initialize/usare la `m_bstrUrl` campo il `MODULE_INFO` struttura.

 MIF_VERSION Initialize/usare la `m_bstrVersion` campo il `MODULE_INFO` struttura.

 MIF_DEBUGMESSAGE Initialize/usare la `m_bstrDebugMessage` campo il `MODULE_INFO` struttura.

 MIF_LOADADDRESS Initialize/usare la `m_addrLoadAddress` campo il `MODULE_INFO` struttura.

 MIF_PREFFEREDADDRESS Initialize/usare la `m_addrPreferredLoadAddress` campo il `MODULE_INFO` struttura.

 MIF_SIZE Initialize/usare la `m_dwSize` campo il `MODULE_INFO` struttura.

 MIF_LOADORDER Initialize/usare la `m_dwLoadOrder` campo il `MODULE_INFO` struttura.

 MIF_TIMESTAMP Initialize/usare la `m_TimeStamp` campo il `MODULE_INFO` struttura.

 MIF_URLSYMBOLLOCATION Initialize/usare la `m_bstrUrlSymbolLocation` campo il `MODULE_INFO` struttura.

 MIF_FLAGS Initialize/usare la `m_dwModuleFlags` campo il `MODULE_INFO` struttura.

 MIF_ALLFIELDS Initialize/Usa tutti i campi nel `MODULE_INFO` struttura.

## <a name="remarks"></a>Note
 Questi valori vengono passati come argomento per il [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) metodo per indicare quali campi della [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struttura devono essere inizializzate.

 Questi valori vengono anche utilizzati nel `MODULE_INFO` struttura per indicare quali campi vengono usati e valido.

 Questi flag possono essere combinati con un bit per bit `OR`.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)