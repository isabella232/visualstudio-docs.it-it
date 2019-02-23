---
title: Notifica della porta | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b022cca2b69c8cb80b24fa34e3b020923cff4022
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689200"
---
# <a name="notify-the-port"></a>La porta di notifica
Dopo aver avviato un programma, la porta deve ricevere una notifica, come indicato di seguito:

1. Quando una porta riceve un nuovo nodo di programma, invia un evento di creazione del programma tornare alla sessione di debug. L'evento è caratterizzata da un'interfaccia che rappresenta il programma.

2. Il programma per l'identificatore di un motore di debug (DE) che è possibile collegare a una query nella sessione di debug.

3. La sessione di debug controlla se il DE è nell'elenco dei consentiti DEs per il programma. La sessione di debug ottiene questo elenco dalle impostazioni di programma attivo della soluzione, passate originariamente al metodo tramite il pacchetto di debug.

    Nell'elenco consentito deve essere la Germania, altrimenti la Germania non verrà collegato al programma.

   A livello di codice quando una porta riceve innanzitutto un nuovo nodo di programma, viene creato un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaccia per rappresentare il programma.

> [!NOTE]
>  Questo non deve essere confuso con il `IDebugProgram2` interfaccia creata in un secondo momento dal motore di debug (DE).

 La porta invia un' [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) evento di creazione di programma al gestore di debug di sessione (SDM) tramite COM `IConnectionPoint` interfaccia.

> [!NOTE]
>  Questo non deve essere confuso con il `IDebugProgramCreateEvent2` interfaccia, che verrà inviato in un secondo momento per la Germania.

 Con l'interfaccia evento stessa, la porta invia il [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), e [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfacce che rappresentano la porta, elaborano, e programma, rispettivamente. Le chiamate SDM [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) per ottenere il GUID della DE che è possibile eseguire il debug del programma. Il GUID è stato originariamente ottenuto il [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia.

 Il modello SDM controlla se il DE è nell'elenco dei consentiti DEs. Il modello SDM ottiene questo elenco dalle impostazioni di programma attivo della soluzione, passate originariamente al metodo tramite il pacchetto di debug. Nell'elenco consentito deve essere la Germania, altrimenti non verrà collegato al programma.

 Una volta che l'identità della DE è noto, il modello SDM è pronto per collegarlo al programma.

## <a name="see-also"></a>Vedere anche
- [Avvio di un programma](../../extensibility/debugger/launching-a-program.md)
- [Collegamento dopo un avvio](../../extensibility/debugger/attaching-after-a-launch.md)
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)