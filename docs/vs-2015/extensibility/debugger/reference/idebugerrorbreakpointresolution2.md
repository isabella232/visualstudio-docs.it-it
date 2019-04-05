---
title: IDebugErrorBreakpointResolution2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpointResolution2
helpviewer_keywords:
- IDebugErrorBreakpointResolution2
ms.assetid: b1234216-0ac8-461d-b2a7-54f60f8f3262
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e39a64cf0c7e5f41102f55c774526510bd3ea32d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969054"
---
# <a name="idebugerrorbreakpointresolution2"></a>IDebugErrorBreakpointResolution2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta la risoluzione di un errore del punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugErrorBreakpointResolution2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un motore di debug implementa questa interfaccia come parte del supporto per i punti di interruzione. Questa interfaccia viene utilizzata per segnalare in un punto di interruzione non è stato possibile eseguire l'associazione.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) restituisce questa interfaccia per specificare le informazioni in cui il punto di interruzione non è stato possibile eseguire l'associazione. Il [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) metodo ottiene il [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugErrorBreakpointResolution2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Ottiene il tipo di punto di interruzione.|  
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Ottiene le informazioni di risoluzione del punto di interruzione.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)   
 [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
