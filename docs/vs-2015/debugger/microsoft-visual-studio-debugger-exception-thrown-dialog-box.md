---
title: Microsoft Visual Studio (generata eccezione) finestra di dialogo del Debugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eccfc06cd48513e7a72eb23bbde11188f2e50dbd
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696875"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>finestra di dialogo Debugger di Microsoft Visual Studio (generata eccezione)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si è verificata un'eccezione nel programma. In questa finestra di dialogo è indicato il tipo di eccezione generata. Il codice deve gestire questa eccezione. Per la gestione dell'eccezione sono disponibili le seguenti opzioni:  
  
 **Break**  
 Consente il passaggio dell'esecuzione nel debugger. Il gestore dell'eccezione non viene richiamato prima dell'interruzione, ma solo se si sceglie di continuare dopo l'interruzione.  
  
 **Continue**  
 Consente all'esecuzione di continuare offrendo al gestore dell'eccezione la possibilità di gestirla. Questa opzione non è disponibile per alcuni tipi di eccezioni. **Continua** consentirà all'applicazione di proseguire. In un'applicazione nativa, l'eccezione verrà generata nuovamente. In un'applicazione gestita, il programma verrà interrotto oppure l'eccezione verrà gestita da un'applicazione host.  
  
> [!NOTE]
> Non è possibile scegliere di continuare dopo un'eccezione non gestita nel codice gestito. Se si sceglie **Continua** dopo un'eccezione non gestita nel codice gestito, il debug verrà interrotto.  
  
 **Ignora**  
 Consente all'esecuzione di continuare senza richiamare il gestore dell'eccezione. Poiché il gestore dell'eccezione non viene richiamato, questa scelta può comportare ulteriori conseguenze, tra cui altre eccezioni o errori. Questa opzione non è disponibile per alcuni tipi di eccezioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle eccezioni con il debugger](../debugger/managing-exceptions-with-the-debugger.md)   
 [Procedure consigliate per le eccezioni](https://msdn.microsoft.com/library/f06da765-235b-427a-bfb6-47cd219af539)   
 [Gestione delle eccezioni](https://msdn.microsoft.com/library/ccb11fe8-6938-41ac-b477-a183e85865b9)
