---
title: Gestione delle eccezioni (Visual Studio SDK) | Microsoft Docs
description: Informazioni sul processo che si verifica quando vengono generate eccezioni. Questo articolo descrive tutti i passaggi necessari.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f74337964b73683a71b180699da626121a4d3067
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097019"
---
# <a name="exception-handling-visual-studio-sdk"></a>Gestione delle eccezioni (Visual Studio SDK)
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

## <a name="see-also"></a>Vedi anche
- [Chiama eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
