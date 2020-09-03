---
title: Interfacce del fornitore di porte obbligatorie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a065389a6b9b67b8bce82394569ce65afb0f8d55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821428"
---
# <a name="required-port-supplier-interfaces"></a>Interfacce obbligatorie dei fornitori di porte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un fornitore di porte deve implementare l'interfaccia [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) . [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Poiché un fornitore di porte fornisce porte, deve implementarle anche. Pertanto, deve implementare le interfacce seguenti:  
  
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Descrive la porta e può enumerare tutti i processi in esecuzione sulla porta.  
  
- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Fornisce per l'avvio e la terminazione dei processi sulla porta.  
  
- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Fornisce un meccanismo per i programmi in esecuzione nel contesto di questa porta per notificare la creazione e la distruzione del nodo del programma. Per altre informazioni, vedere [Program nodes](../../extensibility/debugger/program-nodes.md).  
  
- `IConnectionPointContainer`  
  
     Fornisce un punto di connessione per [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Operazione fornitore porta  
 Il sink [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) riceve notifiche quando i processi e i programmi vengono creati ed eliminati in una porta. Una porta è necessaria per inviare [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) quando viene creato un processo e [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) quando un processo viene distrutto sulla porta. Una porta è necessaria anche per inviare [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) quando viene creato un programma e [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) quando un programma viene eliminato in un processo in esecuzione sulla porta.  
  
 Una porta invia in genere gli eventi di creazione ed eliminazione del programma in risposta ai metodi [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) e [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) , rispettivamente.  
  
 Poiché una porta può avviare e terminare sia i processi fisici che i programmi logici, queste interfacce devono essere implementate anche dal motore di debug:  
  
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
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)
