---
title: Controllo di esecuzione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0fdaa3154dda0dd96f229eace4b82370dfad59a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029008"
---
# <a name="control-of-execution"></a>Controllo dell'esecuzione
Il motore di debug (DE) in genere uno dei seguenti eventi Invia come l'ultimo evento di avvio:  
  
- L'evento punto di ingresso, se la connessione a un programma appena avviato  
  
- L'evento completo di carico, se la connessione a un programma già in esecuzione  
  
  Entrambi questi eventi sono eventi di arresto, vale a dire che la Germania attende una risposta da parte dell'utente tramite l'IDE. Per altre informazioni, vedere [modalità operative](../../extensibility/debugger/operational-modes.md).  
  
## <a name="stopping-event"></a>L'evento di arresto  
 Quando viene inviato un evento di arresto per la sessione di debug:  
  
1. Il programma e il thread che contengono il puntatore all'istruzione corrente può essere ottenuti dall'interfaccia di eventi.  
  
2. L'IDE determina il file del codice sorgente corrente e la posizione, che viene visualizzato come evidenziato nell'editor.  
  
3. La sessione di debug in genere risponde a questo evento di arresto prima chiamando il programma **continuazione** (metodo).  
  
4. Il programma viene quindi eseguita finché non viene rilevata una condizione di interruzione, ad esempio raggiunge un punto di interruzione. In questo caso, la Germania invia un evento punto di interruzione per la sessione di debug. L'evento punto di interruzione è un evento di arresto e la Germania nuovamente attende una risposta dell'utente.  
  
5. Se si sceglie di eseguire, ignorare o da una funzione, l'IDE si comporta la sessione di debug per chiamare il programma `Step` (metodo). L'IDE passa quindi l'unità del passaggio (istruzione, istruzione o riga) e il tipo di passaggio (se eseguire le istruzioni in, failover o la funzione). Una volta completato il passaggio, la Germania invia un evento di completamento del passaggio per la sessione di debug, che è un evento di arresto.  
  
    -oppure-  
  
    Se si sceglie di continuare l'esecuzione dal puntatore dell'istruzione corrente, l'IDE si comporta la sessione di debug per chiamare il programma **Execute** (metodo). Il programma riprende l'esecuzione finché non viene rilevata la condizione di interruzione successiva.  
  
    -oppure-  
  
    Se la sessione di debug ignorare un evento di arresto particolare, la sessione di debug viene chiamato il programma **continuazione** (metodo). Se il programma è stato l'esecuzione di istruzioni in, failover o da una funzione quando rilevata la condizione di interruzione, quindi continua il passaggio.  
  
   A livello di codice quando la Germania rileva una condizione di interruzione, invia eventi quali stopping [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oppure [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) per la gestione di debug di sessione (SDM) per mezzo di un' [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interfaccia. Il DE viene superato il [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) e [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfacce che rappresentano il programma e il thread che contiene il puntatore all'istruzione corrente. Le chiamate SDM [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) per ottenere i frame superiore dello stack e le chiamate [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) per ottenere il contesto del documento associato all'istruzione corrente puntatore. In questo contesto di documento è in genere un file di origine code nome, riga e colonna numero. L'IDE Usa questi per evidenziare il codice sorgente che contiene il puntatore all'istruzione corrente.  
  
   Il modello SDM risponde a questo evento di arresto prima in genere chiamando [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Quindi il programma viene eseguito finché non viene rilevata una condizione di interruzione, ad esempio raggiunge un punto di interruzione, nel quale caso il DE invia un' [IDebugBreakpointEvent2 interfaccia](../../extensibility/debugger/reference/idebugbreakpointevent2.md) per il modello SDM. L'evento punto di interruzione è un evento di arresto e la Germania nuovamente attende una risposta dell'utente.  
  
   Se si sceglie di eseguire, ignorare o da una funzione, l'IDE si comporta il modello SDM per chiamare [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md). L'IDE passa quindi il [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (istruzione, istruzione o riga) e il [STEPKIND](../../extensibility/debugger/reference/stepkind.md), vale a dire, se eseguire le istruzioni in, failover o la funzione. Una volta completato il passaggio, la Germania invia un' [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfaccia per il modello SDM, che è un evento di arresto.  
  
   Se si sceglie di continuare l'esecuzione dal puntatore dell'istruzione corrente, l'IDE chiede il modello SDM per chiamare [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). Il programma riprende l'esecuzione finché non viene rilevata la condizione di interruzione successiva.  
  
   Se il pacchetto di debug per ignorare un evento di arresto particolare, il pacchetto di debug chiama il modello SDM, che chiama [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Se il programma è stato l'esecuzione di istruzioni in, failover o da una funzione quando rilevata la condizione di interruzione, il passaggio continua. Ciò implica che il programma mantiene uno stato di avanzamento nell'esecuzione, in modo che possa continuare.  
  
   Le chiamate verso il modello SDM `Step`, **Execute**, e **Continue** sono asincrona, il che significa che il modello SDM prevede la chiamata per restituire rapidamente. Se la Germania invia il modello SDM un evento di arresto sullo stesso thread prima `Step`, **Execute**, o **Continue** termina, il modello SDM si blocca.  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il debug di attività](../../extensibility/debugger/debugging-tasks.md)