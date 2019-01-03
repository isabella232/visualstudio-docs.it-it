---
title: IDebugProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a7ee7d44d6087ea53cf0ae063ce3bcb7473157aa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826179"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Questa interfaccia rappresenta un programma in esecuzione in un processo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) e un fornitore di porte personalizzate implementano questa interfaccia per rappresentare un programma in un processo. Gestore di sessione di debug (SDM) implementa anche questa interfaccia per fornire informazioni al [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Il [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) evento restituisce questa interfaccia per un nuovo programma. Questa interfaccia viene inoltre utilizzata come parametro per molti metodi in più interfacce.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugProgram2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Enumera i thread che sono in esecuzione in questo programma.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Ottiene il nome del programma.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Ottiene il processo che questo programma è in esecuzione.|  
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Termina il programma.|  
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Collega a questo programma.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Determina se è possibile scollegare un motore di debug (DE) dal programma.|  
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Scollega debugger da questo programma.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Ottiene un identificatore univoco globale per il programma.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Ottiene le proprietà del programma.|  
|[Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continua l'esecuzione di questo programma da uno stato arrestato. Qualsiasi stato di esecuzione precedente viene cancellata.|  
|[Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continua l'esecuzione di questo programma da uno stato arrestato. Qualsiasi stato di esecuzione precedente viene mantenuta.|  
|[Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Esegue un passaggio.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Le richieste che questo programma di arresta l'esecuzione successiva ora una parte del codice di esecuzioni di thread.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Ottiene il nome e l'identificatore del motore di debug (DE) eseguire il programma.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Enumera i contesti di codice per una determinata posizione nel file di origine.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Ottiene i byte di memoria per il programma.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Ottiene il flusso disassembly per questo programma o parte di questo programma.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Enumera i moduli che questo programma è stata caricata ed è in esecuzione.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Ottiene l'aggiornamento di modifica e Continuazione per il programma.<br /><br /> Un motore di debug personalizzato può neimplementuje metodu questo metodo (l'app deve sempre restituire `E_NOTIMPL`).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Enumera i percorsi del codice di questo programma.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Scrive un dump di un file.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Note  
 Un programma è un contenitore di thread in esecuzione in una particolare architettura di runtime, mentre un processo è costituito da uno o più programmi.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Avanti](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Collegare](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)