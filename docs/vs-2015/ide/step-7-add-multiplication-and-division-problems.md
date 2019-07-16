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
ms.openlocfilehash: 47623d7a65de85b50ad1910425052288a261e49d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178584"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Passaggio 7: Aggiungere problemi di moltiplicazione e divisione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella settima parte di questa esercitazione si aggiungeranno i problemi di moltiplicazione e divisione, ma prima di procedere vedere come effettuare questa modifica. Considerare il passaggio iniziale, che comporta l'archiviazione dei valori.  
  
### <a name="to-add-multiplication-and-division-problems"></a>Per aggiungere problemi di moltiplicazione e divisione  
  
1. Aggiungere altre quattro variabili di tipo Integer al modulo.  
  
     [!code-csharp[VbExpressTutorial3Step7#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial3Step7#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#15)]  
  
2. Come in precedenza, modificare il metodo `StartTheQuiz()` per inserire numeri casuali per i problemi di moltiplicazione e divisione.  
  
     [!code-csharp[VbExpressTutorial3Step7#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial3Step7#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#16)]  
  
3. Modificare il metodo `CheckTheAnswer()` in modo che controlli anche i problemi di moltiplicazione e divisione.  
  
     [!code-csharp[VbExpressTutorial3Step7#17](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#17)]
     [!code-vb[VbExpressTutorial3Step7#17](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#17)]  
  
     Non è possibile immettere con facilità il segno di moltiplicazione (×) e di divisione (÷) tramite la tastiera. Visual C# e Visual Basic, quindi, accettano l'asterisco (*) per la moltiplicazione e la barra (/) per la divisione.  
  
4. Modificare l'ultima parte del gestore dell'evento Tick del timer in modo che inserisca la risposta corretta alla scadenza del tempo.  
  
     [!code-csharp[VbExpressTutorial3Step7#23](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#23)]
     [!code-vb[VbExpressTutorial3Step7#23](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#23)]  
  
5. Salvare ed eseguire il programma.  
  
     Gli esecutori del quiz devono risolvere quattro problemi per completare il quiz, come illustrato di seguito.  
  
     ![Quiz matematico con quattro problemi](../ide/media/express-finishedquiz.png "Express_FinishedQuiz")  
Quiz matematico con quattro problemi  
  
### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
- Per procedere al passaggio successivo dell'esercitazione, vedere [Passaggio 8: Personalizzare il Quiz](../ide/step-8-customize-the-quiz.md).  
  
- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 6: Aggiungere un problema di sottrazione](../ide/step-6-add-a-subtraction-problem.md).
