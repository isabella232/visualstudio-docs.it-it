---
title: Finestra di dialogo Microsoft Visual Studio debugger (generata eccezione) | Microsoft Docs
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8376d0cd82e309c2c8db94e38b8c6a2083bd429a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72731202"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>finestra di dialogo Debugger di Microsoft Visual Studio (generata eccezione)
Si è verificata un'eccezione nel programma. In questa finestra di dialogo è indicato il tipo di eccezione generata. Il codice deve gestire questa eccezione. Per la gestione dell'eccezione sono disponibili le seguenti opzioni:

 **Interrompi** Consente di interrompere l'esecuzione nel debugger. Il gestore dell'eccezione non viene richiamato prima dell'interruzione, ma solo se si sceglie di continuare dopo l'interruzione.

 **Continua** Consente di continuare l'esecuzione, concedendo al gestore di eccezioni la possibilità di gestire l'eccezione. Questa opzione non è disponibile per alcuni tipi di eccezioni. **Continua** consentirà all'applicazione di proseguire. In un'applicazione nativa, l'eccezione verrà generata nuovamente. In un'applicazione gestita, il programma verrà interrotto oppure l'eccezione verrà gestita da un'applicazione host.

> [!NOTE]
> Non è possibile scegliere di continuare dopo un'eccezione non gestita nel codice gestito. Se si sceglie **Continua** dopo un'eccezione non gestita nel codice gestito, il debug verrà interrotto.

 **Ignora** Consente di continuare l'esecuzione senza richiamare il gestore di eccezioni. Poiché il gestore dell'eccezione non viene richiamato, questa scelta può comportare ulteriori conseguenze, tra cui altre eccezioni o errori. Questa opzione non è disponibile per alcuni tipi di eccezioni.

## <a name="see-also"></a>Vedere anche
- [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md)
- [Suggerimenti per le eccezioni](/dotnet/standard/exceptions/best-practices-for-exceptions)
- [Gestione delle eccezioni](/cpp/extensions/exception-handling-cpp-component-extensions)