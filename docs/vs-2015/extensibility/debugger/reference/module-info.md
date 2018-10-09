---
title: MODULE_INFO | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 95972779db412ad87883fbb3ba5d4fbbc1ee1cc1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530429"
---
# <a name="moduleinfo"></a>MODULE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [MODULE_INFO](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/module-info).  
  
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
 Una combinazione di flag dal [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) enumerazione che specifica quali campi vengono compilati.  
  
 m_bstrName  
 Nome del modulo.  
  
 m_bstrUrl  
 L'URL del modulo.  
  
 m_bstrVersion  
 La versione del modulo.  
  
 m_bstrDebugMessage  
 Un messaggio facoltativo sul modulo, ad esempio, "non è possibile caricare i simboli."  
  
 m_addrLoadAddress  
 L'indirizzo di caricamento del modulo.  
  
 m_addrPreferredLoadAddress  
 L'indirizzo di caricamento preferito del modulo.  
  
 m_dwSize  
 Le dimensioni del modulo.  
  
 m_dwLoadOrder  
 L'ordine di caricamento del modulo.  
  
 m_TimeStamp  
 L'ora che dell'ultima modifica apportata al file di simboli.  
  
 m_bstrUrlSymbolLocation  
 Il percorso del file di simboli (ad esempio, ".\\") specificato nel modulo. Utilizzato come una posizione di partenza per trovare i simboli per un modulo.  
  
 m_dwModuleFlags  
 Una combinazione di flag dal [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) enumerazione che descrive il modulo.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene passata per il [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) in cui viene compilato nel metodo.  
  
 Questa struttura corrisponde a ogni modulo nel **moduli** finestra.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
