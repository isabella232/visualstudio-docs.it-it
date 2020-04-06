---
title: Interfacce necessarie per i fornitori di porte Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2aeb1f26f81d773e171aa3fed6b0f2ef976c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713157"
---
# <a name="required-port-supplier-interfaces"></a>Interfacce fornitore porta richieste
Un fornitore di porta deve implementare il [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfaccia. [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Un fornitore di porte fornisce le porte e le implementa. Pertanto, è necessario eseguire le interfacce seguenti:Therefore, it must run the following interfaces:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Descrive la porta ed enumera tutti i processi in esecuzione sulla porta.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Fornisce per l'avvio e la terminazione dei processi sulla porta.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Fornisce un meccanismo per i programmi in esecuzione all'interno del contesto di questa porta per notificare la creazione e l'eliminazione del nodo del programma. Per ulteriori informazioni, consultate [Nodi di programma.](../../extensibility/debugger/program-nodes.md)

- `IConnectionPointContainer`

  Fornisce un punto di connessione per [IDebugPortEvents2.](../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="port-supplier-operation"></a>Funzionamento del fornitore della porta
 Il sink [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) riceve notifiche quando processo e programmi vengono creati ed eliminati in una porta. È necessaria una porta per inviare [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) quando viene creato un processo e [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) quando un processo viene eliminato sulla porta. È inoltre necessaria una porta per inviare [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) quando viene creato un programma e [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) quando un programma viene eliminato in un processo in esecuzione sulla porta.

 Una porta invia in genere eventi di creazione ed eliminazione di programmi in risposta rispettivamente ai metodi [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) e [RemoveProgramNode.](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)

 Poiché una porta può avviare e terminare sia i processi fisici che i programmi logici, anche le interfacce seguenti devono essere implementate dal motore di debug:Because a port can launch and terminate both physical processes and logical programs, the following interfaces must also be implemented by the debug engine:

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  Descrive il processo fisico. Devono essere implementati almeno i seguenti metodi:

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [IdProcessoGetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  Fornisce un modo per il modello SDM di collegarsi e staccarsi da un processo.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Descrive il programma logico. Devono essere implementati almeno i seguenti metodi:

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  Fornisce un modo per il sDM di collegarsi a questo programma.

## <a name="see-also"></a>Vedere anche
- [Implementazione di un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)
