---
title: 'Passaggio 3: Impostare le proprietà del modulo'
description: Informazioni su come usare la Finestra Proprietà per modificare la modalità di ricerca del modulo.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b858ed302c7fe89049585edb7cc5c4391a4789b
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480616"
---
# <a name="step-3-set-your-form-properties"></a>Passaggio 3: Impostare le proprietà del modulo

In questo passaggio si usa la finestra **Proprietà** per modificare l'aspetto del form.

## <a name="how-to-set-your-form-properties"></a>Come impostare le proprietà del form

1. Assicurarsi che sia visualizzato **Progettazione Windows Form**. Nell'ambiente di sviluppo integrato (IDE) di Visual Studio, scegliere la scheda **Form1.cs [Design]** (o **Form1.vb [Design]** in Visual Basic).

1. Fare clic in qualsiasi punto all'interno del form **Form1** per selezionarlo. Analizzare la finestra **Proprietà**, che ora visualizza le proprietà per il form. I form dispongono di diverse proprietà. Ad esempio, è possibile impostare il colore primo piano e di sfondo, il testo del titolo visualizzato all'inizio del form, le dimensioni del form e altre proprietà.

   > [!NOTE]
   > Se la finestra **Proprietà** non viene visualizzata, arrestare l'app scegliendo il pulsante quadrato **Interrompi debug** sulla barra degli strumenti o semplicemente chiudere la finestra. Se l'app viene arrestata e la finestra **Proprietà** non è ancora visualizzata, sulla barra dei menu scegliere **Visualizza**  >  **finestra Proprietà**.

1. Dopo aver selezionato il form, individuare la proprietà **Testo** nella finestra **Proprietà**. A seconda di come è ordinato l'elenco, potrebbe essere necessario scorrere verso il basso. Scegliere **testo**, digitare **Visualizzatore immagini**, quindi premere **invio**.  Il form dovrebbe ora disporre del **Visualizzatore immagini** del testo nella relativa barra del titolo e la finestra **Proprietà** dovrebbe essere simile alla schermata seguente.

    ![Finestra Proprietà](../ide/media/express_edittextproperty.png)<br>
   **_Proprietà_* _ _window *

   > [!NOTE]
   > Le proprietà possono essere ordinate in base alla visualizzazione **Per categoria** o **Per nome**. È possibile passare da una visualizzazione all'altra tramite i pulsanti nella finestra **Proprietà**. In questa esercitazione è più facile trovare le proprietà tramite la visualizzazione **Per nome**.

1. Tornare a **Progettazione Windows Form**. Fare clic sul quadratino di trascinamento nella parte inferiore destra del form, ovvero il quadratino bianco in basso a destra del form il cui aspetto è il seguente.

    ![Quadratino di trascinamento](../ide/media/express_bottomrt_drag.png)<br>
   *Quadratino di trascinamento*

    Trascinare il punto di controllo per ridimensionare il form in modo che sia più largo e leggermente più alto.

1. Analizzare la finestra **Proprietà**. Si noti che la proprietà **Size** è stata modificata. La proprietà **Size** viene modificata ogni volta che si ridimensiona il form. Provare a trascinare il punto di controllo del modulo per ridimensionarlo approssimativamente alle dimensioni **550, 350** (non occorre essere precisi), che dovrebbero essere adatte per questo progetto. In alternativa, è possibile immettere i valori direttamente nella proprietà **size** , quindi premere il tasto **invio** .

1. Eseguire di nuovo l'app. Tenere presente che è possibile usare uno dei metodi seguenti per eseguire l'app.

   - Premere **F5**.

   - Sulla barra dei menu scegliere **debug**  >  **Avvia debug**.

   - Sulla barra degli strumenti scegliere il pulsante **Avvia debug** visualizzato di seguito.

      ![Pulsante della barra degli strumenti Avvia debug](../ide/media/express_icondebug.png)<br>
     **_Avvia debug_* _ _toolbar pulsante *

     Esattamente come in precedenza, l'IDE compila ed esegue l'app e viene visualizzata una finestra.

1. Prima di andare al passaggio successivo, arrestare l'app, perché l'IDE non consente di modificare l'app mentre è in esecuzione. Tenere presente che è possibile usare uno dei metodi seguenti per arrestare l'app.

   - Sulla barra degli strumenti scegliere il pulsante **Termina debug**.

   - Sulla barra dei menu scegliere **debug**  >  **Interrompi debug**.

   - Utilizzare la tastiera e premere **MAIUSC** + **F5**.

   - Scegliere il pulsante **X** nell'angolo superiore della finestra **Visualizzatore immagini** .

## <a name="next-steps"></a>Passaggi successivi

* Per andare al passaggio successivo dell'esercitazione, vedere **[passaggio 4: creare il layout del form con un controllo TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)**.

* Per tornare al passaggio precedente dell'esercitazione, vedere [passaggio 2: eseguire l'app visualizzatore immagini](../ide/step-2-run-your-program.md).

## <a name="see-also"></a>Vedi anche

* [Esercitazione 2: creare un quiz matematico a tempo](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: creare un gioco di abbinamenti](tutorial-3-create-a-matching-game.md)
