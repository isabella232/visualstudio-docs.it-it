---
title: Collegamento al | Microsoft Docs
description: Informazioni su Visual Studio il debugger che si collega a un programma dopo che il programma è stato registrato con la porta appropriata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 70576204c655725ea68908424b6caad145cf21f0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051079"
---
# <a name="attach-to-the-program"></a>Collegarsi al programma
Dopo aver registrato i programmi con la porta appropriata, è necessario collegare il debugger al programma di cui si vuole eseguire il debug.

## <a name="choose-how-to-attach"></a>Scegliere la modalità di collegamento
 Esistono tre modi in cui gestione debug sessione (SDM) tenta di connettersi al programma in fase di debug.

1. Per i programmi avviati dal motore di debug tramite il metodo [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) (tipico dei linguaggi interpretati, ad esempio), SDM ottiene l'interfaccia [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) dall'oggetto [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) associato al programma a cui viene collegato. Se SDM può ottenere `IDebugProgramNodeAttach2` l'interfaccia, SDM chiama quindi il [metodo OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Il metodo restituisce per indicare che non è stato collegato al programma e che è possibile eseguire altri tentativi di `IDebugProgramNodeAttach2::OnAttach` `S_OK` connessione al programma.

2. Se SDM può ottenere [l'interfaccia IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) dal programma a cui viene collegato, SDM chiama il [metodo Attach.](../../extensibility/debugger/reference/idebugprogramex2-attach.md) Questo approccio è tipico per i programmi avviati in remoto dal fornitore della porta.

3. Se il programma non può essere collegato tramite i metodi `IDebugProgramNodeAttach2::OnAttach` o , SDM carica il motore di debug (se non è già caricato) chiamando la funzione e quindi chiama il `IDebugProgramEx2::Attach` `CoCreateInstance` metodo [Attach.](../../extensibility/debugger/reference/idebugengine2-attach.md) Questo approccio è tipico per i programmi avviati in locale da un fornitore di porte.

    È anche possibile che un fornitore di porte personalizzato chiami il metodo nell'implementazione del metodo del fornitore `IDebugEngine2::Attach` di porte `IDebugProgramEx2::Attach` personalizzato. In genere, in questo caso, il fornitore di porte personalizzato avvia il motore di debug nel computer remoto.

   L'allegato viene ottenuto quando il gestore di debug della sessione (SDM) chiama il [metodo Attach.](../../extensibility/debugger/reference/idebugengine2-attach.md)

   Se si esegue la dea nello stesso processo dell'applicazione di cui eseguire il debug, è necessario implementare i metodi seguenti di [IDebugProgramNode2:](../../extensibility/debugger/reference/idebugprogramnode2.md)

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  Dopo aver `IDebugEngine2::Attach` chiamato il metodo , seguire questa procedura nell'implementazione del metodo `IDebugEngine2::Attach` :

1. Inviare [un oggetto evento IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) a SDM. Per altre informazioni, vedere [Invio di eventi](../../extensibility/debugger/sending-events.md).

2. Chiamare il [metodo GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) [sull'oggetto IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) passato al `IDebugEngine2::Attach` metodo.

     Viene restituito `GUID` un oggetto utilizzato per identificare il programma. L'oggetto deve essere archiviato nell'oggetto che rappresenta il programma locale al de e deve essere restituito quando il `GUID` `IDebugProgram2::GetProgramId` metodo viene chiamato `IDebugProgram2` sull'interfaccia .

    > [!NOTE]
    > Se si implementa `IDebugProgramNodeAttach2` l'interfaccia , l'oggetto del programma `GUID` viene passato al metodo `IDebugProgramNodeAttach2::OnAttach` . Viene `GUID` usato per il programma `GUID` restituito dal metodo `IDebugProgram2::GetProgramId` .

3. Inviare un [oggetto evento IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) per notificare a SDM che l'oggetto locale è stato creato per `IDebugProgram2` rappresentare il programma al de. Per informazioni dettagliate, vedere [Invio di eventi](../../extensibility/debugger/sending-events.md).

    > [!NOTE]
    > Non si tratta dello `IDebugProgram2` stesso oggetto passato al metodo `IDebugEngine2::Attach` . L'oggetto `IDebugProgram2` passato in precedenza viene riconosciuto solo dalla porta ed è un oggetto separato.

## <a name="see-also"></a>Vedi anche
- [Allegato basato sull'avvio](../../extensibility/debugger/launch-based-attachment.md)
- [Invio di eventi](../../extensibility/debugger/sending-events.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)
- [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md)
- [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
