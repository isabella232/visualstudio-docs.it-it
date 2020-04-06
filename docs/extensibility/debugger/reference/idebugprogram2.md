---
title: Proprietà IDebugProgram2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 150746197be4945b012717bef08e18ea57168177
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722728"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Questa interfaccia rappresenta un programma in esecuzione in un processo.

## <a name="syntax"></a>Sintassi

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug (DE) e un fornitore di porta personalizzato implementano questa interfaccia per rappresentare un programma in un processo. Il gestore di debug della sessione (SDM) implementa anche questa interfaccia per fornire informazioni a [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Note per i chiamanti
 L'evento [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) restituisce questa interfaccia per un nuovo programma. Questa interfaccia viene utilizzata anche come parametro per molti metodi su più interfacce.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono `IDebugProgram2`illustrati i metodi di .

|Metodo|Descrizione|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Enumera i thread in esecuzione in questo programma.|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Ottiene il nome del programma.|
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Ottiene il processo in cui è in esecuzione il programma.|
|[Terminare](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Termina questo programma.|
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Si collega a questo programma.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Determina se un motore di debug (DE) può disconnettersi dal programma.|
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Scollega il debugger da questo programma.|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Ottiene un identificatore univoco globale per questo programma.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Ottiene le proprietà del programma.|
|[Eseguire](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continua l'esecuzione del programma da uno stato arrestato. Qualsiasi stato di esecuzione precedente viene cancellato.|
|[Continuare](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continua l'esecuzione del programma da uno stato arrestato. Qualsiasi stato di esecuzione precedente viene mantenuto.|
|[Passaggio](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Esegue un passaggio.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Richiede che il programma interrompa l'esecuzione alla successiva esecuzione del codice di uno dei relativi thread.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Ottiene il nome e l'identificatore del motore di debug (DE) che esegue il programma.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Enumera i contesti di codice per una determinata posizione in un file di origine.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Ottiene i byte di memoria per questo programma.|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Ottiene il flusso di disassembly per questo programma o parte di questo programma.|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Enumera i moduli caricati dal programma.|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Ottiene l'aggiornamento di Modifica e continuazione (ENC) per questo programma.<br /><br /> Un motore di debug personalizzato non implementa `E_NOTIMPL`questo metodo (deve sempre restituire ).|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Enumera i percorsi di codice di questo programma.|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Scrive un dump in un file.|

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Osservazioni
 Un programma è un contenitore di thread in esecuzione in una particolare architettura di runtime, mentre un processo è costituito da uno o più programmi.

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Avanti](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
