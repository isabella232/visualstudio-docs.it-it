---
title: Istruzioni Stop in Visual Basic | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fcb4e3018dad53ef869748a4394363dba78f71c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517341"
---
# <a name="stop-statements-in-visual-basic"></a>Istruzioni Stop in Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [le istruzioni Stop in Visual Basic](https://docs.microsoft.com/visualstudio/debugger/stop-statements-in-visual-basic).  
  
L'istruzione Stop di Visual Basic fornisce un'alternativa a livello di codice all'impostazione di un punto di interruzione. Quando il debugger rileva un'istruzione Stop, viene interrotta l'esecuzione del programma, ossia viene attivata la modalità di interruzione. I programmatori C# possono ottenere lo stesso risultato tramite una chiamata a System.Diagnostics.Debugger.Break.  
  
 Per impostare o rimuovere un'istruzione Stop, è necessario modificare il codice sorgente. Le istruzioni Stop non possono essere impostate né rimosse mediante i comandi del debugger, come invece avviene per i punti di interruzione.  
  
 A differenza di un'istruzione End, l'istruzione Stop non reimposta le variabili né consente di tornare alla modalità di progettazione. Per continuare l'esecuzione dell'applicazione, scegliere Continua dal menu Debug.  
  
 Quando un'applicazione Visual Basic viene eseguita all'esterno del debugger, un'istruzione Stop avvierà il debugger se è attivato il debug JIT. Se invece il debug JIT non è attivato, l'istruzione Stop si comporterà come un'istruzione End e terminerà l'esecuzione. Poiché non si verificherà alcun evento QueryUnload o Unload, sarà necessario rimuovere tutte le istruzioni Stop dalla versione di rilascio dell'applicazione Visual Basic. Per altre informazioni, vedere [debug JIT](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Per evitare di dover rimuovere le istruzioni Stop, è possibile utilizzare la compilazione condizionale:  
  
```  
#If DEBUG Then  
   Stop  
#Else  
   ' Don't stop  
#End If  
```  
  
 È inoltre possibile utilizzare un'istruzione Assert anziché l'istruzione Stop. Un'istruzione Debug.Assert interrompe l'esecuzione solo quando non viene soddisfatta una condizione specificata e viene rimossa automaticamente quando si compila una versione di rilascio. Per altre informazioni, vedere [asserzioni nel codice gestito](../debugger/assertions-in-managed-code.md). Se si desidera un'istruzione Assert che interrompa sempre l'esecuzione nella versione di debug, è possibile specificare:  
  
```  
Debug.Assert(false)  
```  
  
 Un'altra alternativa consiste nell'utilizzo del metodo Debug.Fail:  
  
```  
Debug.Fail("a clever output string goes here")  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Debug di codice gestito](../debugger/debugging-managed-code.md)


