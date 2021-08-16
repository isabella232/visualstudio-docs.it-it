---
description: Specifica i flag per le informazioni sul modulo di debug.
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: abdd04428695e105b7e9f3e14e740beef3a347574171296768af9a9637eaa592
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121415273"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
Specifica i flag per le informazioni sul modulo di debug.

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

## <a name="fields"></a>Campi
 `MIF_NONE`\
 Inizializzare/usare nessuno dei campi nella struttura .

 `MIF_NAME`\
 Inizializzare/usare `m_bstrName` il campo nella [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struttura .

 `MIF_URL`\
 Inizializzare/usare `m_bstrUrl` il campo nella struttura `MODULE_INFO` .

 `MIF_VERSION`\
 Inizializzare/usare `m_bstrVersion` il campo nella struttura `MODULE_INFO` .

 `MIF_DEBUGMESSAGE`\
 Inizializzare/usare `m_bstrDebugMessage` il campo nella struttura `MODULE_INFO` .

 `MIF_LOADADDRESS`\
 Inizializzare/usare `m_addrLoadAddress` il campo nella struttura `MODULE_INFO` .

 `MIF_PREFFEREDADDRESS`\
 Inizializzare/usare `m_addrPreferredLoadAddress` il campo nella struttura `MODULE_INFO` .

 `MIF_SIZE`\
 Inizializzare/usare `m_dwSize` il campo nella struttura `MODULE_INFO` .

 `MIF_LOADORDER`\
 Inizializzare/usare `m_dwLoadOrder` il campo nella struttura `MODULE_INFO` .

 `MIF_TIMESTAMP`\
 Inizializzare/usare `m_TimeStamp` il campo nella struttura `MODULE_INFO` .

 `MIF_URLSYMBOLLOCATION`\
 Inizializzare/usare `m_bstrUrlSymbolLocation` il campo nella struttura `MODULE_INFO` .

 `MIF_FLAGS`\
 Inizializzare/usare `m_dwModuleFlags` il campo nella struttura `MODULE_INFO` .

 `MIF_ALLFIELDS`\
 Inizializzare/usare tutti i campi nella `MODULE_INFO` struttura .

## <a name="remarks"></a>Commenti
 Questi valori vengono passati come argomento al [metodo GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) per indicare quali campi della [struttura](../../../extensibility/debugger/reference/module-info.md) MODULE_INFO devono essere inizializzati.

 Questi valori vengono usati anche nella `MODULE_INFO` struttura per indicare quali campi vengono usati e validi.

 Questi flag possono essere combinati con un bit per `OR` bit.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
