---
title: PROCESS_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9ab05d85b55fd293b648603f067d135f703aff5e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205011"
---
# <a name="processinfo"></a>PROCESS_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Contiene informazioni sul processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
typedef struct tagPROCESS_INFO {   
   PROCESS_INFO_FIELDS Fields;  
   BSTR                bstrFileName;  
   BSTR                bstrBaseName;  
   BSTR                bstrTitle;  
   AD_PROCESS_ID       ProcessId;  
   DWORD               dwSessionId;  
   BSTR                bstrAttachedSessionName;  
   FILETIME            CreationTime;  
   PROCESS_INFO_FLAGS  Flags;  
} PROCESS_INFO;  
```  
  
```csharp  
public struct PROCESS_INFO {   
   public uint          Fields;  
   public string        bstrFileName;  
   public string        bstrBaseName;  
   public string        bstrTitle;  
   public AD_PROCESS_ID ProcessId;  
   public uint          dwSessionId;  
   public string        bstrAttachedSessionName;  
   public FILETIME      CreationTime;  
   public uint          Flags;  
};  
```  
  
## <a name="members"></a>Members  
 Campi  
 Una combinazione di flag dal [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) enumerazione che specificano quali campi vengono compilati.  
  
 bstrFileName  
 Nome e percorso completo del processo. Equivalente alla chiamata di [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) metodo con il parametro `GN_FILENAME`.  
  
 bstrBaseName  
 Il nome del file e l'estensione del processo. Equivalente alla chiamata di `IDebugProcess2::Getname` metodo con il parametro `GN_BASENAME`.  
  
 bstrTitle  
 Il titolo del processo, se presente. Equivalente alla chiamata di `IDebugProcess2::Getname` metodo con il parametro `GN_TITLE`.  
  
 ProcessId  
 Il [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struttura che identifica il processo. Equivalente alla chiamata di [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) (metodo).  
  
 dwSessionId  
 L'identificatore della sessione di debug che questo processo è in esecuzione in.  
  
 bstrAttachedSessionName  
 Nome della sessione associata. Equivalente alla chiamata di [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) (metodo).  
  
 CreationTime  
 Ora che il processo è stato creato.  
  
 Flag  
 Una combinazione di flag dal [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) enumerazione che specificano le proprietà del processo.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene passata per il [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) in cui viene compilato nel metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
