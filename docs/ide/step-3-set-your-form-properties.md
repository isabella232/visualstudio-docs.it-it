---
title: 'Passaggio 3: Impostare le proprietà del modulo'
description: Informazioni su come usare il Finestra Proprietà per modificare l'aspetto del modulo.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
ms.topic: tutorial
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: d6d67536e525e6e5d97b0e54ffdabea378e6ee10f7405016c3c7ff929664ed74
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121399574"
---
# <a name="step-3-set-your-form-properties"></a>Passaggio 3: Impostare le proprietà del modulo

In questo passaggio si usa la finestra **Proprietà** per modificare l'aspetto del form.

## <a name="how-to-set-your-form-properties"></a>Come impostare le proprietà del modulo

1. Assicurarsi che sia visualizzato **Progettazione Windows Form**. Nell'ambiente di sviluppo integrato (IDE) di Visual Studio, scegliere la scheda **Form1.cs [Design]** (o **Form1.vb [Design]** in Visual Basic).

1. Fare clic in qualsiasi punto all'interno del form **Form1** per selezionarlo. Analizzare la finestra **Proprietà**, che ora visualizza le proprietà per il form. I form dispongono di diverse proprietà. Ad esempio, è possibile impostare il colore primo piano e di sfondo, il testo del titolo visualizzato all'inizio del form, le dimensioni del form e altre proprietà.

   > [!NOTE]
   > Se la **finestra Proprietà** non viene visualizzata, arrestare l'app scegliendo il pulsante arresta debug quadrato sulla barra degli strumenti o chiudendo semplicemente la finestra.  Se l'app viene arrestata e  la finestra Proprietà non è ancora visualizzata, scegliere **Visualizza** finestra Proprietà sulla barra  >  **dei** menu.

1. Dopo aver selezionato il form, individuare la proprietà **Testo** nella finestra **Proprietà**. A seconda di come è ordinato l'elenco, potrebbe essere necessario scorrere verso il basso. Scegliere **Testo,** digitare **Visualizzatore immagini** e quindi premere **INVIO.**  Il modulo dovrebbe ora avere il testo **Visualizzatore** immagini nella barra del titolo e la **finestra** Proprietà dovrebbe essere simile allo screenshot seguente.

    ![Finestra Proprietà](../ide/media/express_edittextproperty.png)<br>
   ***Proprietà** _ _window*

   > [!NOTE]
   > Le proprietà possono essere ordinate in base alla visualizzazione **Per categoria** o **Per nome**. È possibile passare da una visualizzazione all'altra tramite i pulsanti nella finestra **Proprietà**. In questa esercitazione è più facile trovare le proprietà tramite la visualizzazione **Per nome**.

1. Tornare a **Progettazione Windows Form**. Fare clic sul quadratino di trascinamento nella parte inferiore destra del form, ovvero il quadratino bianco in basso a destra del form il cui aspetto è il seguente.

    ![Trascinare il quadratino di ridimensionamento](../ide/media/express_bottomrt_drag.png)<br>
   *Trascinare il quadratino di ridimensionamento*

    Trascinare il punto di controllo per ridimensionare il form in modo che sia più largo e leggermente più alto.

1. Analizzare la finestra **Proprietà**. Si noti che la proprietà **Size** è stata modificata. La proprietà **Size** viene modificata ogni volta che si ridimensiona il form. Provare a trascinare il punto di controllo del modulo per ridimensionarlo approssimativamente alle dimensioni **550, 350** (non occorre essere precisi), che dovrebbero essere adatte per questo progetto. In alternativa, è possibile immettere i valori direttamente nella proprietà **Size** e quindi premere **INVIO.**

1. Eseguire di nuovo l'app. Tenere presente che è possibile usare uno dei metodi seguenti per eseguire l'app.

   - Premere **F5**.

   - Sulla barra dei menu scegliere **Debug**  >  **Avvia debug**.

   - Sulla barra degli strumenti scegliere il pulsante **Avvia debug** visualizzato di seguito.

      ![Pulsante della barra degli strumenti Avvia debug](../ide/media/express_icondebug.png)<br>
     ***Avviare il debug** _ _toolbar pulsante*

     Come in precedenza, l'IDE compila ed esegue l'app e viene visualizzata una finestra.

1. Prima di andare al passaggio successivo, arrestare l'app, perché l'IDE non consente di modificare l'app mentre è in esecuzione. Tenere presente che è possibile usare uno dei metodi seguenti per arrestare l'app.

   - Sulla barra degli strumenti scegliere il pulsante **Termina debug**.

   - Sulla barra dei menu scegliere **Debug**  >  **Arresta debug**.

   - Usare la tastiera e premere **MAIUSC** + **F5.**

   - Scegliere il **pulsante X** nell'angolo superiore della finestra **di Visualizzatore** immagini.

## <a name="next-steps"></a>Passaggi successivi

* Per andare al passaggio successivo dell'esercitazione, vedere Passaggio 4: Eseguire il layout **[del form con un controllo TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)**.

* Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 2: Eseguire l'app visualizzatore di immagini](../ide/step-2-run-your-program.md).

## <a name="see-also"></a>Vedi anche

* [Esercitazione 2: Creare un quiz matematico a tempo](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: Creare un gioco corrispondente](tutorial-3-create-a-matching-game.md)
