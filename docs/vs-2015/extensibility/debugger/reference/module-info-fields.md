---
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b80235f4ae769acbe3c61ad4b597898ee774d6a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547325"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica i flag per le informazioni sul modulo di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
 MIF_NONE  
 Inizializzare/usare nessuno dei campi nella struttura.  
  
 MIF_NAME  
 Inizializza/usa il `m_bstrName` campo nella struttura [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) .  
  
 MIF_URL  
 Inizializza/usa il `m_bstrUrl` campo nella `MODULE_INFO` struttura.  
  
 MIF_VERSION  
 Inizializza/usa il `m_bstrVersion` campo nella `MODULE_INFO` struttura.  
  
 MIF_DEBUGMESSAGE  
 Inizializza/usa il `m_bstrDebugMessage` campo nella `MODULE_INFO` struttura.  
  
 MIF_LOADADDRESS  
 Inizializza/usa il `m_addrLoadAddress` campo nella `MODULE_INFO` struttura.  
  
 MIF_PREFFEREDADDRESS  
 Inizializza/usa il `m_addrPreferredLoadAddress` campo nella `MODULE_INFO` struttura.  
  
 MIF_SIZE  
 Inizializza/usa il `m_dwSize` campo nella `MODULE_INFO` struttura.  
  
 MIF_LOADORDER  
 Inizializza/usa il `m_dwLoadOrder` campo nella `MODULE_INFO` struttura.  
  
 MIF_TIMESTAMP  
 Inizializza/usa il `m_TimeStamp` campo nella `MODULE_INFO` struttura.  
  
 MIF_URLSYMBOLLOCATION  
 Inizializza/usa il `m_bstrUrlSymbolLocation` campo nella `MODULE_INFO` struttura.  
  
 MIF_FLAGS  
 Inizializza/usa il `m_dwModuleFlags` campo nella `MODULE_INFO` struttura.  
  
 MIF_ALLFIELDS  
 Inizializzare/utilizzare tutti i campi della `MODULE_INFO` struttura.  
  
## <a name="remarks"></a>Osservazioni  
 Questi valori vengono passati come argomento al metodo [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) per indicare quali campi della struttura [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) devono essere inizializzati.  
  
 Questi valori vengono inoltre utilizzati nella `MODULE_INFO` struttura per indicare quali campi vengono utilizzati e validi.  
  
 Questi flag possono essere combinati con un bit per bit `OR` .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
