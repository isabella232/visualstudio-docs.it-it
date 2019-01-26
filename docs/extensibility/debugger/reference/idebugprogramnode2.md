---
title: IDebugProgramNode2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de17039a10137ba6fb0075b9943d0771eb166e33
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981103"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
Questa interfaccia rappresenta un programma che è possibile eseguire il debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un motore di debug (DE) o un fornitore di porte personalizzato implementa questa interfaccia per rappresentare un programma che è possibile eseguire il debug. Questa interfaccia viene implementata in genere sullo stesso oggetto che implementa il [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia. Questa interfaccia è registrata con [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] chiamando [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) restituire questa interfaccia. Un fornitore di porte personalizzato riceve questa interfaccia tramite una chiamata a [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Un CRI riceve questa interfaccia tramite una chiamata a [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugProgramNode2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Ottiene il nome di un programma.|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Ottiene il nome del processo di hosting di un programma.|  
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Ottiene l'identificatore di processo di sistema per il processo di hosting di un programma.|  
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|DEPRECATO. NON USARE.|  
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|DEPRECATO. NON USARE. Vedere le [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaccia per un approccio alternativo.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Ottiene il nome e l'identificatore della DE in esecuzione questo programma.|  
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|DEPRECATO. NON USARE.|  
  
## <a name="remarks"></a>Note  
 Gestore di sessione di debug (SDM) chiama in genere [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) per ottenere questa interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [Collegare](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)