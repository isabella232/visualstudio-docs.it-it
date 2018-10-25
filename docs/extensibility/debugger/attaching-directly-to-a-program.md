---
title: Collegamento diretto a un programma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 361a321a2b06f777adefadae45fc50693983d339
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898369"
---
# <a name="attach-directly-to-a-program"></a>Connettersi direttamente a un programma
Gli utenti che desiderano eseguire il debug di programmi in un processo che è già in esecuzione in genere seguono questa procedura:  
  
1. Nell'IDE, scegliere il **processi di Debug** dalle **Tools** menu.  
  
    Verrà visualizzata la finestra di dialogo **Processi**.  
  
2. Scegli un processo e scegliere il **Attach** pulsante.  
  
    Il **Connetti a processo** verrà visualizzata la finestra di dialogo, elencare tutti i motori di debug (DEs) installati nel computer.  
  
3. Specificare la crittografia DEs da utilizzare per il debug del processo selezionato e quindi fare clic su **OK**.  
  
   Il pacchetto di debug viene avviato una sessione di debug e passa l'elenco di DEs a esso. La sessione di debug, a sua volta passa questo elenco, insieme a una funzione di callback, per il processo selezionato e quindi chiede il processo di enumerare i relativi programmi in esecuzione.  
  
   A livello di codice in risposta alla richiesta dell'utente, il pacchetto di debug crea un'istanza di gestore di sessione di debug (SDM) e passa l'elenco di DEs selezionato a esso. Con l'elenco, il pacchetto di debug passa il modello SDM un' [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interfaccia. Il pacchetto di debug passa l'elenco di DEs per il processo selezionato chiamando [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Chiama quindi il modello SDM [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) sulla porta per enumerare i programmi in esecuzione nel processo.  
  
   Da questo momento, ogni motore di debug è collegato a un programma esattamente come descritto nei [collegamento dopo un avvio](../../extensibility/debugger/attaching-after-a-launch.md), con due eccezioni.  
  
   Per motivi di efficienza, DEs implementate per condividere uno spazio indirizzi con il modello SDM vengono raggruppati in modo che ogni Germania offre un set di programmi collegherà a. In questo caso [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) chiamate [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) e lo passa una matrice dei programmi a cui connettersi.  
  
   La seconda eccezione è che gli eventi di avvio inviati da un DE la connessione a un programma già in esecuzione non includono in genere l'evento punto di ingresso.  
  
## <a name="see-also"></a>Vedere anche  
 [L'invio di eventi di avvio dopo un avvio](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)