---
title: 'Procedura dettagliata: Debug in fase di progettazione | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5869279a7bafb11368b7fb232e6ca68ca7d98478
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-debugging-at-design-time"></a>Procedura dettagliata: debug in fase di progettazione
È possibile utilizzare Visual Studio **immediato** finestra per eseguire una funzione o una subroutine quando l'applicazione non è in esecuzione. Se la funzione o subroutine contiene un punto di interruzione, Visual Studio interromperà l'esecuzione al momento appropriato. È quindi possibile usare le finestre del debugger per esaminare lo stato del programma. Questa funzionalità è denominata debug in fase di progettazione.  
  
 La procedura seguente viene illustrato come utilizzare questa funzionalità.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>Per raggiungere punti di interruzione dalla finestra controllo immediato  
  
1.  Incollare il codice seguente in un'applicazione console Visual Basic:  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  Impostare un punto di interruzione sulla riga che legge, `s="Add BreakPoint Here"`.  
  
3.  Digitare il comando seguente nel **immediato** finestra:`?MyFunction<enter>`  
  
4.  Verificare che lo stack di chiamate è accurato e che è stato raggiunto il punto di interruzione.  
  
5.  Nel **Debug** menu, fare clic su **continua**e verificare che sia ancora in modalità progettazione.  
  
6.  Digitare il comando seguente nel **immediato** finestra:`?MyFunction<enter>`  
  
7.  Digitare il comando seguente nel **immediato** finestra:`?MySub<enter>`  
  
8.  Verificare che il punto di interruzione e controllare il valore della variabile statica `i` nel **variabili locali** finestra. Deve essere il valore 3.  
  
9. Verificare che lo stack di chiamate sia accurato.  
  
10. Nel **Debug** menu, fare clic su **continua**e verificare che sia ancora in modalità progettazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debugger Basics](../debugger/debugger-basics.md) (Nozioni di base sul debugger)