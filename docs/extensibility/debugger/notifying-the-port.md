---
title: Notifica della porta | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff94c20969e77bcc70af2f5a16137e09366a0d7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738321"
---
# <a name="notify-the-port"></a>Notificare la porta
Dopo l'avvio di un programma, la porta deve essere notificata, come indicato di seguito:

1. Quando una porta riceve un nuovo nodo di programma, invia un evento di creazione del programma alla sessione di debug. L'evento contiene un'interfaccia che rappresenta il programma.

2. La sessione di debug esegue una query sul programma per l'identificatore di un motore di debug (DE) che può connettersi a.

3. La sessione di debug controlla se il DE è nell'elenco di DEs consentiti per il programma. La sessione di debug ottiene questo elenco dalle impostazioni del programma attive della soluzione, passate in origine dal pacchetto di debug.

    Il DE deve trovarsi nell'elenco consentito, altrimenti il DE non verrà collegato al programma.

   A livello di codice, quando una porta riceve per la prima volta un nuovo nodo di programma, crea un'interfaccia [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) per rappresentare il programma.

> [!NOTE]
> Questa operazione non deve essere confusa con l' `IDebugProgram2` interfaccia creata in un secondo momento dal motore di debug (de).

 La porta Invia un evento di creazione di un programma [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) a gestione debug sessione (SDM) tramite un'interfaccia com `IConnectionPoint` .

> [!NOTE]
> Questa operazione non deve essere confusa con l' `IDebugProgramCreateEvent2` interfaccia, che viene inviata in un secondo momento da de.

 Insieme all'interfaccia evento, la porta Invia le interfacce [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)e [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , che rappresentano rispettivamente la porta, il processo e il programma. SDM chiama [IDebugProgram2:: GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) per ottenere il GUID del de che può eseguire il debug del programma. Il GUID è stato originariamente ottenuto dall'interfaccia [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) .

 SDM verifica se l'oggetto DE è presente nell'elenco di DEs consentiti. SDM ottiene questo elenco dalle impostazioni del programma attive della soluzione, passate originariamente dal pacchetto di debug. Il DE deve trovarsi nell'elenco consentito, altrimenti non verrà collegato al programma.

 Quando l'identità del DE è nota, il SDM è pronto per collegarlo al programma.

## <a name="see-also"></a>Vedere anche
- [Avvio di un programma](../../extensibility/debugger/launching-a-program.md)
- [Connessione dopo un avvio](../../extensibility/debugger/attaching-after-a-launch.md)
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
