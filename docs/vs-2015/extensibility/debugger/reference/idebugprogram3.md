---
title: IDebugProgram3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae6de25108cf93314db17a2ac8de9ce8b1dcaed2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148602"
---
# <a name="idebugprogram3"></a>IDebugProgram3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta un programma in esecuzione in un processo ed estende l' [esecuzione](../../../extensibility/debugger/reference/idebugprogram2-execute.md) fornendo informazioni sul thread.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) e un fornitore di porta personalizzato implementano questa interfaccia per rappresentare un programma in un processo. Il gestore di debug della sessione implementa anche questa interfaccia per fornire informazioni da [collegare](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 L'evento [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) restituisce questa interfaccia per un nuovo programma. Questa interfaccia viene usata anche come parametro per molti metodi su più interfacce.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 La tabella seguente illustra i metodi di `IDebugProgram3` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Esegue il programma. Il thread viene restituito per fornire al debugger le informazioni sul thread visualizzato dall'utente durante l'esecuzione.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Osservazioni  
 Un programma è un contenitore di thread in esecuzione in un'architettura di runtime particolare, mentre un processo è costituito da uno o più programmi.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Prossimo](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Collegare](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
