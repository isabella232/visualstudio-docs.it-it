---
title: IEnumDebugErrorBreakpoints2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95d001c0072442d07ae12f773a26290a95a2f7f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178479"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia enumera i punti di interruzione degli errori associati a un punto di interruzione in sospeso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugErrorBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia come parte del supporto per i punti di interruzione.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Visual Studio chiama [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) per ottenere questa interfaccia che rappresenta un elenco di punti di interruzione che non possono essere associati oppure [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) per ottenere questa interfaccia che rappresenta un elenco di punti di interruzione non associati.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 La tabella seguente illustra i metodi di `IEnumDebugErrorBreakpoints2` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Avanti](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Recupera un numero specificato di punti di interruzione di errore in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Ignora un numero specificato di punti di interruzione di errore in una sequenza di enumerazione.|  
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Ottiene il numero di punti di interruzione di errore in un enumeratore.|  
  
## <a name="remarks"></a>Osservazioni  
 Questa interfaccia contiene un elenco di interfacce [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) , ognuna delle quali descrive un punto di interruzione che non è stato possibile associare e il motivo per cui non è stato possibile associare. Visual Studio usa l' `IEnumDebugErrorBreakpoint2` interfaccia per aggiornare i punti di interruzione visualizzati nell'IDE.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
