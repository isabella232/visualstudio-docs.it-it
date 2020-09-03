---
title: MODULE_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 04a8756fd7eb2a4b938ebcd2d5f4754509b704e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205213"
---
# <a name="module_info"></a>MODULE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Descrive un particolare modulo (DLL, EXE o assembly).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
 dwValidFields  
 Combinazione di flag dell'enumerazione [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) che specifica i campi che vengono compilati.  
  
 m_bstrName  
 Nome del modulo.  
  
 m_bstrUrl  
 URL del modulo.  
  
 m_bstrVersion  
 Versione del modulo.  
  
 m_bstrDebugMessage  
 Un messaggio facoltativo sul modulo, ad esempio, "non è possibile caricare i simboli".  
  
 m_addrLoadAddress  
 Indirizzo di caricamento del modulo.  
  
 m_addrPreferredLoadAddress  
 Indirizzo di caricamento preferito del modulo.  
  
 m_dwSize  
 Dimensioni del modulo.  
  
 m_dwLoadOrder  
 Ordine di caricamento del modulo.  
  
 m_TimeStamp  
 Ora dell'Ultima modifica del file di simboli.  
  
 m_bstrUrlSymbolLocation  
 Percorso del file di simboli (ad esempio, ". \\ ") specificato nel modulo. Usato come posizione iniziale per trovare i simboli per un modulo.  
  
 m_dwModuleFlags  
 Combinazione di flag dell'enumerazione [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) che descrive il modulo.  
  
## <a name="remarks"></a>Osservazioni  
 Questa struttura viene passata al metodo [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) dove viene compilata.  
  
 Questa struttura corrisponde a ogni modulo elencato nella finestra **moduli** .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
