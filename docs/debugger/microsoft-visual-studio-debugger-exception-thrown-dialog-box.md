---
title: Microsoft Visual Studio (generata eccezione) finestra di dialogo del Debugger | Microsoft Docs
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
ms.openlocfilehash: 01ccb091163e3b70c90eaa9b1b6d3b7256a20d4e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954371"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>finestra di dialogo Debugger di Microsoft Visual Studio (generata eccezione)
Si è verificata un'eccezione nel programma. In questa finestra di dialogo è indicato il tipo di eccezione generata. Il codice deve gestire questa eccezione. Per la gestione dell'eccezione sono disponibili le seguenti opzioni:  
  
 **Break**  
 Consente il passaggio dell'esecuzione nel debugger. Il gestore dell'eccezione non viene richiamato prima dell'interruzione, ma solo se si sceglie di continuare dopo l'interruzione.  
  
 **Continue**  
 Consente all'esecuzione di continuare offrendo al gestore dell'eccezione la possibilità di gestirla. Questa opzione non è disponibile per alcuni tipi di eccezioni. **Continua** consentirà all'applicazione di proseguire. In un'applicazione nativa, l'eccezione verrà generata nuovamente. In un'applicazione gestita, il programma verrà interrotto oppure l'eccezione verrà gestita da un'applicazione host.  
  
> [!NOTE]
>  Non è possibile scegliere di continuare dopo un'eccezione non gestita nel codice gestito. Se si sceglie **Continua** dopo un'eccezione non gestita nel codice gestito, il debug verrà interrotto.  
  
 **Ignora**  
 Consente all'esecuzione di continuare senza richiamare il gestore dell'eccezione. Poiché il gestore dell'eccezione non viene richiamato, questa scelta può comportare ulteriori conseguenze, tra cui altre eccezioni o errori. Questa opzione non è disponibile per alcuni tipi di eccezioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle eccezioni con il debugger](../debugger/managing-exceptions-with-the-debugger.md)   
 [Procedure consigliate per le eccezioni](/dotnet/standard/exceptions/best-practices-for-exceptions)   
 [Gestione delle eccezioni](/cpp/windows/exception-handling-cpp-component-extensions)