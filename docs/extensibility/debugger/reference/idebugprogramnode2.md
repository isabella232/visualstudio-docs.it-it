---
description: Questa interfaccia rappresenta un programma di cui è possibile eseguire il debug.
title: Interfaccia IDebugProgramNode2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 8775c8b726bbc75472da8b286fca5b7640c918a8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050559"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
Questa interfaccia rappresenta un programma di cui è possibile eseguire il debug.

## <a name="syntax"></a>Sintassi

```
IDebugProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un motore di debug (DE) o un fornitore di porte personalizzato implementa questa interfaccia per rappresentare un programma di cui è possibile eseguire il debug. Questa interfaccia viene in genere implementata nello stesso oggetto che implementa [l'interfaccia IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md) Questa interfaccia viene registrata con [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] chiamando [PublishProgramNode.](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) per restituire questa interfaccia. Un fornitore di porte personalizzato riceve questa interfaccia tramite una chiamata a [AddProgramNode.](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) Un de riceve questa interfaccia tramite una chiamata a [Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugProgramNode2` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Ottiene il nome di un programma.|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Ottiene il nome del processo che ospita un programma.|
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Ottiene l'identificatore del processo di sistema per il processo che ospita un programma.|
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|Deprecato. NON USARE.|
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|Deprecato. NON USARE. Vedere [l'interfaccia IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) per un approccio alternativo.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Ottiene il nome e l'identificatore del de che esegue il programma.|
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|Deprecato. NON USARE.|

## <a name="remarks"></a>Commenti
 La gestione del debug di sessione (SDM) chiama in genere [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) per ottenere questa interfaccia.

## <a name="requirements"></a>Requisiti
 Intestazione: Msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
