---
description: Questa interfaccia rappresenta un programma in esecuzione in un processo.
title: Interfaccia IDebugProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 4ada2036c6ae2f82066d6ed12344dc1f301c54d7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122087769"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Questa interfaccia rappresenta un programma in esecuzione in un processo.

## <a name="syntax"></a>Sintassi

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) e un fornitore di porte personalizzato implementano questa interfaccia per rappresentare un programma in un processo. La gestione del debug di sessione (SDM) implementa anche questa interfaccia per fornire informazioni a [Attach.](../../../extensibility/debugger/reference/idebugprogram2-attach.md)

## <a name="notes-for-callers"></a>Note per i chiamanti
 [L'evento IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) restituisce questa interfaccia per un nuovo programma. Questa interfaccia viene usata anche come parametro per molti metodi in più interfacce.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugProgram2` .

|Metodo|Descrizione|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Enumera i thread in esecuzione in questo programma.|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Ottiene il nome del programma.|
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Ottiene il processo in cui è in esecuzione il programma.|
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md).|Termina il programma.|
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Si collega a questo programma.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Determina se un motore di debug può disconnettersi dal programma.|
|[Scollega](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Scollega il debugger da questo programma.|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Ottiene un identificatore univoco globale per questo programma.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Ottiene le proprietà del programma.|
|[Eseguire](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continua l'esecuzione del programma da uno stato arrestato. Qualsiasi stato di esecuzione precedente viene cancellato.|
|[Continua](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continua l'esecuzione del programma da uno stato arrestato. Qualsiasi stato di esecuzione precedente viene mantenuto.|
|[Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Esegue un passaggio.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Richiede che l'esecuzione di questo programma venga interrotta alla successiva esecuzione del codice da parte di uno dei relativi thread.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Ottiene il nome e l'identificatore del motore di debug che esegue questo programma.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Enumera i contesti di codice per una determinata posizione in un file di origine.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Ottiene i byte di memoria per questo programma.|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Ottiene il flusso disassembly per questo programma o parte di questo programma.|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Enumera i moduli caricati e in esecuzione da questo programma.|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Ottiene l'aggiornamento ENC (Edit and Continue) per questo programma.<br /><br /> Un motore di debug personalizzato non implementa questo metodo (deve sempre restituire `E_NOTIMPL` ).|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Enumera i percorsi del codice di questo programma.|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Scrive un dump in un file.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Commenti
 Un programma è un contenitore di thread in esecuzione in una particolare architettura di run-time, mentre un processo è costituito da uno o più programmi.

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Avanti](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
