---
title: Connessione al programma | Microsoft Docs
description: Informazioni su come Visual Studio implementa il debugger che si connette a un programma dopo che il programma è stato registrato con la porta appropriata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 030ee19e7e9e9e52140fb41da78f766978e18d3f
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913763"
---
# <a name="attach-to-the-program"></a>Connetti al programma
Dopo aver registrato i programmi con la porta appropriata, è necessario associare il debugger al programma di cui si desidera eseguire il debug.

## <a name="choose-how-to-attach"></a>Scegliere la modalità di connessione
 Il gestore di debug della sessione (SDM) tenta di connettersi al programma di cui è in corso il debug in tre modi.

1. Per i programmi avviati dal motore di debug tramite il metodo [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) (tipico di linguaggi interpretati, ad esempio), SDM Ottiene l'interfaccia [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) dall'oggetto [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) associato al programma a cui si è connessi. Se SDM è in grado di ottenere l' `IDebugProgramNodeAttach2` interfaccia, SDM chiama il metodo [onconnettit](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Il `IDebugProgramNodeAttach2::OnAttach` metodo restituisce `S_OK` per indicare che non è stato collegato al programma e che è possibile eseguire altri tentativi di connessione al programma.

2. Se SDM può ottenere l'interfaccia [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) dal programma a cui viene collegato, SDM chiama il metodo [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) . Questo approccio è tipico per i programmi avviati in modalità remota dal fornitore della porta.

3. Se il programma non può essere collegato tramite `IDebugProgramNodeAttach2::OnAttach` il `IDebugProgramEx2::Attach` metodo o, l'SDM carica il motore di debug (se non è già stato caricato) chiamando la `CoCreateInstance` funzione e quindi chiama il metodo [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) . Questo approccio è tipico per i programmi avviati localmente da un fornitore di porte.

    È inoltre possibile che un fornitore di porte personalizzato chiami il `IDebugEngine2::Attach` metodo nell'implementazione del metodo del fornitore della porta personalizzata `IDebugProgramEx2::Attach` . In genere, in questo caso, il fornitore della porta personalizzata avvia il motore di debug nel computer remoto.

   L'allegato viene eseguito quando il gestore di debug della sessione (SDM) chiama il metodo di [collegamento](../../extensibility/debugger/reference/idebugengine2-attach.md) .

   Se si esegue il DE nello stesso processo dell'applicazione di cui eseguire il debug, è necessario implementare i seguenti metodi di [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  Dopo la `IDebugEngine2::Attach` chiamata del metodo, attenersi alla seguente procedura nell'implementazione del `IDebugEngine2::Attach` Metodo:

1. Inviare un oggetto evento [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) a SDM. Per ulteriori informazioni, vedere [invio di eventi](../../extensibility/debugger/sending-events.md).

2. Chiamare il metodo [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) sull'oggetto [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) passato al `IDebugEngine2::Attach` metodo.

     Viene restituito un oggetto `GUID` utilizzato per identificare il programma. Il `GUID` deve essere archiviato nell'oggetto che rappresenta il programma locale al de e deve essere restituito quando il `IDebugProgram2::GetProgramId` metodo viene chiamato sull' `IDebugProgram2` interfaccia.

    > [!NOTE]
    > Se si implementa l' `IDebugProgramNodeAttach2` interfaccia, il programma `GUID` viene passato al `IDebugProgramNodeAttach2::OnAttach` metodo. `GUID`Viene utilizzato per il programma `GUID` restituito dal `IDebugProgram2::GetProgramId` metodo.

3. Inviare un oggetto evento [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) per notificare a SDM che l' `IDebugProgram2` oggetto locale è stato creato per rappresentare il programma alla de. Per informazioni dettagliate, vedere [invio di eventi](../../extensibility/debugger/sending-events.md).

    > [!NOTE]
    > Non si tratta dello stesso `IDebugProgram2` oggetto passato al `IDebugEngine2::Attach` metodo. L'oggetto passato in precedenza `IDebugProgram2` viene riconosciuto solo dalla porta ed è un oggetto separato.

## <a name="see-also"></a>Vedi anche
- [Allegato basato su avvio](../../extensibility/debugger/launch-based-attachment.md)
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
