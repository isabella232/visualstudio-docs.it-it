---
title: Collegamento diretto a un programma | Microsoft Docs
description: Informazioni su Visual Studio implementa il collegamento di un motore di debug a un processo già in esecuzione usando questa procedura nell'IDE Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 189a5e56e189240b014249e7e4b980bf3e8cce034c3647b59711d7a6ae2e84e1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403359"
---
# <a name="attach-directly-to-a-program"></a>Collegarsi direttamente a un programma
Gli utenti che vogliono eseguire il debug di programmi in un processo già in esecuzione seguono in genere questo processo:

1. Nell'IDE scegliere il **comando Debug processi** dal menu Strumenti. 

    Verrà visualizzata la finestra di dialogo **Processi**.

2. Scegliere un processo e fare clic sul **pulsante** Allega.

    Verrà **visualizzata la finestra di** dialogo Collega a processo in cui sono elencati tutti i motori di debug (DE) installati nel computer.

3. Specificare le DE da usare per eseguire il debug del processo selezionato e quindi fare clic su **OK.**

   Il pacchetto di debug avvia una sessione di debug e passa l'elenco di DE. La sessione di debug passa a sua volta questo elenco, insieme a una funzione di callback, al processo selezionato e quindi chiede al processo di enumerare i programmi in esecuzione.

   A livello di codice, in risposta alla richiesta dell'utente, il pacchetto di debug crea un'istanza di Session Debug Manager (SDM) e passa l'elenco delle DE selezionate. Insieme all'elenco, il pacchetto di debug passa a SDM [un'interfaccia IDebugEventCallback2.](../../extensibility/debugger/reference/idebugeventcallback2.md) Il pacchetto di debug passa l'elenco di DE al processo selezionato chiamando [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). SDM chiama quindi [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) sulla porta per enumerare i programmi in esecuzione nel processo.

   Da questo momento in poi, ogni motore di debug viene collegato a un programma esattamente come descritto [in](../../extensibility/debugger/attaching-after-a-launch.md)Collegamento dopo un avvio , con due eccezioni.

   Per migliorare l'efficienza, le unità DE implementate per condividere uno spazio indirizzi con SDM vengono raggruppate in modo che ogni DE abbia un set di programmi a cui verrà collegato. In questo caso, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) chiama [IDebugEngine2::Attach e](../../extensibility/debugger/reference/idebugengine2-attach.md) le passa una matrice di programmi a cui connettersi.

   La seconda eccezione è che gli eventi di avvio inviati da un de collegarsi a un programma già in esecuzione non includono in genere l'evento del punto di ingresso.

## <a name="see-also"></a>Vedi anche
- [Invio di eventi di avvio dopo un avvio](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
