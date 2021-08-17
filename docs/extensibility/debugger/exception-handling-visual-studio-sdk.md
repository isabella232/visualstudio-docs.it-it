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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 3763c38fa99f28ac2af52ef821aac2c623720b4c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096622"
---
# <a name="exception-handling-visual-studio-sdk"></a>Gestione delle eccezioni (Visual Studio SDK)
Di seguito viene descritto il processo che si verifica quando vengono generate eccezioni.

## <a name="exception-handling-process"></a>Processo di gestione delle eccezioni

1. Quando un'eccezione viene generata per la prima volta, ma prima che venga gestita dal gestore eccezioni nel programma di cui viene effettuato il debug, il motore di debug invia [un IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) al gestore di debug sessione (SDM) come evento di arresto. L'oggetto viene inviato se solo le impostazioni per l'eccezione (specificate nella finestra di dialogo Eccezioni nel pacchetto di debug) specificano che l'utente vuole arrestare le notifiche delle eccezioni `IDebugExceptionEvent2` first-chance.

2. SDM chiama [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) per ottenere la proprietà dell'eccezione.

3. Il pacchetto di debug chiama [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) per determinare le opzioni da presentare all'utente.

4. Il pacchetto di debug chiede all'utente come gestire l'eccezione aprendo una finestra di dialogo di eccezione first-chance.

5. Se l'utente sceglie di continuare, SDM chiama [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).

    - Se il metodo restituisce S_OK, chiama [IDebugExceptionEvent2::P assToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).

         -oppure-

         Se il metodo restituisce S_FALSE, al programma in fase di debug viene data una seconda possibilità di gestire l'eccezione.

6. Se il programma in fase di debug non dispone di un gestore per un'eccezione second-chance, il de invia un oggetto a `IDebugExceptionEvent2` SDM **come EVENT_SYNC_STOP**.

7. Il pacchetto di debug chiede all'utente come gestire l'eccezione aprendo una finestra di dialogo di eccezione first-chance.

8. Il pacchetto di debug chiama [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) per determinare le opzioni da presentare all'utente.

9. Il pacchetto di debug chiede all'utente come gestire l'eccezione aprendo una finestra di dialogo dell'eccezione second-chance.

10. Se il metodo restituisce S_OK, chiama `IDebugExceptionEvent2::PassToDebuggee` .

## <a name="see-also"></a>Vedi anche
- [Chiamare eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
