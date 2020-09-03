---
title: IDebugProgramNode2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1188f18e4a6f604dfd82991433bc0ffe0a07ad47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148573"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta un programma di cui è possibile eseguire il debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un motore di debug (DE) o un fornitore di porta personalizzato implementa questa interfaccia per rappresentare un programma di cui è possibile eseguire il debug. Questa interfaccia viene in genere implementata nello stesso oggetto che implementa l'interfaccia [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) . Questa interfaccia è registrata con [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] chiamando [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) per restituire questa interfaccia. Un fornitore di porte personalizzato riceve questa interfaccia tramite una chiamata a [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Un DE riceve questa interfaccia tramite una chiamata a [Connetti](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 La tabella seguente illustra i metodi di `IDebugProgramNode2` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Ottiene il nome di un programma.|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Ottiene il nome del processo che ospita un programma.|  
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Ottiene l'identificatore del processo di sistema per il processo che ospita un programma.|  
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|Deprecato. NON USARE.|  
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|Deprecato. NON USARE. Per un approccio alternativo, vedere l'interfaccia [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) .|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Ottiene il nome e l'identificatore del DE che esegue questo programma.|  
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|Deprecato. NON USARE.|  
  
## <a name="remarks"></a>Osservazioni  
 Il gestore di debug della sessione (SDM) chiama in genere [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) per ottenere questa interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [Collegare](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
