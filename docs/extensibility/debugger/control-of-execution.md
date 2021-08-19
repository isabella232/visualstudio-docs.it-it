---
title: Controllo dell'esecuzione | Microsoft Docs
description: Informazioni sugli eventi di arresto, il che significa che de attende una risposta dall'utente tramite l'IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: c93c767513592ff7e0fc2c971f7b1eeeca4873c9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133276"
---
# <a name="control-of-execution"></a>Controllo dell'esecuzione
Il motore di debug (DE) in genere invia uno degli eventi seguenti come ultimo evento di avvio:

- Evento del punto di ingresso, se collegato a un programma appena avviato

- Evento di caricamento completato, se collegato a un programma già in esecuzione

  Entrambi questi eventi sono eventi di arresto, ovvero il DE attende una risposta dall'utente tramite l'IDE. Per altre informazioni, vedere [Modalità operative](../../extensibility/debugger/operational-modes.md).

## <a name="stopping-event"></a>Evento di arresto
 Quando un evento di arresto viene inviato alla sessione di debug:

1. Il programma e il thread che contengono il puntatore all'istruzione corrente possono essere ottenuti dall'interfaccia degli eventi.

2. L'IDE determina il file e la posizione correnti del codice sorgente, visualizzati come evidenziato nell'editor.

3. La sessione di debug in genere risponde a questo primo evento di arresto chiamando il metodo **Continue del** programma.

4. Il programma viene quindi eseguito fino a quando non rileva una condizione di arresto, ad esempio quando si tocca un punto di interruzione. In tal caso, il DE invia un evento punto di interruzione alla sessione di debug. L'evento del punto di interruzione è un evento di arresto e il de è di nuovo in attesa di una risposta dell'utente.

5. Se l'utente sceglie di eseguire un'istruzione o uscire da una funzione, l'IDE richiede alla sessione di debug di chiamare il metodo del `Step` programma. L'IDE passa quindi l'unità di passaggio (istruzione, istruzione o riga) e il tipo di passaggio (se eseguire un'istruzione, eseguire o uscire dalla funzione). Al termine del passaggio, il DE invia un evento di completamento del passaggio alla sessione di debug, che è un evento di arresto.

    -oppure-

    Se l'utente sceglie di continuare l'esecuzione dal puntatore all'istruzione corrente, l'IDE richiede alla sessione di debug di chiamare il **metodo Execute del** programma. Il programma riprende l'esecuzione finché non rileva la condizione di arresto successiva.

    -oppure-

    Se la sessione di debug deve ignorare un particolare evento di arresto, la sessione di debug chiama il metodo **Continue del** programma. Se il programma esegue un'istruzione o esce da una funzione quando ha rilevato la condizione di arresto, continua il passaggio.

   A livello di codice, quando il DE rileva una condizione di arresto, invia eventi di arresto come [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) al gestore di debug sessione (SDM) tramite [un'interfaccia IDebugEventCallback2.](../../extensibility/debugger/reference/idebugeventcallback2.md) Il de passa le [interfacce IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) e [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) che rappresentano il programma e il thread contenente il puntatore all'istruzione corrente. SDM chiama [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) per ottenere il primo stack frame e chiama [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) per ottenere il contesto del documento associato al puntatore all'istruzione corrente. Questo contesto del documento è in genere un nome file di codice sorgente, una riga e un numero di colonna. L'IDE usa questi elementi per evidenziare il codice sorgente che contiene il puntatore all'istruzione corrente.

   SDM risponde in genere a questo primo evento di arresto chiamando [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Il programma viene quindi eseguito fino a quando non rileva una condizione di arresto, ad esempio quando si tocca un punto di interruzione, nel qual caso il de invia [un'interfaccia IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) a SDM. L'evento del punto di interruzione è un evento di arresto e il de è di nuovo in attesa di una risposta dell'utente.

   Se l'utente sceglie di eseguire un'istruzione, eseguire o uscire da una funzione, l'IDE richiede a SDM di chiamare [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md). L'IDE passa quindi [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (istruzione, istruzione o riga) e [STEPKIND](../../extensibility/debugger/reference/stepkind.md), ovvero se eseguire un'istruzione, un'istruzione o un'uscita dalla funzione. Al termine del passaggio, il DE invia [un'interfaccia IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) a SDM, che è un evento di arresto.

   Se l'utente sceglie di continuare l'esecuzione dal puntatore all'istruzione corrente, l'IDE chiede a SDM di chiamare [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). Il programma riprende l'esecuzione finché non rileva la condizione di arresto successiva.

   Se il pacchetto di debug deve ignorare un particolare evento di arresto, il pacchetto di debug chiama SDM, che chiama [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Se il programma esegue un'istruzione o esce da una funzione quando ha rilevato la condizione di arresto, continua il passaggio. Ciò implica che il programma mantiene uno stato di esecuzione delle istruzioni, in modo da sapere come continuare.

   Le chiamate effettuate da SDM a , Execute e Continue sono asincrone, il che significa che SDM prevede che la chiamata `Step` restituirà rapidamente.   Se il de invia a SDM un evento di arresto sullo stesso thread prima che venga restituito `Step` , **Execute** o **Continue,** SDM smette di rispondere.

## <a name="see-also"></a>Vedi anche
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
