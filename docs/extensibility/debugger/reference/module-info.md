---
title: MODULE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e3a11e368b6260d00f3f6ed0b19d94aa26bd31a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683610"
---
# <a name="moduleinfo"></a>MODULE_INFO
Descrive un particolare modulo (DLL, EXE o assembly).

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

## <a name="members"></a>Membri
 dwValidFields una combinazione di flag dal [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) enumerazione che specifica quali campi vengono compilati.

 m_bstrName il nome del modulo.

 m_bstrUrl l'URL del modulo.

 m_bstrVersion la versione del modulo.

 m_bstrDebugMessage un messaggio facoltativo sul modulo, ad esempio, "non è possibile caricare i simboli."

 m_addrLoadAddress il modulo Carica l'indirizzo.

 m_addrPreferredLoadAddress l'indirizzo di caricamento preferito del modulo.

 m_dwSize le dimensioni del modulo.

 m_dwLoadOrder l'ordine di caricamento del modulo.

 m_TimeStamp l'ora che dell'ultima modifica apportata al file di simboli.

 m_bstrUrlSymbolLocation il percorso del file di simboli (ad esempio, ".\\") specificato nel modulo. Utilizzato come una posizione di partenza per trovare i simboli per un modulo.

 m_dwModuleFlags una combinazione di flag dal [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) enumerazione che descrive il modulo.

## <a name="remarks"></a>Note
 Questa struttura viene passata per il [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) in cui viene compilato nel metodo.

 Questa struttura corrisponde a ogni modulo nel **moduli** finestra.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)