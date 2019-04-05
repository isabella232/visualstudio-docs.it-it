---
title: IDebugEngineLaunch2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ccbe76d800be035bc39caa477955b91bf21c074e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954859"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
