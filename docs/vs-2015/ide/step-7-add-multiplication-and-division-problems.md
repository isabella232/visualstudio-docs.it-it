---
title: 'Passaggio 7: Aggiungere problemi di moltiplicazione e divisione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a558372c69aaf5aeb76685cae3eae4f30a6b9737
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795268"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Passaggio 7: aggiungere problemi di moltiplicazione e divisione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella settima parte di questa esercitazione si aggiungeranno i problemi di moltiplicazione e divisione, ma prima di procedere vedere come effettuare questa modifica. Considerare il passaggio iniziale, che comporta l'archiviazione dei valori.  
  
### <a name="to-add-multiplication-and-division-problems"></a>Per aggiungere problemi di moltiplicazione e divisione  
  
1.  Aggiungere altre quattro variabili di tipo Integer al modulo.  
  
     [!code-csharp[VbExpressTutorial3Step7#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial3Step7#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#15)]  
  
2.  Come in precedenza, modificare il metodo `StartTheQuiz()` per inserire numeri casuali per i problemi di moltiplicazione e divisione.  
  
     [!code-csharp[VbExpressTutorial3Step7#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial3Step7#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#16)]  
  
3.  Modificare il metodo `CheckTheAnswer()` in modo che controlli anche i problemi di moltiplicazione e divisione.  
  
     [!code-csharp[VbExpressTutorial3Step7#17](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#17)]
     [!code-vb[VbExpressTutorial3Step7#17](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#17)]  
  
     Non è possibile immettere con facilità il segno di moltiplicazione (×) e di divisione (÷) tramite la tastiera. Visual C# e Visual Basic, quindi, accettano l'asterisco (*) per la moltiplicazione e la barra (/) per la divisione.  
  
4.  Modificare l'ultima parte del gestore dell'evento Tick del timer in modo che inserisca la risposta corretta alla scadenza del tempo.  
  
     [!code-csharp[VbExpressTutorial3Step7#23](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#23)]
     [!code-vb[VbExpressTutorial3Step7#23](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#23)]  
  
5.  Salvare ed eseguire il programma.  
  
     Gli esecutori del quiz devono risolvere quattro problemi per completare il quiz, come illustrato di seguito.  
  
     ![Quiz matematico con quattro problemi](../ide/media/express-finishedquiz.png "Express_FinishedQuiz")  
Quiz matematico con quattro problemi  
  
### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
-   Per andare al passaggio successivo dell'esercitazione, vedere [Passaggio 8: personalizzare il quiz](../ide/step-8-customize-the-quiz.md).  
  
-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 6: aggiungere un problema di sottrazione](../ide/step-6-add-a-subtraction-problem.md).
