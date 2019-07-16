---
title: (Visual Studio SDK) di gestione delle eccezioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 38e646f032a12de48bbfb55b089462c7f8a4dd26
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152798"
---
# <a name="exception-handling-visual-studio-sdk"></a>Gestione delle eccezioni (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Di seguito viene descritto il processo che si verifica quando vengono generate eccezioni.  
  
## <a name="exception-handling-process"></a>Processo di gestione delle eccezioni  
  
1. Quando un'eccezione viene generata prima, ma prima che viene gestita dal gestore dell'eccezione nel programma sottoposto a debug, il motore di debug (DE) invia un [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) per la gestione del debug di sessione (SDM) come un evento di arresto. Il `IDebugExceptionEvent2` viene inviato se solo le impostazioni per l'eccezione (specificato nella finestra di dialogo delle eccezioni nel pacchetto di debug) specificano che l'utente desidera arrestare le notifiche di eccezioni first-chance.  
  
2. Le chiamate SDM [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) per ottenere la proprietà dell'eccezione.  
  
3. Le chiamate di pacchetto di debug [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) per determinare quali opzioni per presentare all'utente.  
  
4. Il pacchetto di debug viene chiesto all'utente come gestire l'eccezione, aprire una finestra di dialogo eccezioni first-chance.  
  
5. Se l'utente sceglie di continuare, chiama il modello SDM [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).  
  
    - Se il metodo restituisce S_OK, chiama il metodo [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).  
  
         -oppure-  
  
         Se il metodo restituisce S_FALSE, il programma in fase di debug ha una seconda possibilità per gestire l'eccezione.  
  
6. Se il programma sottoposto a debug non dispone di alcun gestore per un'eccezione second-chance, la Germania invia un' `IDebugExceptionEvent2` per il modello SDM come **EVENT_SYNC_STOP**.  
  
7. Il pacchetto di debug viene chiesto all'utente come gestire l'eccezione, aprire una finestra di dialogo eccezioni first-chance.  
  
8. Le chiamate di pacchetto di debug [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) per determinare quali opzioni per presentare all'utente.  
  
9. Il pacchetto di debug viene chiesto all'utente come gestire l'eccezione, aprire una finestra di dialogo di eccezione second-chance.  
  
10. Se il metodo restituisce S_OK, chiama il metodo `IDebugExceptionEvent2::PassToDebuggee`.  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
