---
title: Aggiungere gestori dell'evento Enter per i controlli NumericUpDown
description: Aggiungere i gestori dell'evento Enter per i controlli NumericUpDown nell'esercitazione creare un quiz matematico a tempo.
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: tutorial
dev_langs:
- CSharp
- VB
ms.assetid: 45a99a5d-c881-4298-b74d-adb481dec5ee
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 3be562e6af78101a86dca5e2567e4b0eb85033cc
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2021
ms.locfileid: "123397811"
---
# <a name="step-5-add-enter-event-handlers-for-the-numericupdown-controls"></a>Passaggio 5: Aggiungere gestori dell'evento Enter per i controlli NumericUpDown

Nella quinta parte di questa esercitazione si aggiungeranno i gestori dell'evento <xref:System.Windows.Forms.Control.Enter> per semplificare l'inserimento delle risposte ai problemi del quiz. Questo codice selezionerà e cancellerà il valore corrente di ogni controllo <xref:System.Windows.Forms.NumericUpDown> non appena l'esecutore del quiz sceglie il controllo e inizia a immettere un valore diverso.

> [!NOTE]
> Questo argomento fa parte di una serie di esercitazioni sui concetti di codifica di base. Per una panoramica dell'esercitazione, vedere [Esercitazione 2: Creare un quiz matematico a tempo.](../ide/tutorial-2-create-a-timed-math-quiz.md)

## <a name="to-verify-the-default-behavior"></a>Per verificare il comportamento predefinito

1. Eseguire il programma e avviare il quiz.

     Nel controllo **NumericUpDown** per il problema di addizione il cursore lampeggia accanto al valore **0** (zero).

2. Immettere **3** e osservare che il controllo mostra **30**.

3. Immettere **5** e osservare che viene visualizzato il valore **350**, che dopo un secondo cambia in **100**.

     Prima di correggere il problema, esaminare questo comportamento. Valutare il motivo per cui il valore **0** non è scomparso dopo avere immesso **3** e **350** è cambiato in **100** ma non immediatamente.

     Questo comportamento può risultare strano, ma è significativo secondo la logica del codice. Quando si fa clic sul pulsante **Avvia**, la proprietà **Enabled** viene impostata su **False** e il pulsante viene visualizzato in grigio e non è disponibile. Il programma imposta la selezione corrente (stato attivo) sul controllo con il successivo valore TabIndex più basso, ovvero il controllo NumericUpDown per il problema dell'addizione. Quando si preme **TAB** per passare a un controllo NumericUpDown, il cursore viene posizionato automaticamente all'inizio del controllo e per questo motivo i numeri immessi vengono visualizzati a sinistra e non a destra. Quando si specifica un numero maggiore del valore della proprietà **MaximumValue**, impostato su 100, il numero immesso viene sostituito con il valore di tale proprietà.

## <a name="to-add-an-enter-event-handler-for-a-numericupdown-control"></a>Per aggiungere un gestore eventi Enter per un controllo NumericUpDown

1. Scegliere il primo controllo **NumericUpDown** (denominato "sum") nel modulo e quindi nella finestra di dialogo **Proprietà** scegliere l'icona **Eventi** sulla barra degli strumenti.

   ![Pulsante Eventi nella barra degli strumenti delle proprietà](media/control-properties-events.png)

   La scheda **Eventi** nella finestra di dialogo **Proprietà** visualizza tutti gli eventi a cui è possibile rispondere (che è possibile gestire) per l'elemento scelto nel form. Poiché è stato scelto il controllo NumericUpDown, tutti gli eventi elencati sono relativi a esso.

2. Scegliere l'evento **Enter**, digitare `answer_Enter` e quindi premere **INVIO**.

   ![Nome del metodo del gestore dell'evento Enter](media/enter-event.png)

   Si è appena aggiunto un gestore eventi Enter per il controllo NumericUpDown della somma e il gestore è stato denominato **answer_Enter**.

3. Nel metodo per il gestore eventi **answer_Enter** aggiungere il codice seguente:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet11":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Sebbene il codice possa sembrare complesso, è facile da capire se lo si analizza passaggio per passaggio. Innanzitutto, osservare l'inizio del metodo: `object sender` in C# o `sender As System.Object` in Visual Basic. Questo parametro fa riferimento all'oggetto di cui viene generato l'evento, noto come mittente. In questo caso l'oggetto mittente è il controllo NumericUpDown. Pertanto, nella prima riga del metodo si specifica che il mittente non è un oggetto generico, ma è in maniera specifica un controllo NumericUpDown. Ogni controllo NumericUpDown è un oggetto , ma non tutti gli oggetti sono controlli NumericUpDown. Il controllo NumericUpDown è denominato **answerBox** in questo metodo, perché verrà usato per tutti i controlli NumericUpDown nel form, non solo per il controllo NumericUpDown somma. Poiché si dichiara la variabile answerBox in questo metodo, il relativo ambito è applicabile solo a questo metodo. In altre parole, è possibile utilizzare la variabile solo all'interno del metodo.

     La riga successiva verifica se answerBox è stato convertito (cast) correttamente da un oggetto in un controllo NumericUpDown. Se la conversione ha esito negativo, la variabile avrebbe un valore pari a `null` (C#) o `Nothing` (Visual Basic). La terza riga ottiene la lunghezza della risposta visualizzata nel controllo NumericUpDown, mentre la quarta riga seleziona il valore corrente nel controllo in base a tale lunghezza. A questo punto, quando l'esecutore del quiz sceglie il controllo, Visual Studio genera l'evento che determina la selezione della risposta corrente. Non appena l'esecutore del quiz inizia a immettere un'altra risposta, la risposta precedente viene cancellata e sostituita con la nuova.

4. In **Progettazione Windows Form** scegliere il controllo **NumericUpDown** per la differenza.

5. Nella pagina **Eventi** della finestra di dialogo **Proprietà** scorrere fino all'evento **Enter**, scegliere la freccia a discesa alla fine della riga, quindi scegliere il gestore eventi `answer_Enter` appena aggiunto.

6. Ripetere il passaggio precedente per i controlli NumericUpDown del prodotto e del quoziente.

7. Salvare ed eseguire il programma.

     Quando si sceglie un controllo **NumericUpDown**, il valore esistente viene selezionato automaticamente e quindi cancellato quando si inizia a immettere un valore diverso.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere **[Passaggio 6: Aggiungere un problema di sottrazione.](../ide/step-6-add-a-subtraction-problem.md)**

- Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 4: Aggiungere il metodo CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md).
