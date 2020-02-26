---
title: 'Passaggio 7: Aggiungere problemi di moltiplicazione e divisione'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92a1744b68ad043dcee21dcb5995fbd1908bd81b
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579787"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Passaggio 7: Aggiungere problemi di moltiplicazione e divisione

Nella settima parte di questa esercitazione si aggiungeranno i problemi di moltiplicazione e divisione, ma prima di procedere vedere come effettuare questa modifica. Considerare il passaggio iniziale, che comporta l'archiviazione dei valori.

> [!NOTE]
> Questo argomento fa parte di una serie di esercitazioni sui concetti di codifica di base. Per una panoramica dell'esercitazione, vedere [Esercitazione 2: creare un quiz matematico a tempo](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-multiplication-and-division-problems"></a>Per aggiungere problemi di moltiplicazione e divisione

1. Aggiungere altre quattro variabili di tipo Integer al modulo.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. Come in precedenza, modificare il metodo `StartTheQuiz()` per inserire numeri casuali per i problemi di moltiplicazione e divisione.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. Modificare il metodo `CheckTheAnswer()` in modo che controlli anche i problemi di moltiplicazione e divisione.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Non è possibile immettere facilmente il segno di moltiplicazione (×) e il segno di divisione (÷) usando la C# tastiera, quindi e Visual Basic accettano un asterisco (*) per la moltiplicazione e una barra (/) per la divisione.

4. Modificare l'ultima parte del gestore dell'evento <xref:System.Windows.Forms.Timer.Tick> del timer in modo che inserisca la risposta corretta allo scadere del tempo.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. Salvare ed eseguire il programma.

     Gli esecutori del quiz devono risolvere quattro problemi per completare il quiz, come illustrato di seguito.

     ![Quiz matematico con quattro problemi](../ide/media/express_finishedquiz.png)<br/>
***Quiz matematico*** *con quattro problemi*

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere **[passaggio 8: personalizzare il quiz](../ide/step-8-customize-the-quiz.md)** .

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 6: Aggiungere un problema di sottrazione](../ide/step-6-add-a-subtraction-problem.md).
