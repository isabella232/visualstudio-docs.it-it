---
title: "Passaggio 4: Aggiungere un gestore dell'evento Click a ogni etichetta"
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9159ccec69bd6e8cad0290b092f38434b495fc6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954571"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>Passaggio 4: Aggiungere un gestore dell'evento Click a ogni etichetta

Il gioco delle coppie funziona come segue:

1. Quando un giocatore sceglie uno dei quadrati con un'icona nascosta, il programma mostra l'icona al giocatore facendola diventare nera.

2. Quindi il giocatore sceglie un'altra icona nascosta.

3. Se le icone corrispondono, restano visibili. In caso contrario, vengono nuovamente nascoste.

   Per far sì che il programma funzioni in questo modo, si aggiunge un gestore dell'evento <xref:System.Windows.Forms.Control.Click> che modifica il colore dell'etichetta scelta.

## <a name="to-add-a-click-event-handler-to-each-label"></a>Per aggiungere un gestore dell'evento Click a ogni etichetta

1.  Aprire il modulo in **Progettazione Windows Form**. In **Esplora soluzioni** scegliere *Form1.cs* o *Form1.vb*. Sulla barra dei menu scegliere **Visualizza** > **Finestra di progettazione**.

2.  Scegliere il primo controllo etichetta per selezionarlo. Tenere quindi premuto **CTRL** mentre si sceglie ognuna delle altre etichette per selezionarle. Assicurarsi che ogni etichetta sia selezionata.

3.  Fare clic sul pulsante **Eventi** della barra degli strumenti della finestra **Proprietà** per visualizzare la pagina **Eventi** nella finestra **Proprietà**. Scorrere verso il basso fino all'evento **Click** e immettere **label_Click** nella casella, come illustrato nell'immagine seguente.

     ![Finestra Proprietà con evento Click visualizzato](../ide/media/express_labelclick.png)

4.  Premere il tasto **INVIO**. L'IDE aggiunge al codice un gestore dell'evento `Click` denominato `label_Click()` e lo collega a ognuna delle etichette nel modulo.

5.  Compilare la parte restante di codice come segue:

     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/CSharp/step-4-add-a-click-event-handler-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/VisualBasic/step-4-add-a-click-event-handler-to-each-label_1.vb)]

    > [!NOTE]
    > Se si sceglie di copiare e incollare il blocco di codice `label_Click()` anziché immetterlo manualmente, è necessario verificare di sostituire il codice `label_Click()` esistente. In caso contrario, verrà generato un blocco di codice duplicato.

    > [!NOTE]
    > È possibile riconoscere `object sender` all'inizio del gestore eventi, uguale a quello usato in [Esercitazione 2: Creare un quiz matematico a tempo](../ide/tutorial-2-create-a-timed-math-quiz.md). Poiché eventi Click di diversi controlli etichetta sono stati collegati a un unico metodo del gestore, viene chiamato lo stesso metodo, indipendentemente dall'etichetta scelta dall'utente. Il metodo del gestore dell'evento deve sapere quale etichetta è stata scelta, quindi usa il nome `sender` per identificare il controllo etichetta. La prima riga del metodo indica al programma che non si tratta di un oggetto generico, bensì di un controllo etichetta e che questo oggetto usa il nome `clickedLabel` per accedere ai metodi e alle proprietà dell'etichetta.

     Questo metodo prima controlla se è stata eseguita correttamente la conversione (cast) di `clickedLabel` da un oggetto a un controllo etichetta. In caso contrario, il valore sarà `null` (C#) o `Nothing` (Visual Basic) e non è consigliabile eseguire la parte restante di codice nel metodo. Il metodo controlla quindi il colore del testo dell'etichetta scelta tramite la proprietà **ForeColor** dell'etichetta. Se il colore del testo dell'etichetta è nero, significa che l'icona è già stata scelta e il metodo è terminato. Questa è l'azione eseguita dall'istruzione `return`, che indica al programma di arrestare l'esecuzione del metodo. In caso contrario, l'icona non è stata scelta, pertanto il programma cambierà in nero il colore del testo dell'etichetta.

6.  Sulla barra dei menu scegliere **File** > **Salva tutto** per salvare lo stato di avanzamento e quindi, sempre sulla barra dei menu, scegliere **Debug** > **Avvia debug** per eseguire il programma. Si dovrebbe visualizzare un form vuoto con uno sfondo blu. Scegliere una cella qualsiasi nel form: una delle icone deve diventare visibile. Continuare a scegliere diversi punti nel form. Le icone scelte verranno visualizzate.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

-   Per procedere al passaggio successivo dell'esercitazione, vedere [Passaggio 5: Aggiungere riferimenti alle etichette](../ide/step-5-add-label-references.md).

-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 3: Assegnare un'icona casuale a ogni etichetta](../ide/step-3-assign-a-random-icon-to-each-label.md).
