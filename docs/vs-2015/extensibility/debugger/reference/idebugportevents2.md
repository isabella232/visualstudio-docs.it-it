---
title: IDebugPortEvents2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e0f6455e6df8db88b1aae1a7b7f6965c0ee524b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188534"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia invia una notifica a un listener (in genere la gestione del debug della sessione [SDM] o un motore di debug) di creazione e distruzione di processi e programmi su una porta specifica. Queste informazioni possono essere usate per presentare una visualizzazione in tempo reale dei processi e dei programmi in esecuzione sulla porta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio implementa in genere questa interfaccia per ricevere notifiche sulla creazione e la distruzione di programmi. Un motore di debug può inoltre implementare questa interfaccia per restare in ascolto di tali eventi di porta.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 È possibile eseguire query su tutte le interfacce [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) per un' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaccia. Il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> metodo per `IDebugPortEvents2` viene quindi chiamato nell' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaccia per ottenere un' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaccia. Infine, il <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> metodo nell' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaccia viene chiamato per inviare gli eventi tramite il metodo dell' [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md) .  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente viene illustrato il metodo di `IDebugPortEvents2` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Invia eventi che descrivono la creazione e l'eliminazione di processi e programmi sulla porta.|  
  
## <a name="remarks"></a>Osservazioni  
 `IDebugPortEvents2` viene usato anche da SDM per eseguire il debug di programmi eseguiti in un processo di cui è già in corso il debug.  
  
 Gli eventi porta vengono passati a SDM da questa interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
