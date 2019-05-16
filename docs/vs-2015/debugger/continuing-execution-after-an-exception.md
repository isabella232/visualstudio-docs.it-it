---
title: Continuare l'esecuzione dopo un'eccezione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
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
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6ae74c51f0f738bc596fbe5c789011630927707c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65702259"
---
# <a name="continuing-execution-after-an-exception"></a>Continuazione dell'esecuzione dopo un'eccezione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando l'esecuzione viene interrotta dal debugger a causa di un'eccezione, viene visualizzata una finestra di dialogo. Per Visual Basic o c#, verrà visualizzato il [informazioni sulle eccezioni](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb) finestra di dialogo, per impostazione predefinita. Per C++, si noterà il precedente **eccezione** nella finestra di dialogo. Se Usa Visual Basic o c#, ma sono disabilitate le **informazioni sulle eccezioni** nel **opzioni** della finestra di dialogo verrà visualizzato il **eccezione** nella finestra di dialogo.  
  
 Quando la **informazioni sulle eccezioni** oppure **eccezione** verrà visualizzata la finestra di dialogo, è possibile provare a risolvere il problema che ha causato l'eccezione.  
  
## <a name="managed-code"></a>Codice gestito  
 Nel codice gestito, è possibile continuare l'esecuzione nello stesso thread dopo un'eccezione non gestita. Il **informazioni sulle eccezioni** rimuove lo stack di chiamate al punto in cui è stata generata l'eccezione.  
  
## <a name="native-code"></a>Codice nativo  
 In C/C++ nativo, sono disponibili due opzioni:  
  
- È possibile fare clic su **Interrompi** e provare a risolvere il problema. Mentre si è in modalità di interruzione, è possibile rimuovere lo stack di chiamate facendo clic su un frame nel **Stack di chiamate** finestra e selezionando **Rimuovi fino a questo Frame** menu di scelta rapida. Quando si continua a eseguire il debug, il **eccezione** nella finestra di dialogo viene visualizzata nuovamente se non è stato risolto il problema. In caso contrario, il **eccezione** nella finestra di dialogo non verrà più visualizzata.  
  
- È possibile fare clic su **continuazione** per continuare l'esecuzione senza tentare di risolvere il problema. Il **eccezione** viene nuovamente visualizzato nella finestra di dialogo.  
  
## <a name="mixed-code"></a>Codice misto  
 Se si rileva un'eccezione non gestita durante il debug di codice misto nativo e gestito, i vincoli del sistema operativo impediscono la rimozione dello stack di chiamate. Se si tenta di rimuovere lo stack di chiamate utilizzando il menu di scelta rapida, un messaggio di errore indica che il debugger non può eseguire la rimozione da un'eccezione non gestita durante il debug di codice misto.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md)
