---
title: Interfacce fornitore di porte | Microsoft Docs
description: Informazioni sulle interfacce che un fornitore di porte deve eseguire. Un fornitore di porte fornisce le porte e le implementa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 7f09a1cf675b9836e9bf909d13e3d8036f359928510e5c2f733701432e40a9fd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432956"
---
# <a name="required-port-supplier-interfaces"></a>Interfacce dei fornitori di porte necessarie
Un fornitore di porte deve implementare [l'interfaccia IDebugPortSupplier2.](../../extensibility/debugger/reference/idebugportsupplier2.md) [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Un fornitore di porte fornisce le porte e le implementa. Pertanto, deve eseguire le interfacce seguenti:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Descrive la porta ed enumera tutti i processi in esecuzione sulla porta.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Fornisce per l'avvio e la terminazione dei processi sulla porta.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Fornisce un meccanismo per i programmi in esecuzione all'interno del contesto di questa porta per notificare la creazione e l'eliminazione di nodi di programma. Per altre informazioni, vedere [Nodi di programma.](../../extensibility/debugger/program-nodes.md)

- `IConnectionPointContainer`

  Fornisce un punto di connessione [per IDebugPortEvents2.](../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="port-supplier-operation"></a>Port supplier operation (Operazione fornitore porta)
 Il sink [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) riceve notifiche quando i processi e i programmi vengono creati ed distrutti su una porta. È necessaria una porta per inviare [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) quando viene creato un processo e [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) quando un processo viene eliminato nella porta. È necessaria anche una porta per inviare [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) quando viene creato un programma e [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) quando un programma viene eliminato in un processo in esecuzione sulla porta.

 Una porta invia in genere eventi di creazione ed eliminazione programma in risposta rispettivamente ai [metodi AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) [e RemoveProgramNode.](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)

 Poiché una porta può avviare e terminare processi fisici e programmi logici, anche le interfacce seguenti devono essere implementate dal motore di debug:

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  Descrive il processo fisico. È necessario che siano implementati almeno i metodi seguenti:

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  Consente al modello SDM di collegarsi e disconnettersi da un processo.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Descrive il programma logico. È necessario che siano implementati almeno i metodi seguenti:

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  Fornisce un modo per collegare SDM a questo programma.

## <a name="see-also"></a>Vedi anche
- [Implementazione di un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)
