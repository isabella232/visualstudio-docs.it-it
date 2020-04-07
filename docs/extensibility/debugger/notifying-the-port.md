---
title: Notifica alla porta Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738321"
---
# <a name="notify-the-port"></a>Notifica alla porta
Dopo aver avviato un programma, la porta deve essere notificata, come segue:

1. Quando una porta riceve un nuovo nodo di programma, invia un evento di creazione del programma alla sessione di debug. L'evento porta con sé un'interfaccia che rappresenta il programma.

2. La sessione di debug esegue una query sul programma per l'identificatore di un motore di debug (DE) che può connettersi.

3. La sessione di debug controlla per vedere se il DE è nell'elenco dei DEs consentiti per quel programma. La sessione di debug ottiene questo elenco dalle impostazioni del programma attivo della soluzione, originariamente passato dal pacchetto di debug.

    Il DE deve essere nell'elenco consentito, altrimenti il DE non sarà collegato al programma.

   A livello di codice, quando una porta riceve per la prima volta un nuovo nodo di programma, crea un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaccia per rappresentare il programma.

> [!NOTE]
> Questo non deve essere `IDebugProgram2` confuso con l'interfaccia creata in seguito dal motore di debug (DE).

 La porta invia un evento di creazione del programma [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) al gestore `IConnectionPoint` di sessione di debug (SDM) tramite un'interfaccia COM.

> [!NOTE]
> Questo non deve essere `IDebugProgramCreateEvent2` confuso con l'interfaccia, che viene inviata in seguito dal DE.

 Insieme all'interfaccia eventi stessa, la porta invia le interfacce [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)e [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) che rappresentano rispettivamente la porta, il processo e il programma. SDM chiama [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) per ottenere il GUID del DE che può eseguire il debug del programma. Il GUID è stato originariamente ottenuto dal [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia.

 Il File SDM verifica se il DE è nell'elenco dei DE consentiti. Il modello SDM ottiene questo elenco dalle impostazioni del programma attivo della soluzione, originariamente passato dal pacchetto di debug. Il DE deve essere nell'elenco consentito, altrimenti non sarà collegato al programma.

 Una volta che l'identità del DE è noto, il modello SDM è pronto per collegarlo al programma.

## <a name="see-also"></a>Vedere anche
- [Avvio di un programma](../../extensibility/debugger/launching-a-program.md)
- [Collegamento dopo un lancio](../../extensibility/debugger/attaching-after-a-launch.md)
- [Attività di debugDebugging tasks](../../extensibility/debugger/debugging-tasks.md)
