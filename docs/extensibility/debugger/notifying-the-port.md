---
title: Notifica alla porta | Microsoft Docs
description: Informazioni su come viene notificata la porta dopo l'avvio di un programma. Questo articolo contiene una descrizione dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 1aaa319f0c6cd545e1f319ab7c8c510f694529d7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710328"
---
# <a name="notify-the-port"></a>Inviare una notifica alla porta
Dopo l'avvio di un programma, è necessario ricevere una notifica alla porta, come indicato di seguito:

1. Quando una porta riceve un nuovo nodo di programma, invia un evento di creazione del programma alla sessione di debug. L'evento contiene un'interfaccia che rappresenta il programma.

2. La sessione di debug esegue una query sul programma per l'identificatore di un motore di debug (DE) a cui è possibile connettersi.

3. La sessione di debug verifica se de è in elenco di DE consentite per il programma. La sessione di debug ottiene questo elenco dalle impostazioni del programma attivo della soluzione, originariamente passate al pacchetto di debug.

    Il de deve essere nell'elenco consentito oppure il de non verrà collegato al programma.

   A livello di codice, quando una porta riceve per la prima volta un nuovo nodo di programma, crea [un'interfaccia IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) per rappresentare il programma.

> [!NOTE]
> Questa operazione non deve essere confusa con `IDebugProgram2` l'interfaccia creata successivamente dal motore di debug.

 La porta invia un evento di creazione del programma [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) al gestore di debug sessione (SDM) tramite un'interfaccia `IConnectionPoint` COM.

> [!NOTE]
> Questa operazione non deve essere confusa con `IDebugProgramCreateEvent2` l'interfaccia , che viene inviata in un secondo momento dal de.

 Insieme all'interfaccia eventi stessa, la porta invia le interfacce [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)e [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) che rappresentano rispettivamente la porta, il processo e il programma. SDM chiama [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) per ottenere il GUID del de che può eseguire il debug del programma. Il GUID è stato originariamente ottenuto [dall'interfaccia IDebugProgramNode2.](../../extensibility/debugger/reference/idebugprogramnode2.md)

 SDM verifica se il de è nell'elenco di DE consentite. SDM ottiene questo elenco dalle impostazioni del programma attivo della soluzione, originariamente passate al pacchetto di debug. Il de deve essere nell'elenco consentito oppure non verrà collegato al programma.

 Una volta nota l'identità del de, SDM è pronta per collegarla al programma.

## <a name="see-also"></a>Vedi anche
- [Avvio di un programma](../../extensibility/debugger/launching-a-program.md)
- [Collegamento dopo un avvio](../../extensibility/debugger/attaching-after-a-launch.md)
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
