---
title: IEnumDebugErrorBreakpoints2 | Microsoft Docs
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
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9ffe2d65f2a087d0b65cc4f122d446b0704924f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530491"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IEnumDebugErrorBreakpoints2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugerrorbreakpoints2).  
  
Questa interfaccia enumera i punti di interruzione di errore associati a un punto di interruzione in sospeso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugErrorBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia come parte del supporto per i punti di interruzione.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Le chiamate di Visual Studio [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) per ottenere questa interfaccia che rappresenta un elenco di punti di interruzione che non può essere associato, oppure [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) per ottenere questa interfaccia che rappresenta un elenco di punti di interruzione che non sono associate.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugErrorBreakpoints2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Recupera un determinato numero di punti di interruzione di errore in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Ignora un determinato numero di punti di interruzione di errore in una sequenza di enumerazione.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Ottiene il numero di punti di interruzione di errore in un enumeratore.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia contiene un elenco degli [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfacce, ognuno dei quali descrive un punto di interruzione che non è stato possibile associare e perché si potrebbe non essere associato. Visual Studio Usa il `IEnumDebugErrorBreakpoint2` interfaccia per aggiornare i punti di interruzione visualizzati nell'IDE.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

