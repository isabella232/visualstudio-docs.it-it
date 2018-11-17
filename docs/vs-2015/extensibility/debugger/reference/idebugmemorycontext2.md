---
title: IDebugMemoryContext2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d19bad3f5ec4459c6aacf7b6456be9afb956043a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741175"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta una posizione nello spazio degli indirizzi dei computer che esegue il programma sottoposto a debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un indirizzo in memoria.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) oppure [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) restituisce questa interfaccia. Inoltre, le chiamate a [Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) e [Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) restituire nuove copie di questa interfaccia viene applicato l'operazione aritmetica appropriato.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugMemoryContext2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Ottiene il nome visualizzabile dall'utente per questo contesto.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Ottiene informazioni che descrivono questo contesto.|  
|[Aggiungi](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Aggiunge un valore specificato all'indirizzo del contesto corrente per creare un nuovo contesto.|  
|[Sottrai](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Sottrae un valore specificato dall'indirizzo del contesto corrente per creare un nuovo contesto.|  
|[Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Confronta due contesti nel modo indicati dal flag di confronto.|  
  
## <a name="remarks"></a>Note  
 Visual Studio **memoria** finestra chiamate [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) per ottenere il `IDebugMemoryContext2` interfaccia che contiene l'espressione valutata utilizzata per l'indirizzo di memoria. In questo contesto viene quindi passato a [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) e [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) per specificare l'indirizzo per la lettura o scrittura.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)

