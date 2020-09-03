---
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 05a073b3663ff85fe3d68878999aaf1dfa9e0017
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198842"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica le informazioni da recuperare su un oggetto di riferimento di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membri  
 DEBUGREF_INFO_NAME  
 Inizializza/usa il `bstrName` campo nella struttura.  
  
 DEBUGREF_INFO_TYPE  
 Inizializza/usa il `bstrType` campo nella struttura.  
  
 DEBUGREF_INFO_VALUE  
 Inizializza/usa il `bstrValue` campo nella struttura.  
  
 DEBUGREF_INFO_ATTRIB  
 Inizializza/usa il `dwAttrib` campo nella struttura.  
  
 DEBUGREF_INFO_REFTYPE  
 Inizializza/usa il `dwRefType` campo nella struttura.  
  
 DEBUGREF_INFO_REF  
 Inizializza/usa il `pReference` campo nella struttura.  
  
 DEBUGREF_INFO_VALUE_AUTOEXPAND  
 Il campo del valore deve contenere il valore espanso automaticamente, se disponibile, per questo tipo di oggetto.  
  
 DEBUGREF_INFO_NONE  
 Indica che non è impostato alcun flag.  
  
 DEBUGREF_INFO_ALL  
 Indica una maschera dei flag.  
  
## <a name="remarks"></a>Osservazioni  
 Questi flag vengono passati ai metodi [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) e [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) per indicare quali campi della struttura [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) devono essere inizializzati.  
  
 Utilizzato per il `dwFields` membro della `DEBUG_REFERENCE_INFO` struttura per indicare quali campi vengono utilizzati e validi quando viene restituita la struttura.  
  
 Questi valori possono essere combinati con un bit per bit `OR` .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
