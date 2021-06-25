---
title: Interfacce dei fornitori di porte | Microsoft Docs
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
ms.workload:
- vssdk
ms.openlocfilehash: 96cf70302839a9de3c5fb0fec01136d9700ee17e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902371"
---
# <a name="required-port-supplier-interfaces"></a>Interfacce del fornitore di porte necessarie
Un fornitore di porte deve implementare [l'interfaccia IDebugPortSupplier2.](../../extensibility/debugger/reference/idebugportsupplier2.md) [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Un fornitore di porte fornisce le porte e le implementa. Pertanto, deve eseguire le interfacce seguenti:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Descrive la porta ed enumera tutti i processi in esecuzione sulla porta.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Fornisce per avviare e terminare i processi sulla porta.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Fornisce un meccanismo per i programmi in esecuzione all'interno del contesto di questa porta per notificare la creazione e la distruzione dei nodi del programma. Per altre informazioni, vedere [Nodi di programma](../../extensibility/debugger/program-nodes.md).

- `IConnectionPointContainer`

  Fornisce un punto di connessione per [IDebugPortEvents2.](../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="port-supplier-operation"></a>Operazione del fornitore di porte
 Il sink [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) riceve notifiche quando il processo e i programmi vengono creati ed distrutti su una porta. È necessaria una porta per inviare [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) quando viene creato un processo e [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) quando un processo viene eliminato automaticamente sulla porta. Una porta è necessaria anche per inviare [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) quando viene creato un programma e [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) quando un programma viene eliminato in un processo in esecuzione sulla porta.

 Una porta in genere invia eventi di creazione ed eliminazione programma in risposta rispettivamente ai [metodi AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) e [RemoveProgramNode.](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)

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

  Consente al modello SDM di connettersi e scollegarsi da un processo.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Descrive il programma logico. È necessario che siano implementati almeno i metodi seguenti:

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  Consente al modello SDM di connettersi a questo programma.

## <a name="see-also"></a>Vedere anche
- [Implementazione di un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)
