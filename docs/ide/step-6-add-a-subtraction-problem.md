---
title: 'Passaggio 6: Aggiungere un problema di sottrazione'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 611df946b97f97832b7debfac3d11c5b7972cdae
ms.sourcegitcommit: 10d16e18c5f5e482c4c2856e6cacaad283463b65
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2020
ms.locfileid: "75776096"
---
# <a name="step-6-add-a-subtraction-problem"></a>Passaggio 6: Aggiungere un problema di sottrazione
Nella sesta parte di questa esercitazione si aggiungerà un problema di sottrazione e si apprenderà come eseguire le attività seguenti:

- Archiviare i valori della sottrazione.

- Generare numeri casuali per il problema e verificare che la risposta sia compresa tra 0 e 100.

- Aggiornare il metodo che controlla le risposte in modo che verifichi anche il nuovo problema di sottrazione.

- Aggiornare il gestore dell'evento <xref:System.Windows.Forms.Timer.Tick> del timer in modo che inserisca la risposta corretta quando il tempo scade.

> [!NOTE]
> Questo argomento fa parte di una serie di esercitazioni sui concetti di codifica di base. Per una panoramica dell'esercitazione, vedere [Esercitazione 2: creare un quiz matematico a tempo](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-a-subtraction-problem"></a>Per aggiungere un problema di sottrazione

1. Aggiungere al form due variabili Integer per il problema di sottrazione, tra le variabili Integer per il problema di addizione e il timer. Il codice dovrebbe essere analogo al seguente.

     [!code-vb[VbExpressTutorial3Step5_6#12](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#12](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     I nomi delle nuove variabili Integer, **minuendo** e **sottraendo**, non sono termini di programmazione. Si tratta dei nomi tradizionali in aritmetica per il numero che si sta sottraendo (il sottraendo) e il numero da cui si sottrae (il minuendo). La differenza è il minuendo meno il sottraendo. È possibile utilizzare altri nomi, perché il programma non richiede nomi specifici per variabili, controlli, componenti o metodi. È necessario attenersi alle regole, ad esempio i nomi non devono iniziare con una cifra, ma è in genere possibile utilizzare nomi quali x1, x2, x3 e x4. Tuttavia, i nomi generici rendono il codice difficile da leggere e complicano il rilevamento dei problemi. Per mantenere univoci e significativi i nomi delle variabili, più avanti in questa esercitazione si useranno i nomi tradizionali per la moltiplicazione (moltiplicando × moltiplicatore = prodotto) e di divisione (dividendo ÷ divisore = quoziente).

     A questo punto, verrà modificato il metodo `StartTheQuiz()` per fornire valori casuali per il problema di sottrazione.

2. Aggiungere il codice seguente dopo il commento "Completare il problema di sottrazione".

     [!code-vb[VbExpressTutorial3Step5_6#13](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_2.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#13](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_2.cs)]

     Per evitare risposte negative per il problema di sottrazione, nel codice il metodo <xref:System.Random.Next> della classe <xref:System.Random> viene utilizzato in modo diverso rispetto al problema di addizione. Quando si assegnano due valori al metodo `Next()`, viene scelto un numero casuale maggiore o uguale al primo valore e minore del secondo. Nel codice seguente viene scelto un numero casuale da 1 a 100, che viene archiviato nella variabile minuendo.

     [!code-vb[VbExpressTutorial3Step5_6#21](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_3.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#21](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_3.cs)]

     È possibile chiamare in più modi il metodo `Next()` della classe Random, a cui in precedenza in questa esercitazione è stato assegnato il nome "randomizer". I metodi che è possibile chiamare in più modi sono denominati metodi di overload ed è possibile utilizzare IntelliSense per esplorarli. Esaminare nuovamente la descrizione comando della finestra di IntelliSense per il metodo `Next()`.

     ![descrizione comando della finestra IntelliSense](../ide/media/express_overloads.png)<br/>
*Descrizione comando della finestra* di IntelliSense

     La dicitura **(+ 2 overload(s))** della descrizione comando indica che è possibile chiamare il metodo `Next()` in altri due modi. Gli overload contengono numeri o tipi di argomenti diversi, pertanto funzionano in modo leggermente diverso l'uno dall'altro. Ad esempio, un metodo potrebbe accettare un singolo argomento Integer, mentre uno degli overload potrebbe accettare un Integer e una stringa. Scegliere l'overload corretto in base all'operazione da eseguire. Quando si aggiunge codice al metodo `StartTheQuiz()`, nella finestra di IntelliSense vengono visualizzate altre informazioni non appena si immette `randomizer.Next(`. Per scorrere gli overload, usare i tasti **freccia SU** e **freccia GIÙ**, come illustrato nella figura seguente:

     ![Overload per il metodo Next&#40;&#41; in IntelliSense](../ide/media/express_nextoverload.png)<br/>
*Overload per* il metodo ***Next ()*** *in* ***IntelliSense***

     In questo caso, si desidera scegliere l'ultimo overload, perché consente di specificare i valori minimo e massimo.

3. Modificare il metodo `CheckTheAnswer()` per verificare la risposta corretta per la sottrazione.

     [!code-vb[VbExpressTutorial3Step5_6#14](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_4.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#14](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_4.cs)]

     In C#`&&` è l'operatore `logical and`. In Visual Basic l'operatore equivalente è `AndAlso`. Questi operatori indicano "Se la somma di addendo1 e addendo2 è uguale al valore NumericUpDown della somma e se minuendo meno sottraendo è uguale al valore NumericUpDown della differenza". Il metodo `CheckTheAnswer()` restituisce `true` solo se le risposte ai problemi dell'addizione e della sottrazione sono corrette.

4. Sostituire l'ultima parte del gestore eventi Tick del timer con il codice seguente in modo che inserisca la risposta corretta alla scadenza del tempo.

     [!code-vb[VbExpressTutorial3Step5_6#22](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_5.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#22](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_5.cs)]

5. Salvare ed eseguire il codice.

     Il programma include un problema di sottrazione, come illustrato nella figura seguente:

     ![Quiz matematico con sottrazione](../ide/media/express_addsubtract.png)<br/>
***Quiz matematico*** *con problema di sottrazione*

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere **[passaggio 7: aggiungere problemi di moltiplicazione e divisione](../ide/step-7-add-multiplication-and-division-problems.md)** .

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 5: Aggiungere gestori dell'evento Enter per i controlli NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).
