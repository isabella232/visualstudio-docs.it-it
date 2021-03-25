---
title: Interfacce del fornitore di porte obbligatorie | Microsoft Docs
description: Informazioni sulle interfacce che devono essere eseguite da un fornitore di porte. Un fornitore di porte fornisce le porte e le implementa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1f5755ce47a2b76c9a0d38b1f7eed3b38d64c876
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070609"
---
# <a name="required-port-supplier-interfaces"></a>Interfacce del fornitore di porte obbligatorie
Un fornitore di porte deve implementare l'interfaccia [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) . [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Un fornitore di porte fornisce le porte e le implementa. Pertanto, deve eseguire le interfacce seguenti:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Descrive la porta ed enumera tutti i processi in esecuzione sulla porta.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Fornisce per l'avvio e la terminazione dei processi sulla porta.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Fornisce un meccanismo per i programmi in esecuzione nel contesto di questa porta per notificare la creazione e la distruzione del nodo del programma. Per altre informazioni, vedere [Program nodes](../../extensibility/debugger/program-nodes.md).

- `IConnectionPointContainer`

  Fornisce un punto di connessione per [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).

## <a name="port-supplier-operation"></a>Operazione fornitore porta
 Il sink [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) riceve notifiche quando i processi e i programmi vengono creati ed eliminati in una porta. Una porta è necessaria per inviare [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) quando viene creato un processo e [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) quando un processo viene distrutto sulla porta. Una porta è necessaria anche per inviare [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) quando viene creato un programma e [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) quando un programma viene eliminato in un processo in esecuzione sulla porta.

 Una porta invia in genere gli eventi di creazione ed eliminazione del programma in risposta ai metodi [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) e [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) , rispettivamente.

 Poiché una porta può avviare e terminare sia i processi fisici che i programmi logici, le interfacce seguenti devono essere implementate anche dal motore di debug:

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  Descrive il processo fisico. È necessario implementare almeno i metodi seguenti:

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  Fornisce un modo per il collegamento e lo scollegamento di SDM da un processo.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Descrive il programma logico. È necessario implementare almeno i metodi seguenti:

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  Fornisce un modo per la connessione di SDM a questo programma.

## <a name="see-also"></a>Vedi anche
- [Implementazione di un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)
