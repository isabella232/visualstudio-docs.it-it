---
title: Associazione dopo un lancio Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a4ce0a7465891035b43bbb8f6f22f0c064d104c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739279"
---
# <a name="attach-after-a-launch"></a>Attacca dopo un lancio
Dopo l'avvio di un programma, la sessione di debug è pronta per collegare il motore di debug (DE) a tale programma.

## <a name="design-decisions"></a>Decisioni progettuali
 Poiché la comunicazione è più semplice all'interno di uno spazio di indirizzi condiviso, è necessario scegliere tra due approcci di progettazione: impostare la comunicazione tra la sessione di debug e il DE. In alternativa, impostare la comunicazione tra il DE e il programma. Scegliere tra le seguenti opzioni:

- Se ha più senso impostare la comunicazione tra la sessione di debug e IL DE, la sessione di debug co-crea il DE e chiede il DE per connettersi al programma. Questa progettazione lascia la sessione di debug e DE insieme in uno spazio degli indirizzi e l'ambiente di runtime e programma insieme in un altro.

- Se ha più senso impostare la comunicazione tra il DE e il programma, l'ambiente di runtime crea il DE. Questa progettazione lascia il modello SDM in uno spazio degli indirizzi e DE, ambiente di runtime e programma insieme in un altro. Questa progettazione è tipica di un DE implementato con un interprete per l'esecuzione di linguaggi con script.

    > [!NOTE]
    > La modalità di connessione del DE al programma dipende dall'implementazione. Anche la comunicazione tra il DE e il programma dipende dall'implementazione.

## <a name="implementation"></a>Implementazione
 A livello di codice, quando il gestore di sessione di debug (SDM) riceve prima il [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) oggetto che rappresenta il programma da avviare, chiama il [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) metodo, passando un [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) oggetto, che viene successivamente utilizzato per passare gli eventi di debug al modello SDM. Il `IDebugProgram2::Attach` metodo chiama quindi il [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metodo. Per ulteriori informazioni su come il `IDebugProgram2` sistema SDM riceve l'interfaccia, vedere [Notifica della porta](../../extensibility/debugger/notifying-the-port.md).

 Se il DE deve essere eseguito nello stesso spazio degli indirizzi del programma di cui si sta eseguendo `IDebugProgramNodeAttach2::OnAttach` il `S_FALSE`debug, poiché il DE è in genere parte di un interprete che esegue uno script, il metodo restituisce . Il `S_FALSE` ritorno indica che è stato completato il processo di collegamento.

 Se, tuttavia, il DE viene eseguito nello `IDebugProgramNodeAttach2::OnAttach` spazio `S_OK`degli indirizzi del modello SDM: il metodo restituisce o il [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaccia non è implementata affatto sul [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) oggetto associato al programma che si sta eseguendo il debug. In questo caso, il [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) metodo viene infine chiamato per completare l'operazione di collegamento.

 In quest'ultimo caso, è necessario chiamare `IDebugProgram2` il [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metodo sull'oggetto che è stato passato `GUID` al `IDebugProgram2::GetProgramId` `IDebugEngine2::Attach` metodo, archiviare l'oggetto `GUID` nell'oggetto programma locale e restituire questo quando il metodo viene successivamente chiamato su questo oggetto. Il `GUID` viene utilizzato per identificare il programma in modo univoco tra i vari componenti di debug.

 Nel caso del `IDebugProgramNodeAttach2::OnAttach` metodo `S_FALSE`restituito `GUID` , l'oggetto da utilizzare per il programma `IDebugProgramNodeAttach2::OnAttach` viene passato `GUID` a tale metodo ed è il metodo che imposta l'oggetto programma locale.

 Il DE è ora collegato al programma e pronto per inviare eventuali eventi di avvio.

## <a name="see-also"></a>Vedere anche
- [Collegamento diretto a un programma](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Notifica della porta](../../extensibility/debugger/notifying-the-port.md)
- [Attività di debugDebugging tasks](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
