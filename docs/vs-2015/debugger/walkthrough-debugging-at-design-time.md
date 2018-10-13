---
title: 'Procedura dettagliata: Debug in fase di progettazione | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4ff1d0e1c155784bd6116be2bc6eb63e6c53d80
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227233"
---
# <a name="walkthrough-debugging-at-design-time"></a>Procedura dettagliata: debug in fase di progettazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile usare Visual Studio **Immediate** finestra per eseguire una funzione o subroutine mentre l'applicazione non è in esecuzione. Se la funzione o subroutine contiene un punto di interruzione, Visual Studio si interromperà l'esecuzione nel punto appropriato. È quindi possibile usare le finestre del debugger per esaminare lo stato del programma. Questa funzionalità è denominata debug in fase di progettazione.  
  
 La procedura seguente illustra come è possibile usare questa funzionalità.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>Per raggiungere punti di interruzione dalla finestra di controllo immediato  
  
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
  
3.  Digitare il comando seguente nel **Immediate** finestra: `?MyFunction<enter>`  
  
4.  Verificare che è stato raggiunto il punto di interruzione e che lo stack di chiamate è accurato.  
  
5.  Nel **Debug** menu, fare clic su **continua**e verificare che sia ancora in modalità progettazione.  
  
6.  Digitare il comando seguente nel **Immediate** finestra: `?MyFunction<enter>`  
  
7.  Digitare il comando seguente nel **Immediate** finestra: `?MySub<enter>`  
  
8.  Verificare che sia stato raggiunto il punto di interruzione ed esamina il valore della variabile statica `i` nella **variabili locali** finestra. Deve avere il valore di 3.  
  
9. Verificare che lo stack di chiamate è accurato.  
  
10. Nel **Debug** menu, fare clic su **continua**e verificare che sia ancora in modalità progettazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debugger Basics](../debugger/debugger-basics.md) (Nozioni di base sul debugger)



