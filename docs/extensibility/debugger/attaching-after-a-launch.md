---
title: Collegamento dopo un avvio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1b0a34505cf32e0e3fd4dc18bfeab4588856dba4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63409957"
---
# <a name="attach-after-a-launch"></a>Collegare dopo un avvio
Dopo aver avviato un programma, la sessione di debug è pronta per collegare il motore di debug (DE) a tale programma.

## <a name="design-decisions"></a>Decisioni di progettazione
 Poiché la comunicazione è più semplice all'interno di uno spazio di indirizzi condivisa, è necessario scegliere tra due approcci di progettazione: impostare la comunicazione tra la sessione di debug e il DE. In alternativa, impostare la comunicazione tra il DE e il programma. Scegliere tra gli elementi seguenti:

- Se è più opportuno configurare la comunicazione tra la sessione di debug e il DE, la sessione di debug CO-crea il DE e chiede di DE collegare al programma. Questa progettazione rende la sessione di debug e DE insieme uno spazio indirizzi e l'ambiente di runtime e il programma insieme in un altro.

- Se è più opportuno configurare la comunicazione tra il DE e il programma, l'ambiente di runtime CO-crea il DE. Questa progettazione lascia il modello SDM in uno spazio indirizzi e il DE ambiente run-time e programma insieme in un altro. Questa progettazione è tipica di un CRI implementata con un interprete per eseguire i linguaggi basati su script.

    > [!NOTE]
    > Modalità la Germania viene associato al programma è dipendente dall'implementazione. Comunicazione tra il DE e il programma viene anche dipende dall'implementazione.

## <a name="implementation"></a>Implementazione
 A livello di codice quando la sessione debug manager (SDM) prima di tutto riceve la [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) oggetto che rappresenta il programma da avviare, chiama il [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) passandogli un [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) oggetto, che è successivo usato per passare gli eventi di debug indietro per il modello SDM. Il `IDebugProgram2::Attach` chiama quindi il [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) (metodo). Per altre informazioni sul modo in cui il modello SDM riceve la `IDebugProgram2` dell'interfaccia, vedere [notifica della porta](../../extensibility/debugger/notifying-the-port.md).

 Se la Germania deve essere eseguito nello stesso spazio di indirizzi del programma si esegue il debug: poiché la Germania è in genere parte di un interprete che esegue uno script, il `IDebugProgramNodeAttach2::OnAttach` restituzione del metodo `S_FALSE`. Il `S_FALSE` restituito indica che completato il processo di collegamento.

 Se, tuttavia, la Germania viene eseguito nello spazio degli indirizzi del messaggio SDM: il `IDebugProgramNodeAttach2::OnAttach` restituzione del metodo `S_OK`, o il [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaccia non è implementata affatto d'il [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) oggetto associato al programma si esegue il debug. In questo caso, il [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) viene chiamato alla fine per completare l'operazione di collegamento.

 Nel secondo caso, è necessario chiamare il [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metodo sul `IDebugProgram2` che è stato passato al `IDebugEngine2::Attach` (metodo), store il `GUID` nel programma locale dell'oggetto e restituire this `GUID` quando il `IDebugProgram2::GetProgramId` viene successivamente chiamato su questo oggetto. Il `GUID` viene usato per identificare in modo univoco il programma per i vari componenti di debug.

 Nel caso del `IDebugProgramNodeAttach2::OnAttach` metodo che restituisce `S_FALSE`, il `GUID` da usare per il programma viene passato al metodo ed è il `IDebugProgramNodeAttach2::OnAttach` metodo che imposta il `GUID` sull'oggetto programma locale.

 La Germania è ora allegato al programma e pronto per inviare gli eventi di avvio.

## <a name="see-also"></a>Vedere anche
- [Collegamento diretto a un programma](../../extensibility/debugger/attaching-directly-to-a-program.md)
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