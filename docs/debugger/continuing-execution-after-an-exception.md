---
title: Continuare l'esecuzione dopo un'eccezione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48e0cf526d6fadcb1b91206d6e1958d89d3bdfe5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949963"
---
# <a name="continuing-execution-after-an-exception"></a>Continuazione dell'esecuzione dopo un'eccezione
Quando il debugger interrompe l'esecuzione a causa di un'eccezione, verrà visualizzato il **Helper eccezioni**, per impostazione predefinita. Se è stata disabilitata la **Helper eccezioni** nel **opzioni** della finestra di dialogo verrà visualizzato il **informazioni sulle eccezioni** (C# o Visual Basic) o il  **Eccezione** nella finestra di dialogo (C++).  
  
 Quando la **Helper eccezioni** viene visualizzata, è possibile provare a risolvere il problema che ha causato l'eccezione.
  
## <a name="managed-and-native-code"></a>Codice gestito e nativo  
 Nel codice gestito e nativo, è possibile continuare l'esecuzione nello stesso thread dopo un'eccezione non gestita. Il **Helper eccezioni** rimuove lo stack di chiamate al punto in cui è stata generata l'eccezione.
  
## <a name="mixed-code"></a>Codice misto  
 Se si rileva un'eccezione non gestita durante il debug di codice misto nativo e gestito, i vincoli del sistema operativo impediscono la rimozione dello stack di chiamate. Se si tenta di rimuovere lo stack di chiamate utilizzando il menu di scelta rapida, un messaggio di errore indica che il debugger non può eseguire la rimozione da un'eccezione non gestita durante il debug di codice misto.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md)