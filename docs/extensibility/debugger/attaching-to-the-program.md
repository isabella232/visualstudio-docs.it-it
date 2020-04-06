---
title: Associazione al Programma Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f39b489a57ab93ba5f2d116738c591bd53ff95f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739248"
---
# <a name="attach-to-the-program"></a>Collegamento al programma
Dopo aver registrato i programmi con la porta appropriata, è necessario connettere il debugger al programma di cui si desidera eseguire il debug.

## <a name="choose-how-to-attach"></a>Scegli come allegare
 Esistono tre modi in cui il gestore di sessione di debug (SDM) tenta di connettersi al programma in fase di debug.

1. Per i programmi avviati dal motore di debug tramite il [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) metodo (tipico dei linguaggi interpretati, ad esempio), il modello SDM ottiene il [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaccia dal [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) oggetto associato al programma a cui viene collegato. Se il file SDM può ottenere l'interfaccia, `IDebugProgramNodeAttach2` il file SDM chiama quindi il [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metodo. Il `IDebugProgramNodeAttach2::OnAttach` metodo `S_OK` restituisce per indicare che non è stato collegato al programma e che è possibile effettuare altri tentativi di collegamento al programma.

2. Se il file SDM può ottenere il [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) interfaccia dal programma a cui viene collegato, il sDM chiama il [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) metodo. Questo approccio è tipico per i programmi che sono stati avviati in remoto dal fornitore della porta.

3. Se il programma non può `IDebugProgramNodeAttach2::OnAttach` `IDebugProgramEx2::Attach` essere collegato tramite i metodi o , il processo `CoCreateInstance` SDM carica il motore di debug (se non è già caricato) chiamando la funzione e quindi chiama il [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) metodo. Questo approccio è tipico per i programmi avviati localmente da un fornitore di porte.

    È anche possibile che un fornitore `IDebugEngine2::Attach` di porta personalizzato chiami il `IDebugProgramEx2::Attach` metodo nell'implementazione del metodo da parte del fornitore della porta personalizzata. In genere, in questo caso, il fornitore della porta personalizzata avvia il motore di debug nel computer remoto.

   L'allegato viene ottenuto quando il gestore di sessione di debug (SDM) chiama il [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) metodo.

   Se si esegue il DE nello stesso processo dell'applicazione da sottoporre a debug, è necessario implementare i seguenti metodi di [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  Dopo `IDebugEngine2::Attach` aver chiamato il metodo, seguire questi `IDebugEngine2::Attach` passaggi nell'implementazione del metodo:

1. Inviare un oggetto evento [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) al modello SDM. Per ulteriori informazioni, vedere [Invio di eventi](../../extensibility/debugger/sending-events.md).

2. Chiamare il [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metodo il [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) oggetto `IDebugEngine2::Attach` che è stato passato al metodo.

     Restituisce `GUID` un oggetto utilizzato per identificare il programma. L'oggetto `GUID` deve essere archiviato nell'oggetto che rappresenta il programma locale `IDebugProgram2::GetProgramId` per il `IDebugProgram2` DE e deve essere restituito quando il metodo viene chiamato sull'interfaccia.

    > [!NOTE]
    > Se si `IDebugProgramNodeAttach2` implementa l'interfaccia, `GUID` il programma `IDebugProgramNodeAttach2::OnAttach` viene passato al metodo. Viene `GUID` utilizzato per il `GUID` programma restituito `IDebugProgram2::GetProgramId` dal metodo .

3. Inviare un oggetto evento [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) per notificare al modello SDM che l'oggetto locale `IDebugProgram2` è stato creato per rappresentare il programma al DE. Per informazioni dettagliate, vedere [Invio di eventi](../../extensibility/debugger/sending-events.md).

    > [!NOTE]
    > Questo non è `IDebugProgram2` lo stesso oggetto `IDebugEngine2::Attach` che è stato passato nel metodo. L'oggetto `IDebugProgram2` passato in precedenza viene riconosciuto solo dalla porta ed è un oggetto separato.

## <a name="see-also"></a>Vedere anche
- [Allegato basato sul lancio](../../extensibility/debugger/launch-based-attachment.md)
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
