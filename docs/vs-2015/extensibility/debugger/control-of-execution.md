---
title: Controllo dell'esecuzione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c885c0c983e6fafd69d55b3d68f8ed6e8ff2628c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387265"
---
# <a name="control-of-execution"></a>Controllo dell'esecuzione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il motore di debug (DE) Invia in genere uno degli eventi seguenti come ultimo evento di avvio:  
  
- Evento del punto di ingresso, se collegato a un programma appena avviato  
  
- Evento di caricamento completo, se collegato a un programma già in esecuzione  
  
  Entrambi questi eventi arrestano gli eventi, vale a dire che il DE attende una risposta dall'utente tramite l'IDE. Per ulteriori informazioni, vedere [modalità operative](../../extensibility/debugger/operational-modes.md).  
  
## <a name="stopping-event"></a>Evento di arresto  
 Quando un evento di arresto viene inviato alla sessione di debug:  
  
1. Il programma e il thread che contengono il puntatore all'istruzione corrente possono essere ottenuti dall'interfaccia eventi.  
  
2. L'IDE determina il file e la posizione del codice sorgente corrente, che visualizza evidenziato nell'editor.  
  
3. La sessione di debug risponde in genere a questo primo evento di arresto chiamando il metodo **continue** del programma.  
  
4. Il programma viene quindi eseguito fino a quando non viene rilevata una condizione di arresto, ad esempio il raggiungimento di un punto di interruzione, nel qual caso il DE Invia un evento del punto di interruzione alla sessione di debug. L'evento del punto di interruzione è un evento di arresto e il valore di nuovo attende la risposta dell'utente.  
  
5. Se l'utente sceglie di eseguire un'istruzione, una o più di una funzione, l'IDE chiede alla sessione di debug di chiamare il metodo del programma `Step` , passando all'unità di misura (istruzione, istruzione o riga) e al tipo di passaggio, ovvero se eseguire un'istruzione, una o più parti della funzione. Al termine del passaggio, il DE Invia un evento Step complete alla sessione di debug, che è un evento di arresto.  
  
    -oppure-  
  
    Se l'utente sceglie di continuare l'esecuzione dal puntatore all'istruzione corrente, l'IDE chiede alla sessione di debug di chiamare il metodo **Execute** del programma. Il programma riprende l'esecuzione fino a quando non viene rilevata la condizione di arresto successiva.  
  
    -oppure-  
  
    Se la sessione di debug deve ignorare un determinato evento di arresto, la sessione di debug chiama il metodo **continue** del programma. Se il programma esegue l'istruzione, l'esecuzione o la disattivazione di una funzione quando si verifica la condizione di arresto, continua il passaggio.  
  
   A livello di codice, quando il DE rileva una condizione di arresto, invia tali eventi di arresto come [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) a gestione debug sessione (SDM) per mezzo di un'interfaccia [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) . Il DE passa le interfacce [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) e [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) che rappresentano il programma e il thread contenente il puntatore all'istruzione corrente. SDM chiama [IDebugThread2:: EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) per ottenere il primo stack frame e chiama [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) per ottenere il contesto del documento associato al puntatore all'istruzione corrente. Questo contesto del documento è in genere un nome di file di codice sorgente, una riga e un numero di colonna. L'IDE li usa per evidenziare il codice sorgente che contiene il puntatore all'istruzione corrente.  
  
   SDM risponde in genere a questo primo evento di arresto chiamando [IDebugProgram2:: continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Il programma viene quindi eseguito fino a quando non rileva una condizione di arresto, ad esempio il raggiungimento di un punto di interruzione, nel qual caso il DE Invia un' [interfaccia IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) al SDM. L'evento del punto di interruzione è un evento di arresto e il valore di nuovo attende la risposta dell'utente.  
  
   Se l'utente sceglie di eseguire un'istruzione, una o più di una funzione, l'IDE richiede a SDM di chiamare [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md), passando il [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (istruzione, istruzione o riga) e [STEPKIND](../../extensibility/debugger/reference/stepkind.md), vale a dire se eseguire un'istruzione, una o più parti della funzione. Al termine del passaggio, il DE Invia un'interfaccia [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) al SDM, che è un evento di arresto.  
  
   Se l'utente sceglie di continuare l'esecuzione dal puntatore all'istruzione corrente, l'IDE chiede a SDM di chiamare [IDebugProgram2:: Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). Il programma riprende l'esecuzione fino a quando non viene rilevata la condizione di arresto successiva.  
  
   Se il pacchetto di debug deve ignorare un determinato evento di arresto, il pacchetto di debug chiama SDM, che chiama [IDebugProgram2:: continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Se il programma esegue l'istruzione, l'esecuzione o la disattivazione di una funzione quando si verifica la condizione di arresto, continua il passaggio. Questo implica che il programma gestisce uno stato di avanzamento, in modo da poter continuare.  
  
   Le chiamate effettuate da SDM a `Step` , **Execute**e **continue** sono asincrone, il che significa che SDM prevede che la chiamata restituisca rapidamente. Se l'oggetto DE invia l'evento SDM a Stop sullo stesso thread prima `Step` che **venga**restituito, Execute o **continue** , l'SDM smette di rispondere.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
