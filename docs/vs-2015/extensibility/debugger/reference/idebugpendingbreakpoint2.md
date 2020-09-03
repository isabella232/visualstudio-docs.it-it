---
title: IDebugPendingBreakpoint2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1238fcbce22db3f3bc3e32019aac886c79d0c114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201031"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta un punto di interruzione pronto per l'associazione a una posizione di codice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia come parte del supporto per i punti di interruzione.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) crea un punto di interruzione in sospeso da un'interfaccia [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) . Una chiamata a [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crea un' `IDebugBreakpoint2` interfaccia che rappresenta un punto di interruzione associato nel programma.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 La tabella seguente illustra i metodi di `IDebugPendingBreakpoint2` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina se il punto di interruzione in sospeso può essere associato a una posizione di codice.|  
|[Associare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Associa questo punto di interruzione in sospeso a una o più posizioni di codice.|  
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ottiene lo stato del punto di interruzione in sospeso.|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ottiene la richiesta del punto di interruzione utilizzata per creare il punto di interruzione in sospeso.|  
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Consente di abilitare o disabilitare lo stato virtualizzato del punto di interruzione in sospeso.|  
|[Attiva](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Attiva o imposta lo stato di abilitazione del punto di interruzione in sospeso.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Imposta o modifica la condizione associata a questo punto di interruzione in sospeso.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Imposta o modifica il numero di passaggi associato a questo punto di interruzione in sospeso.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera tutti i punti di interruzione associati da questo punto di interruzione in sospeso.|  
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera tutti i punti di interruzione di errore derivanti da questo punto di interruzione in sospeso.|  
|[Elimina](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Elimina il punto di interruzione in sospeso e tutti i punti di interruzione associati.|  
  
## <a name="remarks"></a>Osservazioni  
 `IDebugPendingBreakpoint2` può essere considerato come un provider di tutte le informazioni necessarie per associare un punto di interruzione al codice che può essere applicato a uno o più programmi.  
  
 Un punto di interruzione in sospeso può produrre potenzialmente più di un punto di interruzione associato. Un punto di interruzione in un modello di tipo C++, ad esempio, potrebbe generare un punto di interruzione associato per ogni istanza univoca di tale modello.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
