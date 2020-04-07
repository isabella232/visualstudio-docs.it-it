---
title: Controllo dell'esecuzione Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2d338c5470611a5eea0c6279404c4eaddebb2d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739071"
---
# <a name="control-of-execution"></a>Controllo dell'esecuzione
Il motore di debug (DE) invia in genere uno dei seguenti eventi come ultimo evento di avvio:

- L'evento del punto di ingresso, se collegato a un programma appena lanciato

- L'evento load complete, se collegato a un programma che è già in esecuzione

  Entrambi questi eventi sono gli eventi di arresto, vale a dire che il DE attende una risposta dall'utente tramite l'IDE. Per ulteriori informazioni, consultate [Modalità operative.](../../extensibility/debugger/operational-modes.md)

## <a name="stopping-event"></a>Evento di arresto
 Quando un evento di arresto viene inviato alla sessione di debug:When a stopping event is sent to the debug session:

1. Il programma e il thread che contengono il puntatore all'istruzione corrente possono essere ottenuti dall'interfaccia eventi.

2. L'IDE determina il file di codice sorgente corrente e la posizione, che viene visualizzato come evidenziato nell'editor.

3. La sessione di debug in genere risponde a questo primo evento di arresto chiamando il metodo **Continue** del programma.

4. Il programma viene quindi eseguito fino a quando non viene rilevata una condizione di arresto, ad esempio il punto di interruzione. In questo caso, il DE invia un evento punto di interruzione alla sessione di debug. L'evento del punto di interruzione è un evento di arresto e il DE attende nuovamente una risposta dell'utente.

5. Se l'utente sceglie di eseguire un'istruzione in, over o out di una funzione, `Step` l'IDE richiede la sessione di debug per chiamare il metodo del programma. L'IDE passa quindi l'unità di passaggio (istruzione, istruzione o riga) e il tipo di passaggio (se eseguire un'istruzione, eseguire o uscire dalla funzione). Al termine del passaggio, il DE invia un evento di completamento del passaggio alla sessione di debug, che è un evento di arresto.

    -oppure-

    Se l'utente sceglie di continuare l'esecuzione dal puntatore all'istruzione corrente, l'IDE richiede la sessione di debug per chiamare il programma **Execute** metodo. Il programma riprende l'esecuzione fino a quando non incontra la condizione di arresto successiva.

    -oppure-

    Se la sessione di debug deve ignorare un particolare evento di arresto, la sessione di debug chiama il metodo **Continue** del programma. Se il programma stava eseguendo un'istruzione in, oltre o da una funzione quando ha rilevato la condizione di arresto, quindi continua il passaggio.

   A livello di codice, quando il DE rileva una condizione di arresto, invia tali eventi di arresto come [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) per il gestore di sessione di debug (SDM) tramite un [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interfaccia. Il DE passa il [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) e [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfacce che rappresentano il programma e il thread contenente il puntatore all'istruzione corrente. SDM chiama [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) per ottenere lo stack frame superiore e chiama [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) per ottenere il contesto del documento associato al puntatore all'istruzione corrente. Questo contesto del documento è in genere un nome di file di codice sorgente, un numero di riga e di colonna. L'IDE utilizza questi per evidenziare il codice sorgente che contiene il puntatore all'istruzione corrente.

   Il modello SDM in genere risponde a questo primo evento di arresto chiamando [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Il programma viene quindi eseguito fino a quando non viene rilevata una condizione di arresto, ad esempio il punto di interruzione, nel qual caso il DE invia un [IDebugBreakpointEvent2 interfaccia](../../extensibility/debugger/reference/idebugbreakpointevent2.md) per il modello SDM. L'evento del punto di interruzione è un evento di arresto e il DE attende nuovamente una risposta dell'utente.

   Se l'utente sceglie di eseguire un'istruzione in una funzione, oltre o da uscite da una funzione, l'IDE richiede al file SDM di chiamare [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md). L'IDE passa quindi [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (istruzione, istruzione o riga) e [STEPKIND](../../extensibility/debugger/reference/stepkind.md), ovvero se eseguire un'istruzione, eseguire o uscire dalla funzione. Al termine del passaggio, il DE invia un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfaccia per il modello SDM, che è un evento di arresto.

   Se l'utente sceglie di continuare l'esecuzione dal puntatore all'istruzione corrente, l'IDE chiede al modello SDM di chiamare [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). Il programma riprende l'esecuzione fino a quando non incontra la condizione di arresto successiva.

   Se il pacchetto di debug deve ignorare un particolare evento di arresto, il pacchetto di debug chiama il modello SDM, che chiama [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Se il programma stava eseguendo un'istruzione in, oltre o da una funzione quando ha rilevato la condizione di arresto, continua il passaggio. Ciò implica che il programma mantiene uno stato di stepping, in modo che sappia come continuare.

   Le chiamate effettuate dal `Step`modello SDM a , **Execute**e **Continue** sono asincrone, il che significa che il modello SDM prevede che la chiamata venga restituita rapidamente. Se il DE invia il modello SDM `Step`un evento di arresto sullo stesso thread prima, **Execute**o **Continue** restituisce , il modello SDM si blocca.

## <a name="see-also"></a>Vedere anche
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
