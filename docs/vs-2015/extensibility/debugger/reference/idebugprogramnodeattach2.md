---
title: IDebugProgramNodeAttach2 | Microsoft Docs
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
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ef3bedd5b5d501e6c0a60ef6958a8a3745b86865
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526312"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugProgramNodeAttach2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramnodeattach2).  
  
Consente a un nodo di programma ricevere una notifica di un tentativo di collegare al programma associato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata nella stessa classe che implementa il [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia per ricevere la notifica di un'operazione di connessione e fornire un'opportunità per annullare l'operazione di collegamento.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Ottenere questa interfaccia chiamando il `QueryInterface` metodo in un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) oggetto. Il [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metodo deve essere chiamato prima il [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodo per consentire al nodo di programma di arrestare il processo di collegamento.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Questa interfaccia implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Collega al programma associato oppure rinvia il processo di collegamento per il [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) (metodo).|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia è l'alternativa migliore all'oggetto deprecato [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) (metodo). Tutti i motori di debug vengono sempre caricati con il `CoCreateInstance` di funzione, vale a dire, creazione di istanze all'esterno di spazio degli indirizzi del programma sottoposto a debug.  
  
 Se una precedente implementazione del `IDebugProgramNode2::Attach_V7` metodo è stato semplicemente impostando il `GUID` del programma in fase di debug, quindi solo le [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metodo deve essere implementato.  
  
 Se una precedente implementazione del `IDebugProgramNode2::Attach_V7` usare il metodo di interfaccia di callback che è stato fornito, quindi dovrà essere spostati su un'implementazione di tale funzionalità il [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodo e il `IDebugProgramNodeAttach2` interfaccia non deve essere implementato.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Collegare](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)

