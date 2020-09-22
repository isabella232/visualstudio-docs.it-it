---
title: Connessione dopo un avvio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 693cf6d746f51862415f2f30e46d48a998047f14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840292"
---
# <a name="attaching-after-a-launch"></a>Collegamento dopo un avvio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dopo l'avvio di un programma, la sessione di debug è pronta per allineare il motore di debug (DE) a detto programma.  
  
## <a name="design-decisions"></a>Decisioni sulla progettazione  
 Poiché la comunicazione è più semplice in uno spazio di indirizzi condiviso, è necessario decidere se è più sensato facilitare la comunicazione tra la sessione di debug e il DE oppure tra il DE e il programma. Scegliere una delle opzioni seguenti:  
  
- Se è più sensato facilitare la comunicazione tra la sessione di debug e il DE, la sessione di debug crea il DE e chiede alla DE di connettersi al programma. In questo modo, la sessione di debug e il raggruppamento vengono riuniti in uno spazio di indirizzi e l'ambiente di runtime e il programma insieme in un altro.  
  
- Se è più sensato facilitare la comunicazione tra il DE e il programma, l'ambiente di run-time crea il DE. In questo modo, l'SDM viene lasciato in uno spazio di indirizzi e l'ambiente di run-time e il programma viene insieme in un altro. Questo è tipico di un DE implementato con un interprete per l'esecuzione di linguaggi con script.  
  
    > [!NOTE]
    > Il modo in cui il DE si connette al programma dipende dall'implementazione. Anche la comunicazione tra il DE e il programma è dipendente dall'implementazione.  
  
## <a name="implementation"></a>Implementazione  
 A livello di codice, quando la gestione del debug della sessione (SDM) riceve prima di tutto l'oggetto [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma da avviare, chiama il metodo di [connessione](../../extensibility/debugger/reference/idebugprogram2-attach.md) , passandogli un oggetto [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) , che viene usato in un secondo momento per passare di nuovo gli eventi di debug a SDM. Il `IDebugProgram2::Attach` metodo chiama quindi il metodo [onconnettit](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Per ulteriori informazioni sul modo in cui SDM riceve l' `IDebugProgram2` interfaccia, vedere [notifica della porta](../../extensibility/debugger/notifying-the-port.md).  
  
 Se il DE deve essere eseguito nello stesso spazio di indirizzi del programma di cui è in corso il debug, in genere perché il DE fa parte di un interprete che esegue uno script, il `IDebugProgramNodeAttach2::OnAttach` metodo restituisce `S_FALSE` , a indicare che è stato completato il processo di connessione.  
  
 Se, invece, il DE viene eseguito nello spazio degli indirizzi di SDM, il `IDebugProgramNodeAttach2::OnAttach` metodo restituisce `S_OK` o l'interfaccia [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) non viene implementata affatto nell'oggetto [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) associato al programma di cui è in corso il debug. In questo caso, viene chiamato il metodo di [connessione](../../extensibility/debugger/reference/idebugengine2-attach.md) per completare l'operazione di connessione.  
  
 Nel secondo caso, è necessario chiamare il metodo [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) sull' `IDebugProgram2` oggetto passato al `IDebugEngine2::Attach` metodo, archiviare `GUID` nell'oggetto programma locale e restituire questo oggetto `GUID` quando il `IDebugProgram2::GetProgramId` metodo viene chiamato successivamente su questo oggetto. `GUID`Viene utilizzato per identificare il programma in modo univoco tra i vari componenti di debug.  
  
 Si noti che, nel caso del `IDebugProgramNodeAttach2::OnAttach` metodo che restituisce `S_FALSE` , il `GUID` da usare per il programma viene passato a tale metodo ed è il `IDebugProgramNodeAttach2::OnAttach` metodo che imposta l' `GUID` oggetto nell'oggetto del programma locale.  
  
 Il DE è ora collegato al programma e pronto per l'invio di eventi di avvio.  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione diretta a un programma](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Notifica della porta](../../extensibility/debugger/notifying-the-port.md)   
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Collegare](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Onconnetti](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
