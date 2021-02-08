---
title: Connessione dopo un avvio | Microsoft Docs
description: Quando viene avviato un programma, la sessione di debug è pronta per l'associazione del motore di debug al programma. Scegliere un approccio di progettazione per la comunicazione con il motore di debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 22ce6497b820e1dcd37315f9d74cb97de4cc34e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837736"
---
# <a name="attach-after-a-launch"></a>Connetti dopo un avvio
Dopo l'avvio di un programma, la sessione di debug è pronta per allineare il motore di debug (DE) al programma detto.

## <a name="design-decisions"></a>Decisioni di progettazione
 Poiché la comunicazione è più semplice in uno spazio di indirizzi condiviso, è necessario scegliere tra due approcci di progettazione: impostare la comunicazione tra la sessione di debug e il DE. In alternativa, impostare la comunicazione tra il DE e il programma. Scegliere una delle opzioni seguenti:

- Se è più opportuno configurare la comunicazione tra la sessione di debug e il DE, la sessione di debug crea il DE e chiede alla DE di connettersi al programma. Questa struttura lascia la sessione di debug e il raggruppamento in uno spazio di indirizzi e l'ambiente di runtime e il programma insieme in un altro.

- Se è più opportuno configurare la comunicazione tra il DE e il programma, l'ambiente di runtime co-crea il DE. Questa progettazione lascia l'SDM in uno spazio di indirizzi e l'ambiente di run-time e il programma insieme in un altro. Questa progettazione è tipica di una DE implementata con un interprete per l'esecuzione di linguaggi con script.

    > [!NOTE]
    > Il modo in cui il DE si connette al programma dipende dall'implementazione. Anche la comunicazione tra il DE e il programma è dipendente dall'implementazione.

## <a name="implementation"></a>Implementazione
 A livello di codice, quando la gestione del debug della sessione (SDM) riceve prima di tutto l'oggetto [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma da avviare, chiama il metodo di [connessione](../../extensibility/debugger/reference/idebugprogram2-attach.md) , passandogli un oggetto [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) , che viene usato in un secondo momento per passare di nuovo gli eventi di debug a SDM. Il `IDebugProgram2::Attach` metodo chiama quindi il metodo [onconnettit](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Per ulteriori informazioni sul modo in cui SDM riceve l' `IDebugProgram2` interfaccia, vedere [notifica della porta](../../extensibility/debugger/notifying-the-port.md).

 Se il DE deve essere eseguito nello stesso spazio di indirizzi del programma di cui si sta eseguendo il debug: poiché il DE è in genere parte di un interprete che esegue uno script, il `IDebugProgramNodeAttach2::OnAttach` metodo restituisce `S_FALSE` . Il `S_FALSE` risultato indica che è stato completato il processo di connessione.

 Se, tuttavia, il DE viene eseguito nello spazio degli indirizzi di SDM: il `IDebugProgramNodeAttach2::OnAttach` metodo restituisce `S_OK` oppure l'interfaccia [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) non viene implementata affatto nell'oggetto [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) associato al programma di cui si sta eseguendo il debug. In questo caso, viene chiamato il metodo di [connessione](../../extensibility/debugger/reference/idebugengine2-attach.md) per completare l'operazione di connessione.

 Nel secondo caso, è necessario chiamare il metodo [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) sull' `IDebugProgram2` oggetto passato al `IDebugEngine2::Attach` metodo, archiviare `GUID` nell'oggetto programma locale e restituire questo oggetto `GUID` quando il `IDebugProgram2::GetProgramId` metodo viene chiamato successivamente su questo oggetto. `GUID`Viene utilizzato per identificare il programma in modo univoco tra i vari componenti di debug.

 Nel caso della `IDebugProgramNodeAttach2::OnAttach` restituzione del metodo `S_FALSE` , l' `GUID` oggetto da usare per il programma viene passato a tale metodo ed è il `IDebugProgramNodeAttach2::OnAttach` metodo che imposta l' `GUID` oggetto sull'oggetto programma locale.

 Il DE è ora collegato al programma e pronto per l'invio di eventi di avvio.

## <a name="see-also"></a>Vedi anche
- [Connessione diretta a un programma](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Notifica della porta](../../extensibility/debugger/notifying-the-port.md)
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
