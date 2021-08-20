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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160387"
---
# <a name="notify-the-port"></a>Inviare una notifica alla porta
Dopo l'avvio di un programma, la porta deve ricevere una notifica, come indicato di seguito:

1. Quando una porta riceve un nuovo nodo di programma, invia un evento di creazione del programma alla sessione di debug. L'evento contiene un'interfaccia che rappresenta il programma.

2. La sessione di debug esegue una query sul programma per l'identificatore di un motore di debug (DE) a cui è possibile connettersi.

3. La sessione di debug verifica se DE è in elenco di DE consentiti per il programma. La sessione di debug ottiene questo elenco dalle impostazioni del programma attivo della soluzione, originariamente passate dal pacchetto di debug.

    De deve essere in elenco consentiti, altrimenti de non verrà allegato al programma.

   A livello di codice, quando una porta riceve per la prima volta un nuovo nodo di programma, crea [un'interfaccia IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) per rappresentare il programma.

> [!NOTE]
> Questa operazione non deve essere confusa `IDebugProgram2` con l'interfaccia creata in seguito dal motore di debug.

 La porta invia un evento di creazione del programma [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) alla gestione del debug di sessione (SDM) tramite un'interfaccia `IConnectionPoint` COM.

> [!NOTE]
> Questo non deve essere confuso con `IDebugProgramCreateEvent2` l'interfaccia , che viene inviata in un secondo momento dal de.

 Insieme all'interfaccia evento stessa, la porta invia le interfacce [IDebugPort2,](../../extensibility/debugger/reference/idebugport2.md) [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)e [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) che rappresentano rispettivamente la porta, il processo e il programma. SDM chiama [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) per ottenere il GUID di DE in grado di eseguire il debug del programma. Il GUID è stato originariamente ottenuto [dall'interfaccia IDebugProgramNode2.](../../extensibility/debugger/reference/idebugprogramnode2.md)

 SDM verifica se DE è in elenco di DE consentiti. SDM ottiene questo elenco dalle impostazioni del programma attivo della soluzione, originariamente passate dal pacchetto di debug. Il de deve essere in elenco consentiti, altrimenti non verrà allegato al programma.

 Una volta nota l'identità di DE, SDM è pronto per collegarlo al programma.

## <a name="see-also"></a>Vedi anche
- [Avvio di un programma](../../extensibility/debugger/launching-a-program.md)
- [Collegamento dopo un avvio](../../extensibility/debugger/attaching-after-a-launch.md)
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
