---
title: 'Passaggio 2: Creare un problema di addizione casuale'
description: Informazioni su come rendere il quiz complesso aggiungendo problemi matematici basati su numeri casuali.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 56089560652fd4d229e7cc4974f22169e1c6df43
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2021
ms.locfileid: "123397985"
---
# <a name="step-2-create-a-random-addition-problem"></a>Passaggio 2: Creare un problema di addizione casuale

Nella seconda parte di questa esercitazione vengono aggiunti al quiz problemi di matematica basati su numeri casuali. Viene inoltre creato un metodo denominato `StartTheQuiz()` che completa i problemi e avvia il timer del conto alla rovescia. Più avanti nell'esercitazione si aggiungeranno problemi di sottrazione, moltiplicazione e divisione.

> [!NOTE]
> Questo argomento fa parte di una serie di esercitazioni sui concetti di codifica di base. Per una panoramica dell'esercitazione, vedere [Esercitazione 2: Creare un quiz matematico a tempo.](../ide/tutorial-2-create-a-timed-math-quiz.md)

## <a name="to-create-a-random-addition-problem"></a>Per creare un problema di addizione casuale

1. Nella finestra di progettazione moduli scegliere il modulo (**Form1**).

2. Sulla barra dei menu scegliere **Visualizza**  >  **codice.**

     Viene visualizzato il file *Form1.cs* o *Form1.vb*, a seconda del linguaggio di programmazione in uso, per consentire di visualizzare il code-behind per il modulo.

3. Creare un oggetto <xref:System.Random> aggiungendo un'istruzione `new` nella parte superiore del codice, come illustrato di seguito.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet1":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Al modulo è stato aggiunto un oggetto Random denominato **randomizer**.

     `Random` è noto come oggetto. Probabilmente la parola oggetto è già stata incontrata. Nella prossima esercitazione ne verrà spiegato il significato in termini di programmazione. Per ora, è sufficiente ricordare che è possibile utilizzare le istruzioni `new` per creare pulsanti, etichette, panelli, elementi OpenFileDialog, ColorDialog, SoundPlayer, Random e form e che tali elementi sono definiti oggetti. Quando si esegue il programma, il modulo viene avviato e il code-behind crea un oggetto casuale, a cui viene assegnato il nome **randomizer**.

     Verrà quindi compilato un metodo per controllare le risposte, pertanto nel quiz è richiesto l'uso di variabili per archiviare numeri casuali generati per ciascun problema. Vedere [Variabili](/dotnet/visual-basic/programming-guide/language-features/variables/index) o [Tipi](/dotnet/csharp/programming-guide/types/index). Per utilizzare correttamente le variabili, è necessario dichiararle ovvero elencarne i nomi e i tipi di dati.

4. Aggiungere due variabili Integer al form e denominarle **addend1** e **addend2**.

    > [!NOTE]
    > Una variabile Integer è nota come int in C# o Integer in Visual Basic. Questo tipo di variabile archivia un numero intero positivo o negativo compreso tra -2147483648 e 2147483647 e non può archiviare numeri decimali.

     Aggiungere una variabile Integer usando una sintassi analoga a quella usata per aggiungere l'oggetto casuale, come illustrato nel codice seguente.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet2":::

5. Aggiungere un metodo denominato `StartTheQuiz()` che usa il metodo <xref:System.Random.Next> dell'oggetto Random per mostrare numeri casuali nelle etichette. `StartTheQuiz()` compilerà infine tutti i problemi e avvierà il timer. Aggiungere quindi un commento. La funzione dovrebbe essere simile alla seguente.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet3":::

     Si noti che quando si immette il punto (.) dopo `randomizer` nel codice, viene aperta una finestra di IntelliSense che mostra tutti i metodi dell'oggetto Random che è possibile chiamare. Ad esempio, in IntelliSense è elencato il metodo `Next()`, come indicato di seguito.

     ![Metodo Next](../ide/media/express_randomwhite.png)<br/>
*Metodo Next*

     Quando si inserisce un punto dopo un oggetto, IntelliSense mostra un elenco dei membri dell'oggetto, ad esempio proprietà, metodi ed eventi.

    > [!NOTE]
    > Quando si utilizza il metodo `Next()` con l'oggetto `Random`, ad esempio quando si chiama `randomizer.Next(50)`, si ottiene un numero casuale minore di 50 (compreso tra 0 e 49). In questo esempio, è stato chiamato `randomizer.Next(51)`. Viene utilizzato 51 e non 50 di modo che la somma dei due numeri casuali corrisponda a una risposta compresa tra 0 e 100. Se si passa 50 al metodo `Next()`, viene scelto un numero compreso tra 0 e 49, pertanto la risposta più alta possibile è 98, non 100. Dopo l'esecuzione delle prime due istruzioni nel metodo, ciascuna delle due variabili Integer, **addend1** e **addend2**, contiene un numero casuale compreso tra 0 e 50. Questo screenshot mostra il codice C#, ma IntelliSense funziona allo stesso modo per Visual Basic.

     Esaminare attentamente queste istruzioni.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet18":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet18":::

     Le istruzioni impostano le proprietà **Text** delle due etichette **plusLeftLabel** e **plusRightLabel**, in modo da visualizzare i due numeri casuali. È necessario utilizzare il metodo `ToString()` della variabile Integer per convertire i numeri in testo. In termini di programmazione, stringa significa testo. I controlli di etichetta visualizzare solo testo, non numeri.

6. Nella finestra di progettazione fare doppio clic sul pulsante **Avvia** o sceglierlo e quindi premere **INVIO**.

     Quando un esecutore del quiz sceglie il pulsante, viene avviato il quiz; è appena stato aggiunto un gestore dell'evento Click per implementare questo comportamento.

7. Aggiungere le due istruzioni riportate di seguito.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb" id="Snippet4":::

     La prima istruzione chiama il nuovo metodo `StartTheQuiz()`. La seconda imposta la proprietà **Enabled** del controllo **startButton** su **False** per impedire all'esecutore del quiz di scegliere il pulsante durante il quiz.

8. Salvare il codice, eseguirlo e scegliere il pulsante **Avvio**.

     Viene visualizzato un problema di addizione casuale, come illustrato nello screenshot seguente.

     ![Problema con addizione casuale](../ide/media/express_additionproblem.png)<br/>
*Problema con addizione casuale*

     Nel passaggio successivo dell'esercitazione, verrà aggiunta la somma.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere **[Passaggio 3: Aggiungere un timer per il conto alla rovescia.](../ide/step-3-add-a-countdown-timer.md)**

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 1: Creare un progetto e aggiungere etichette al modulo](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).
