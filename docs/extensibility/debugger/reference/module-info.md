---
description: Descrive un modulo specifico (DLL, EXE o assembly).
title: MODULE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3ed9dd2e86c04771b8bb3b6c5fa87279d7bb41738b959b22ce51ce487029851c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338241"
---
# <a name="module_info"></a>MODULE_INFO
Descrive un modulo specifico (DLL, EXE o assembly).

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagMODULE_INFO { 
   MODULE_INFO_FIELDS dwValidFields;
   BSTR               m_bstrName;
   BSTR               m_bstrUrl;
   BSTR               m_bstrVersion;
   BSTR               m_bstrDebugMessage;
   UINT64             m_addrLoadAddress;
   UINT64             m_addrPreferredLoadAddress;
   DWORD              m_dwSize;
   DWORD              m_dwLoadOrder;
   FILETIME           m_TimeStamp;
   BSTR               m_bstrUrlSymbolLocation;
   MODULE_FLAGS       m_dwModuleFlags;
} MODULE_INFO;
```

```csharp
public struct MODULE_INFO { 
   public uint     dwValidFields;
   public string   m_bstrName;
   public string   m_bstrUrl;
   public string   m_bstrVersion;
   public string   m_bstrDebugMessage;
   public ulong    m_addrLoadAddress;
   public ulong    m_addrPreferredLoadAddress;
   public uint     m_dwSize;
   public uint     m_dwLoadOrder;
   public FILETIME m_TimeStamp;
   public string   m_bstrUrlSymbolLocation;
   public uint     m_dwModuleFlags;
};
```

## <a name="members"></a>Members
 `dwValidFields`\
 Combinazione di flag [dell'MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) che specifica quali campi vengono compilati.

 `m_bstrName`\
 Nome del modulo.

 `m_bstrUrl`\
 URL del modulo.

 `m_bstrVersion`\
 Versione del modulo.

 `m_bstrDebugMessage`\
 Messaggio facoltativo sul modulo, ad esempio "Non è possibile caricare i simboli".

 `m_addrLoadAddress`\
 Indirizzo di caricamento del modulo.

 `m_addrPreferredLoadAddress`\
 Indirizzo di carico preferito del modulo.

 `m_dwSize`\
 Dimensioni del modulo.

 `m_dwLoadOrder`\
 Ordine di caricamento del modulo.

 `m_TimeStamp`\
 Ora dell'ultima modifica del file di simboli.

 `m_bstrUrlSymbolLocation`\
 Percorso del file di simboli (ad esempio, ". \\ ") specificato nel modulo. Usato come posizione iniziale per trovare i simboli per un modulo.

 `m_dwModuleFlags`\
 Combinazione di flag [dell'MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) che descrive il modulo.

## <a name="remarks"></a>Commenti
 Questa struttura viene passata al [metodo GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) in cui viene compilata.

 Questa struttura corrisponde a ogni modulo elencato nella **finestra** Moduli.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
