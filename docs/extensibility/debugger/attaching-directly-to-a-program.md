---
title: Associazione diretta a un programma Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9a5699ee81b8c8ae36bcf492e93467615a9e89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739258"
---
# <a name="attach-directly-to-a-program"></a>Collegare direttamente a un programma
Gli utenti che desiderano eseguire il debug di programmi in un processo che è già in esecuzione in genere seguono questo processo:Users who want to debug programs in a process that is already running typically follow this process:

1. Nell'IDE, scegliere il **Debug processi** comando dal **strumenti** menu.

    Verrà visualizzata la finestra di dialogo **Processi**.

2. Scegliere un processo e fare clic sul pulsante **Allega.**

    Viene visualizzata la finestra di dialogo **Connetti a processo** in cui sono elencati tutti i motori di debug (DE) installati nel computer.

3. Specificare i DEs da utilizzare per eseguire il debug del processo selezionato e quindi fare clic su **OK**.

   Il pacchetto di debug avvia una sessione di debug e vi passa l'elenco di DE. La sessione di debug passa a sua volta questo elenco, insieme a una funzione di callback, al processo selezionato e quindi chiede al processo di enumerare i programmi in esecuzione.

   A livello di codice, in risposta alla richiesta dell'utente, il pacchetto di debug crea un'istanza del gestore di sessione di debug (SDM) e vi passa l'elenco dei DEe selezionati. Insieme all'elenco, il pacchetto di debug passa il modello SDM un [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interfaccia. Il pacchetto di debug passa l'elenco di DEs al processo selezionato chiamando [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Il modello SDM chiama quindi [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) sulla porta per enumerare i programmi in esecuzione nel processo.

   Da questo punto in poi, ogni motore di debug è collegato a un programma esattamente come descritto in [Collegamento dopo un avvio,](../../extensibility/debugger/attaching-after-a-launch.md)con due eccezioni.

   Per migliorare l'efficienza, le DE implementate per condividere uno spazio di indirizzi con il sistema SDM vengono raggruppate in modo che ogni DE disponga di un set di programmi a cui verrà associato. In questo caso, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) chiama [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) e passa una matrice di programmi a cui connettersi.

   La seconda eccezione è che gli eventi di avvio inviati da un DE collegato a un programma che è già in esecuzione in genere non includono l'evento del punto di ingresso.

## <a name="see-also"></a>Vedere anche
- [Invio di eventi di avvio dopo un avvio](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [Attività di debugDebugging tasks](../../extensibility/debugger/debugging-tasks.md)
