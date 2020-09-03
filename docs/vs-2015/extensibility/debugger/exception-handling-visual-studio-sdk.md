---
title: Gestione delle eccezioni (Visual Studio SDK) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152798"
---
# <a name="exception-handling-visual-studio-sdk"></a>Gestione delle eccezioni (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Di seguito viene descritto il processo che si verifica quando vengono generate eccezioni.  
  
## <a name="exception-handling-process"></a>Processo di gestione delle eccezioni  
  
1. Quando viene generata prima un'eccezione, ma prima che venga gestita dal gestore di eccezioni nel programma di cui è in corso il debug, il motore di debug (DE) Invia un [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) al gestore di debug della sessione (SDM) come evento di arresto. `IDebugExceptionEvent2`Viene inviato se solo le impostazioni per l'eccezione (specificato nella finestra di dialogo eccezioni nel pacchetto di debug) specificano che l'utente desidera arrestare le notifiche di eccezioni first-chance.  
  
2. SDM chiama [IDebugExceptionEvent2:: GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) per ottenere la proprietà dell'eccezione.  
  
3. Il pacchetto di debug chiama [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) per determinare le opzioni da presentare all'utente.  
  
4. Il pacchetto di debug chiede all'utente come gestire l'eccezione aprendo una finestra di dialogo di eccezione first-chance.  
  
5. Se l'utente sceglie di continuare, SDM chiama [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).  
  
    - Se il metodo restituisce S_OK, chiama [IDebugExceptionEvent2::P asstodebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).  
  
         -oppure-  
  
         Se il metodo restituisce S_FALSE, il programma di cui è in corso il debug riceve una seconda possibilità per gestire l'eccezione.  
  
6. Se il programma di cui è in corso il debug non dispone di un gestore per un'eccezione di seconda probabilità, il DE Invia un oggetto `IDebugExceptionEvent2` a SDM come **EVENT_SYNC_STOP**.  
  
7. Il pacchetto di debug chiede all'utente come gestire l'eccezione aprendo una finestra di dialogo di eccezione first-chance.  
  
8. Il pacchetto di debug chiama [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) per determinare le opzioni da presentare all'utente.  
  
9. Il pacchetto di debug chiede all'utente come gestire l'eccezione aprendo una finestra di dialogo di eccezione della seconda possibilità.  
  
10. Se il metodo restituisce S_OK, chiama `IDebugExceptionEvent2::PassToDebuggee` .  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
