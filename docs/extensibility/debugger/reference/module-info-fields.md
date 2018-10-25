---
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cf01cb2573922adb5d8b5b4bc26b10b839009dda
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832852"
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
Specifica i flag per le informazioni del modulo di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_MODULE_INFO_FIELDS {   
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
public enum enum_MODULE_INFO_FIELDS {   
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
 MIF_NONE  
 Initialize/usare nessuno dei campi nella struttura.  
  
 MIF_NAME  
 Initialize/usare la `m_bstrName` campo le [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struttura.  
  
 MIF_URL  
 Initialize/usare la `m_bstrUrl` campo il `MODULE_INFO` struttura.  
  
 MIF_VERSION  
 Initialize/usare la `m_bstrVersion` campo il `MODULE_INFO` struttura.  
  
 MIF_DEBUGMESSAGE  
 Initialize/usare la `m_bstrDebugMessage` campo il `MODULE_INFO` struttura.  
  
 MIF_LOADADDRESS  
 Initialize/usare la `m_addrLoadAddress` campo il `MODULE_INFO` struttura.  
  
 MIF_PREFFEREDADDRESS  
 Initialize/usare la `m_addrPreferredLoadAddress` campo il `MODULE_INFO` struttura.  
  
 MIF_SIZE  
 Initialize/usare la `m_dwSize` campo il `MODULE_INFO` struttura.  
  
 MIF_LOADORDER  
 Initialize/usare la `m_dwLoadOrder` campo il `MODULE_INFO` struttura.  
  
 MIF_TIMESTAMP  
 Initialize/usare la `m_TimeStamp` campo il `MODULE_INFO` struttura.  
  
 MIF_URLSYMBOLLOCATION  
 Initialize/usare la `m_bstrUrlSymbolLocation` campo il `MODULE_INFO` struttura.  
  
 MIF_FLAGS  
 Initialize/usare la `m_dwModuleFlags` campo il `MODULE_INFO` struttura.  
  
 MIF_ALLFIELDS  
 Initialize/Usa tutti i campi nel `MODULE_INFO` struttura.  
  
## <a name="remarks"></a>Note  
 Questi valori vengono passati come argomento per il [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) metodo per indicare quali campi della [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struttura devono essere inizializzate.  
  
 Questi valori vengono anche utilizzati nel `MODULE_INFO` struttura per indicare quali campi vengono usati e valido.  
  
 Questi flag possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)