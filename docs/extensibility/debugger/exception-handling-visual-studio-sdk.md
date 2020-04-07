---
title: Gestione delle eccezioni (Visual Studio SDK) Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34b83c7181a7ba405e642d9911e2c53df3f4401d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738770"
---
# <a name="exception-handling-visual-studio-sdk"></a>Gestione delle eccezioni (Visual Studio SDK)Exception handling (Visual Studio SDK)
Di seguito viene descritto il processo che si verifica quando vengono generate eccezioni.

## <a name="exception-handling-process"></a>Processo di gestione delle eccezioni

1. Quando un'eccezione viene generata per la prima volta, ma prima che venga gestita dal gestore di eccezioni nel programma sottoposto a debug, il motore di debug (DE) invia un [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) al gestore di sessione di debug (SDM) come evento di arresto. L'oggetto `IDebugExceptionEvent2` viene inviato se solo le impostazioni per l'eccezione (specificate nella finestra di dialogo Eccezioni nel pacchetto di debug) specificano che l'utente desidera interrompere le notifiche di eccezione first-chance.

2. SDM chiama [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) per ottenere la proprietà dell'eccezione.

3. Il pacchetto di debug chiama [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) per determinare le opzioni da presentare all'utente.

4. Il pacchetto di debug chiede all'utente come gestire l'eccezione aprendo una finestra di dialogo di eccezione first-chance.

5. Se l'utente sceglie di continuare, SDM chiama [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).

    - Se il metodo restituisce S_OK, chiama [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).

         -oppure-

         Se il metodo restituisce S_FALSE, al programma in fase di debug viene data una seconda possibilità di gestire l'eccezione.

6. Se il programma in fase di debug non dispone di alcun `IDebugExceptionEvent2` gestore per un'eccezione second-chance, il DE invia un al file SDM come **EVENT_SYNC_STOP**.

7. Il pacchetto di debug chiede all'utente come gestire l'eccezione aprendo una finestra di dialogo di eccezione first-chance.

8. Il pacchetto di debug chiama [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) per determinare le opzioni da presentare all'utente.

9. Il pacchetto di debug chiede all'utente come gestire l'eccezione aprendo una finestra di dialogo di eccezione second-chance.

10. Se il metodo restituisce S_OK, chiama `IDebugExceptionEvent2::PassToDebuggee`.

## <a name="see-also"></a>Vedere anche
- [Chiamare eventi del debuggerCall debugger events](../../extensibility/debugger/calling-debugger-events.md)
