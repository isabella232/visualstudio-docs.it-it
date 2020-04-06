---
title: proprietà MODULE_INFO_FIELDS . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa64147738a916d44b6924f193860f74bd10a855
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714322"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
Specifica i flag per le informazioni sul modulo di debug.

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

## <a name="fields"></a>Campi
 `MIF_NONE`\
 Inizializzare/utilizzare nessuno dei campi nella struttura.

 `MIF_NAME`\
 Inizializzare/utilizzare `m_bstrName` il campo nella struttura [MODULE_INFO.](../../../extensibility/debugger/reference/module-info.md)

 `MIF_URL`\
 Inizializzare/utilizzare `m_bstrUrl` il `MODULE_INFO` campo nella struttura.

 `MIF_VERSION`\
 Inizializzare/utilizzare `m_bstrVersion` il `MODULE_INFO` campo nella struttura.

 `MIF_DEBUGMESSAGE`\
 Inizializzare/utilizzare `m_bstrDebugMessage` il `MODULE_INFO` campo nella struttura.

 `MIF_LOADADDRESS`\
 Inizializzare/utilizzare `m_addrLoadAddress` il `MODULE_INFO` campo nella struttura.

 `MIF_PREFFEREDADDRESS`\
 Inizializzare/utilizzare `m_addrPreferredLoadAddress` il `MODULE_INFO` campo nella struttura.

 `MIF_SIZE`\
 Inizializzare/utilizzare `m_dwSize` il `MODULE_INFO` campo nella struttura.

 `MIF_LOADORDER`\
 Inizializzare/utilizzare `m_dwLoadOrder` il `MODULE_INFO` campo nella struttura.

 `MIF_TIMESTAMP`\
 Inizializzare/utilizzare `m_TimeStamp` il `MODULE_INFO` campo nella struttura.

 `MIF_URLSYMBOLLOCATION`\
 Inizializzare/utilizzare `m_bstrUrlSymbolLocation` il `MODULE_INFO` campo nella struttura.

 `MIF_FLAGS`\
 Inizializzare/utilizzare `m_dwModuleFlags` il `MODULE_INFO` campo nella struttura.

 `MIF_ALLFIELDS`\
 Inizializzare/utilizzare tutti i `MODULE_INFO` campi nella struttura.

## <a name="remarks"></a>Osservazioni
 Questi valori vengono passati come argomento per il [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) metodo per indicare quali campi della struttura [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) devono essere inizializzati.

 Questi valori vengono utilizzati anche nella `MODULE_INFO` struttura per indicare quali campi vengono utilizzati e validi.

 Questi flag possono essere combinati `OR`con un oggetto .

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
