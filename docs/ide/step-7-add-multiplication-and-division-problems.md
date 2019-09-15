---
title: 'Passaggio 7: Aggiungere problemi di moltiplicazione e divisione'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- csharp
- vb
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 182ab3c06ef0956d6c0d97c4276a44c3f3239875
ms.sourcegitcommit: 0e482cfc15f809b564c3de61646f29ecd7bfcba6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2019
ms.locfileid: "70987856"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Passaggio 7: Aggiungere problemi di moltiplicazione e divisione

Nella settima parte di questa esercitazione si aggiungeranno i problemi di moltiplicazione e divisione, ma prima di procedere vedere come effettuare questa modifica. Considerare il passaggio iniziale, che comporta l'archiviazione dei valori.

> [!NOTE]
> Questo argomento fa parte di una serie di esercitazioni sui concetti di codifica di base. 
> - Per una panoramica dell'esercitazione, vedere [Esercitazione 2: Creare un quiz matematico a tempo (C#)](../ide/tutorial-2-create-a-timed-math-quiz.md). 
> - Per scaricare una versione completa del codice, vedere l' [esempio di esercitazione completa per i quiz matematici](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-add-multiplication-and-division-problems"></a>Per aggiungere problemi di moltiplicazione e divisione

1. Aggiungere altre quattro variabili di tipo Integer al modulo.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     > [!IMPORTANT]
     > Usare il controllo linguaggio di programmazione nella parte superiore destra della pagina per visualizzare il C# frammento di codice o il frammento di codice Visual Basic.<br><br>![Controllo del linguaggio di programmazione per Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

2. Come in precedenza, modificare il metodo `StartTheQuiz()` per inserire numeri casuali per i problemi di moltiplicazione e divisione.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. Modificare il metodo `CheckTheAnswer()` in modo che controlli anche i problemi di moltiplicazione e divisione.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Non è possibile immettere con facilità il segno di moltiplicazione (×) e di divisione (÷) tramite la tastiera. Visual C# e Visual Basic, quindi, accettano l'asterisco (*) per la moltiplicazione e la barra (/) per la divisione.

4. Modificare l'ultima parte del gestore dell'evento <xref:System.Windows.Forms.Timer.Tick> del timer in modo che inserisca la risposta corretta allo scadere del tempo.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. Salvare ed eseguire il programma.

     Gli esecutori del quiz devono risolvere quattro problemi per completare il quiz, come illustrato di seguito.

     ![Quiz matematico con quattro problemi](../ide/media/express_finishedquiz.png)<br/>
***Quiz matematico*** *con quattro problemi*

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere  **[passaggio 8: Personalizzare i quiz](../ide/step-8-customize-the-quiz.md).**

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 6: Aggiungere un problema di sottrazione](../ide/step-6-add-a-subtraction-problem.md).
