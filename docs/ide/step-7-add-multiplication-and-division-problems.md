---
title: 'Passaggio 7: Aggiungere problemi di moltiplicazione e divisione'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3c3c89def201f0045d561b180bd3af521ba4c2de
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2018
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Passaggio 7: Aggiungere problemi di moltiplicazione e divisione
Nella settima parte di questa esercitazione si aggiungeranno i problemi di moltiplicazione e divisione, ma prima di procedere vedere come effettuare questa modifica. Considerare il passaggio iniziale, che comporta l'archiviazione dei valori.  

## <a name="to-add-multiplication-and-division-problems"></a>Per aggiungere problemi di moltiplicazione e divisione  

1.  Aggiungere altre quattro variabili di tipo Integer al modulo.  

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]  

2.  Come in precedenza, modificare il metodo `StartTheQuiz()` per inserire numeri casuali per i problemi di moltiplicazione e divisione.  

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]  

3.  Modificare il metodo `CheckTheAnswer()` in modo che controlli anche i problemi di moltiplicazione e divisione.  

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]  

     Non è possibile immettere con facilità il segno di moltiplicazione (×) e di divisione (÷) tramite la tastiera. Visual C# e Visual Basic, quindi, accettano l'asterisco (*) per la moltiplicazione e la barra (/) per la divisione.  
  
4.  Modificare l'ultima parte del gestore dell'evento <xref:System.Windows.Forms.Timer.Tick> del timer in modo che inserisca la risposta corretta allo scadere del tempo.  
  
     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]  

5.  Salvare ed eseguire il programma.  

     Gli esecutori del quiz devono risolvere quattro problemi per completare il quiz, come illustrato di seguito.  

     ![Quiz matematico con quattro problemi](../ide/media/express_finishedquiz.png "Express_FinishedQuiz")  
**Quiz matematico** con quattro problemi  
  
## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
-   Per andare al passaggio successivo dell'esercitazione, vedere [Passaggio 8: Personalizzare il quiz](../ide/step-8-customize-the-quiz.md).  
  
-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 6: Aggiungere un problema di sottrazione](../ide/step-6-add-a-subtraction-problem.md).
