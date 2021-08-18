---
title: Collegamento dopo un avvio | Microsoft Docs
description: Quando viene avviato un programma, la sessione di debug è pronta per collegare il motore di debug al programma. Scegliere un approccio di progettazione per la comunicazione con il motore di debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 3f16df10717ae0d13ac4add90d25ea5be7d3208c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111853"
---
# <a name="attach-after-a-launch"></a>Collegare dopo un avvio
Dopo l'avvio di un programma, la sessione di debug è pronta per collegare il motore di debug (DE) a questo programma.

## <a name="design-decisions"></a>Decisioni di progettazione
 Poiché la comunicazione è più semplice all'interno di uno spazio di indirizzi condiviso, è necessario scegliere tra due approcci di progettazione: impostare la comunicazione tra la sessione di debug e il de. In caso contrario, impostare la comunicazione tra de e il programma. Scegliere tra le opzioni seguenti:

- Se ha più senso configurare la comunicazione tra la sessione di debug e de, la sessione di debug crea il de e chiede al de di connettersi al programma. Questa progettazione lascia la sessione di debug e DE insieme in uno spazio degli indirizzi e l'ambiente di run-time e il programma insieme in un altro.

- Se è più opportuno configurare la comunicazione tra de e il programma, l'ambiente di esecuzione crea la de- Questa progettazione lascia SDM in uno spazio di indirizzi e de, ambiente di run-time e programma insieme in un altro. Questa progettazione è tipica di una de implementata con un interprete per eseguire linguaggi con script.

    > [!NOTE]
    > La modalità di connessione del de al programma dipende dall'implementazione. Anche la comunicazione tra de e il programma dipende dall'implementazione.

## <a name="implementation"></a>Implementazione
 A livello di codice, quando il gestore di debug di sessione (SDM) riceve per la prima volta l'oggetto [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma da avviare, chiama il metodo [Attach,](../../extensibility/debugger/reference/idebugprogram2-attach.md) passando un [oggetto IDebugEventCallback2,](../../extensibility/debugger/reference/idebugeventcallback2.md) che in seguito viene usato per passare gli eventi di debug a SDM. Il `IDebugProgram2::Attach` metodo chiama quindi il metodo [OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Per altre informazioni sul modo in cui SDM riceve `IDebugProgram2` l'interfaccia, vedere [Notifica della porta](../../extensibility/debugger/notifying-the-port.md).

 Se il de deve essere eseguito nello stesso spazio di indirizzi del programma di cui si esegue il debug: poiché il de è in genere parte di un interprete che esegue uno script, il metodo `IDebugProgramNodeAttach2::OnAttach` restituisce `S_FALSE` . Il `S_FALSE` valore restituito indica che è stato completato il processo di connessione.

 Se, tuttavia, il de viene eseguito nello spazio degli indirizzi di SDM: il metodo restituisce `IDebugProgramNodeAttach2::OnAttach` `S_OK` o [l'interfaccia IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) non viene implementata affatto nell'oggetto [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) associato al programma di cui si esegue il debug. In questo caso, il [metodo Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) viene infine chiamato per completare l'operazione di collegamento.

 Nel secondo caso, è necessario chiamare il metodo [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) sull'oggetto passato al metodo , archiviare nell'oggetto programma locale e restituire questo valore quando il metodo viene successivamente chiamato su `IDebugProgram2` `IDebugEngine2::Attach` questo `GUID` `GUID` `IDebugProgram2::GetProgramId` oggetto. Viene `GUID` usato per identificare il programma in modo univoco tra i vari componenti di debug.

 Nel caso del metodo che restituisce , l'oggetto da utilizzare per il programma viene passato a tale metodo ed è il metodo che imposta `IDebugProgramNodeAttach2::OnAttach` `S_FALSE` `GUID` l'oggetto `IDebugProgramNodeAttach2::OnAttach` `GUID` nell'oggetto programma locale.

 Il de è ora collegato al programma e pronto per inviare eventuali eventi di avvio.

## <a name="see-also"></a>Vedi anche
- [Collegamento diretto a un programma](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Notifica alla porta](../../extensibility/debugger/notifying-the-port.md)
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
