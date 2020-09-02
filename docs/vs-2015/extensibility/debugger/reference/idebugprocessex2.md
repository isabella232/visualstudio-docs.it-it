---
title: IDebugProcessEx2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d2b036bd68aca126675f26b9823d2c786a0ae652
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675322"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia consente a gestione debug sessione (SDM) di notificare a un processo a cui si sta collegando o scollegando il processo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un fornitore di porte personalizzato implementa questa interfaccia sullo stesso oggetto dell'interfaccia [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) per:  
  
- Supporto del rilevamento delle sessioni connesse a un processo  
  
- Supporto della connessione automatica tra più motori di debug  
  
  Il fornitore della porta personalizzata può implementare questa interfaccia se viene scelta.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
  
- SDM chiama [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) su un' `IDebugProcess2` interfaccia per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 La tabella seguente illustra i metodi di `IDebugProcessEx2` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informa il processo che una sessione sta ora eseguendo il debug del processo.|  
|[Scollega](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informa il processo che una sessione non sta più eseguendo il debug del processo.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Aggiunge nodi di programma per un elenco di motori di debug.|  
  
## <a name="remarks"></a>Osservazioni  
 Questa interfaccia è privata tra il SDM e il processo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Portpriv. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
