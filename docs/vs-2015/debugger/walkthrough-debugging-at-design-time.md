---
title: 'Procedura dettagliata: debug in fase di progettazione | Microsoft Docs'
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
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54466cc3561c194199bbad2b35cd00433da2b0f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149421"
---
# <a name="walkthrough-debugging-at-design-time"></a>Procedura dettagliata: debug in fase di progettazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile usare la finestra **controllo immediato** di Visual Studio per eseguire una funzione o una subroutine mentre l'applicazione non è in esecuzione. Se la funzione o subroutine contiene un punto di interruzione, Visual Studio interrompe l'esecuzione nel punto appropriato. È quindi possibile usare le finestre del debugger per esaminare lo stato del programma. Questa funzionalità è denominata debug in fase di progettazione.  
  
 Nella procedura seguente viene illustrato come è possibile utilizzare questa funzionalità.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>Per raggiungere i punti di interruzione dalla finestra di controllo immediato  
  
1. Incollare il codice seguente in un'applicazione console Visual Basic:  
  
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
  
2. Impostare un punto di interruzione sulla riga che legge, `s="Add BreakPoint Here"` .  
  
3. Nella finestra di **controllo immediato** Digitare quanto segue: `?MyFunction<enter>`  
  
4. Verificare che il punto di interruzione sia stato raggiunto e che lo stack di chiamate sia accurato.  
  
5. Scegliere **continua**dal menu **debug** e verificare che l'utente sia ancora in modalità progettazione.  
  
6. Nella finestra di **controllo immediato** Digitare quanto segue: `?MyFunction<enter>`  
  
7. Nella finestra di **controllo immediato** Digitare quanto segue: `?MySub<enter>`  
  
8. Verificare di aver raggiunto il punto di interruzione ed esaminare il valore della variabile statica `i` nella finestra variabili **locali** . Il valore deve essere 3.  
  
9. Verificare che lo stack di chiamate sia accurato.  
  
10. Scegliere **continua**dal menu **debug** e verificare che l'utente sia ancora in modalità progettazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)
