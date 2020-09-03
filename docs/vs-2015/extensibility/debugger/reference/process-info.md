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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205011"
---
# <a name="process_info"></a>PROCESS_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Contiene informazioni su un processo.  
  
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
  
## <a name="members"></a>Membri  
 Campi  
 Combinazione di flag dell'enumerazione [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) che specificano i campi da compilare.  
  
 bstrFileName  
 Nome del percorso completo del processo. Equivale a chiamare il metodo [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) con il parametro `GN_FILENAME` .  
  
 bstrBaseName  
 Il nome file e l'estensione del processo. Equivale a chiamare il `IDebugProcess2::Getname` metodo con il parametro `GN_BASENAME` .  
  
 bstrTitle  
 Titolo del processo, se ne esiste uno. Equivale a chiamare il `IDebugProcess2::Getname` metodo con il parametro `GN_TITLE` .  
  
 ProcessId  
 Struttura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) che identifica il processo. Equivale a chiamare il metodo [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) .  
  
 dwSessionId  
 Identificatore della sessione di debug in cui è in esecuzione il processo.  
  
 bstrAttachedSessionName  
 Nome della sessione associata. Equivale a chiamare il metodo [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) .  
  
 CreationTime  
 Ora di creazione del processo.  
  
 Flags  
 Combinazione di flag dell'enumerazione [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) che specificano le proprietà del processo.  
  
## <a name="remarks"></a>Osservazioni  
 Questa struttura viene passata al metodo [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) dove viene compilata.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)   
 [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
