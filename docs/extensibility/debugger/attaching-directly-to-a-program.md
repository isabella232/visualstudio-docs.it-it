---
title: Connessione diretta a un programma | Microsoft Docs
description: Informazioni su come Visual Studio implementa l'associazione di un motore di debug a un processo già in esecuzione tramite questa procedura nell'IDE di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2f261d6492943ab0b0da878097685ae2773ddff4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055297"
---
# <a name="attach-directly-to-a-program"></a>Connettersi direttamente a un programma
Gli utenti che desiderano eseguire il debug di programmi in un processo già in esecuzione in genere seguono questo processo:

1. Nell'IDE scegliere il comando **debug processi** dal menu **strumenti** .

    Verrà visualizzata la finestra di dialogo **Processi**.

2. Scegliere un processo e fare clic sul pulsante **Connetti** .

    Viene visualizzata la finestra **di dialogo Connetti a processo** , che elenca tutti i motori di debug (des) installati nel computer.

3. Specificare il DEs da usare per eseguire il debug del processo selezionato e quindi fare clic su **OK**.

   Il pacchetto di debug avvia una sessione di debug e passa l'elenco di DEs a tale sessione. La sessione di debug a sua volta passa questo elenco, insieme a una funzione di callback, al processo selezionato, quindi chiede al processo di enumerare i programmi in esecuzione.

   A livello di codice, in risposta alla richiesta dell'utente, il pacchetto di debug crea un'istanza di gestione debug sessione (SDM) e passa l'elenco di DEs selezionati. Insieme all'elenco, il pacchetto di debug passa l'interfaccia SDM a [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) . Il pacchetto di debug passa l'elenco di DEs al processo selezionato chiamando [IDebugProcess2:: Connetti](../../extensibility/debugger/reference/idebugprocess2-attach.md). Il SDM chiama quindi [IDebugProcess2:: EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) sulla porta per enumerare i programmi in esecuzione nel processo.

   Da questo punto in poi, ogni motore di debug viene collegato a un programma esattamente come descritto in [connessione dopo un avvio](../../extensibility/debugger/attaching-after-a-launch.md), con due eccezioni.

   Per migliorare l'efficienza, le DEs implementate per condividere uno spazio degli indirizzi con SDM sono raggruppate in modo che ogni DE disponga di un set di programmi a cui si connetterà. In questo caso, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) chiama [IDebugEngine2:: collega](../../extensibility/debugger/reference/idebugengine2-attach.md) e passa a una matrice di programmi a cui connettersi.

   La seconda eccezione è costituita dal fatto che gli eventi di avvio inviati da una connessione a un programma già in esecuzione non includono in genere l'evento del punto di ingresso.

## <a name="see-also"></a>Vedi anche
- [Invio di eventi di avvio dopo un avvio](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
