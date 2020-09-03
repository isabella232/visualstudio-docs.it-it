---
title: Connessione diretta a un programma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab49163fc1474b541df3bc1b54d336574761baa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147989"
---
# <a name="attaching-directly-to-a-program"></a>Collegamento diretto a un programma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>Vedere anche  
 [Invio di eventi di avvio dopo un avvio](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
