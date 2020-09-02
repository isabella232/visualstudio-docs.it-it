---
title: IDebugMemoryContext2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f5a0533e2f7ce50dce7ccdf1285e4ab28a4b7a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146361"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta una posizione nello spazio degli indirizzi del computer in cui è in esecuzione il programma di cui è in corso il debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un indirizzo in memoria.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) o [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) restituisce questa interfaccia. Inoltre, le chiamate a [Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) e [Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) restituiscono nuove copie di questa interfaccia dopo l'applicazione dell'operazione aritmetica appropriata.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 La tabella seguente illustra i metodi di `IDebugMemoryContext2` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Ottiene il nome visualizzabile dall'utente per questo contesto.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Ottiene informazioni che descrivono questo contesto.|  
|[Aggiungere](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Aggiunge un valore specificato all'indirizzo del contesto corrente per creare un nuovo contesto.|  
|[Sottrazione](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Sottrae un valore specificato dall'indirizzo del contesto corrente per creare un nuovo contesto.|  
|[Confronta](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Confronta due contesti nel modo indicato dai flag di confronto.|  
  
## <a name="remarks"></a>Osservazioni  
 La finestra **memoria** di Visual Studio chiama [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) per ottenere l' `IDebugMemoryContext2` interfaccia che contiene l'espressione valutata utilizzata per l'indirizzo di memoria. Questo contesto viene quindi passato a [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) e [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) per specificare l'indirizzo per la lettura o la scrittura.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
