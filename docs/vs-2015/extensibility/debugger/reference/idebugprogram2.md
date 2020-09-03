---
title: IDebugProgram2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 372c119b6a841d7d4b349e85548914f7641b53d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148650"
---
# <a name="idebugprogram2"></a>IDebugProgram2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta un programma in esecuzione in un processo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) e un fornitore di porta personalizzato implementano questa interfaccia per rappresentare un programma in un processo. Il gestore di debug della sessione implementa anche questa interfaccia per fornire informazioni da [collegare](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 L'evento [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) restituisce questa interfaccia per un nuovo programma. Questa interfaccia viene usata anche come parametro per molti metodi su più interfacce.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 La tabella seguente illustra i metodi di `IDebugProgram2` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Enumera i thread in esecuzione in questo programma.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Ottiene il nome del programma.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Ottiene il processo in cui è in esecuzione il programma.|  
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md).|Termina il programma.|  
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Si connette al programma.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Determina se un motore di debug (DE) può scollegarsi dal programma.|  
|[Scollega](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Scollega il debugger dal programma.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Ottiene un identificatore univoco globale per il programma.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Ottiene le proprietà del programma.|  
|[Eseguire](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continua l'esecuzione del programma da uno stato interrotto. Qualsiasi stato di esecuzione precedente è stato cancellato.|  
|[Continua](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continua l'esecuzione del programma da uno stato interrotto. Viene mantenuto qualsiasi stato di esecuzione precedente.|  
|[Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Esegue un passaggio.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Richiede che il programma arresti l'esecuzione la volta successiva che uno dei thread esegue il codice.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Ottiene il nome e l'identificatore del motore di debug (DE) che esegue il programma.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Enumera i contesti di codice per una determinata posizione in un file di origine.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Ottiene i byte di memoria per il programma.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Ottiene il flusso di disassembly per il programma o parte di questo programma.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Enumera i moduli caricati ed eseguiti dal programma.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Ottiene l'aggiornamento di modifica e continuazione (ENC) per questo programma.<br /><br /> Un motore di debug personalizzato non implementa questo metodo (deve sempre restituire `E_NOTIMPL` ).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Enumera i percorsi del codice del programma.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Scrive un dump in un file.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Osservazioni  
 Un programma è un contenitore di thread in esecuzione in un'architettura di runtime particolare, mentre un processo è costituito da uno o più programmi.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Prossimo](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Collegare](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
