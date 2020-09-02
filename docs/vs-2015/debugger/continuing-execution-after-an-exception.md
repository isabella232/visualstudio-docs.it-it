---
title: Continuazione dell'esecuzione dopo un'eccezione | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702259"
---
# <a name="continuing-execution-after-an-exception"></a>Continuazione dell'esecuzione dopo un'eccezione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando l'esecuzione viene interrotta dal debugger a causa di un'eccezione, viene visualizzata una finestra di dialogo. Per Visual Basic o C#, per impostazione predefinita viene visualizzata la finestra di dialogo informazioni sulle [eccezioni](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb) . Per C++, viene visualizzata la finestra di dialogo **eccezione** precedente. Se si usa Visual Basic o C# ma la **finestra di dialogo** opzioni è stata disabilitata nella finestra di dialogo **Opzioni** , verrà visualizzata la finestra di dialogo **eccezione** .  
  
 Quando viene visualizzata la finestra di dialogo informazioni sulle **eccezioni** o **eccezione** , è possibile tentare di risolvere il problema che ha causato l'eccezione.  
  
## <a name="managed-code"></a>Codice gestito  
 Nel codice gestito, è possibile continuare l'esecuzione nello stesso thread dopo un'eccezione non gestita. In informazioni sulle **eccezioni** viene rimosso lo stack di chiamate fino al punto in cui è stata generata l'eccezione.  
  
## <a name="native-code"></a>Codice nativo  
 In C/C++ nativo, sono disponibili due opzioni:  
  
- È possibile fare clic su **Interrompi** e tentare di risolvere il problema. Quando si è in modalità di disattivazione, è possibile rimuovere lo stack di chiamate facendo clic con il pulsante destro del mouse su un frame nella finestra **stack di chiamate** e selezionando **Rimuovi fino a questo frame** dal menu di scelta rapida. Quando si continua a eseguire il debug, la finestra di dialogo **eccezione** viene visualizzata di nuovo se il problema non è stato risolto. In caso contrario, la finestra di dialogo **eccezione** non verrà visualizzata nuovamente.  
  
- È possibile fare clic su **continua** per continuare l'esecuzione senza tentare di risolvere il problema. Verrà visualizzata nuovamente la finestra di dialogo **eccezione** .  
  
## <a name="mixed-code"></a>Codice misto  
 Se si rileva un'eccezione non gestita durante il debug di codice misto nativo e gestito, i vincoli del sistema operativo impediscono la rimozione dello stack di chiamate. Se si tenta di rimuovere lo stack di chiamate utilizzando il menu di scelta rapida, un messaggio di errore indica che il debugger non può eseguire la rimozione da un'eccezione non gestita durante il debug di codice misto.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md)
