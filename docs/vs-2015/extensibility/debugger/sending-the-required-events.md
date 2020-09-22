---
title: Invio degli eventi richiesti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 457e2daf3e52c23ba9733d09d3aeb94750b5fab9
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2020
ms.locfileid: "90840152"
---
# <a name="sending-the-required-events"></a>Invio degli eventi richiesti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usare questa procedura per inviare gli eventi richiesti.  
  
## <a name="process-for-sending-required-events"></a>Processo per l'invio di eventi richiesti  
 Gli eventi seguenti sono obbligatori, in questo ordine, quando si crea un motore di debug (DE) e lo si collega a un programma:  
  
1. Inviare un oggetto evento [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) al gestore di debug della sessione (SDM) quando il de viene inizializzato per il debug di uno o più programmi in un processo.  
  
2. Quando il programma di cui eseguire il debug è associato a, inviare un oggetto evento [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) al SDM. Questo evento può essere un evento di arresto, a seconda della progettazione del motore.  
  
3. Se il programma è associato a quando viene avviato il processo, inviare un oggetto evento [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) a SDM per notificare l'IDE del nuovo thread. Questo evento può essere un evento di arresto, a seconda della progettazione del motore.  
  
4. Invia un oggetto evento [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) a SDM quando il programma di cui è in corso il debug viene completato il caricamento o quando il programma viene collegato al programma. Questo evento deve essere un evento di arresto.  
  
5. Se l'applicazione di cui eseguire il debug viene avviata, inviare un oggetto evento [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) a SDM quando sta per essere eseguita la prima istruzione di codice nell'architettura di run-time. Questo evento è sempre un evento di arresto. Quando si esegue un'istruzione nella sessione di debug, l'IDE si interrompe in questo evento.  
  
> [!NOTE]
> Molti linguaggi usano inizializzatori globali o funzioni esterne e precompilate (dalla libreria CRT o _Main) all'inizio del codice. Se la lingua del programma di cui si esegue il debug contiene uno di questi tipi di elementi prima del punto di ingresso iniziale, il codice viene eseguito e l'evento del punto di ingresso viene inviato quando viene raggiunto il punto di ingresso dell'utente, ad esempio **Main** o `WinMain` .  
  
## <a name="see-also"></a>Vedere anche  
 [Abilitazione di un programma da sottoporre a debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
