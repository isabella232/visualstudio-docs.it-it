---
title: IDebugEngineLaunch2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 06ca3d52c58ea1d8aff78936f8b7240e1b77e9c4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934265"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Utilizzato da un motore di debug (DE) per avviare e interrompere i programmi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata da un CRI personalizzato se dispone di requisiti speciali per l'avvio di un processo che non può essere gestito completamente da una porta personalizzata. Ciò avviene in genere quando la Germania fa parte di un interprete e il processo sottoposto a debug è uno script: l'interprete deve essere avviata prima di tutto e quindi lo script viene caricato e avviato. Una porta è possibile avviare l'interprete, ma lo script può richiedere una gestione speciale, ovvero dispone di un ruolo in cui la Germania. Questa interfaccia è implementata solo se sono presenti requisiti specifici per l'avvio di un programma che non può gestire una porta personalizzata.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene chiamata dal gestore di sessione di debug (SDM) se il modello SDM può ottenere questa interfaccia dal [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfaccia (tramite QueryInterface). Se è possibile ottenere questa interfaccia, il modello SDM sa che la Germania è previsti requisiti speciali e chiama questa interfaccia per avviare il programma anziché la porta come avviarlo.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugEngineLaunch2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Avvia un processo mediante il DE.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Riprende l'esecuzione del processo.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Determina se un processo può essere terminato.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Termina un processo.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)