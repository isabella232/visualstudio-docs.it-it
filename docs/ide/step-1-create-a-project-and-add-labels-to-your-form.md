---
title: 'Passaggio 1: Creare un progetto e aggiungere etichette al modulo'
description: Informazioni su come creare il progetto, aggiungere etichette, un pulsante e altri controlli a un form e impostare le proprietà per ogni controllo aggiunto.
ms.custom: SEO-VS-2020
ms.date: 10/15/2019
ms.topic: tutorial
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ffe6d669ae10603b1113bcb9ee87be63b076ddcf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628529"
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>Passaggio 1: Creare un progetto e aggiungere etichette al modulo

I passaggi iniziali dello sviluppo di questo quiz consistono nella creazione del progetto e nell'aggiunta di etichette, di un pulsante e di altri controlli a un modulo. Si impostano inoltre le proprietà di ogni controllo che si desidera aggiungere. Il progetto conterrà il modulo, i controlli e, più avanti nell'esercitazione, il codice. Il pulsante avvia il quiz, le etichette mostrano i problemi del quiz e gli altri controlli mostrano le risposte e il tempo rimanente per completarlo.

> [!NOTE]
> Questo argomento fa parte di una serie di esercitazioni sui concetti di codifica di base. Per una panoramica dell'esercitazione, vedere [Esercitazione 2: Creare un quiz matematico](../ide/tutorial-2-create-a-timed-math-quiz.md)a tempo.

## <a name="to-create-a-project-for-a-form"></a>Per creare un progetto da un modulo

::: moniker range="vs-2017"

1. Sulla barra dei menu scegliere **File** > **nuovo** > **Project**.

1. Scegliere **Visual C#** o **Visual Basic** sul lato destro della finestra di dialogo **Nuovo progetto** e quindi scegliere **Desktop di Windows**.

1. Nell'elenco di modelli scegliere il modello **App Windows Forms (.NET Framework)**, assegnare il nome *QuizMatematico* e quindi scegliere il pulsante **OK**.

    Verrà visualizzato un modulo con nome *Form1.cs* o *Form1.vb*, a seconda del linguaggio di programmazione scelto.

   > [!NOTE]
   > Se non viene visualizzato il modello **App Windows Forms (.NET Framework)**, usare il programma di installazione di Visual Studio per installare il carico di lavoro **Sviluppo per desktop .NET**.<br/><br/>![Carico di lavoro Sviluppo per desktop .NET nel programma di installazione di Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Per altre informazioni, vedere la pagina [Installare Visual Studio](../install/install-visual-studio.md).

::: moniker-end

::: moniker range=">=vs-2019"

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

   ![Visualizzare la finestra Crea un nuovo progetto](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *Windows Forms* nella casella di ricerca. Scegliere quindi **Desktop dall'elenco** **Project tipo di** dati.

   Dopo aver applicato il filtro **Project** tipo, scegliere il modello **Windows Forms App (.NET Framework)** per C# o Visual Basic e quindi scegliere **Avanti.**

   ![Scegliere il modello C# o Visual Basic per l'app Windows Forms (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Se il modello **App Windows Forms (.NET Core)** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo progetto**. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > ![Collegamento "Installa altri strumenti e funzionalità" nel messaggio "L'elemento cercato non è stato trovato?" nella finestra "Crea un nuovo progetto"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Nella finestra di dialogo Programma di installazione di Visual Studio quindi scegliere il carico di **lavoro Sviluppo desktop .NET.**
   >
   > ![Carico di lavoro Sviluppo per desktop .NET nel programma di installazione di Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Successivamente, scegliere il pulsante **Modifica** nel programma di installazione di Visual Studio. Quando viene richiesto, salvare il lavoro. Scegliere quindi **Continua** per installare il carico di lavoro.

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *QuizMatematico* nella casella **Nome del progetto**. Scegliere quindi **Crea**.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Per impostare le proprietà per un modulo

1. In Visual Studio scegliere il modulo (*Form1.cs* oppure *Form1.vb*, a seconda del linguaggio di programmazione) e quindi modificare la relativa proprietà **Testo** in **Quiz matematico**.

     La finestra **Proprietà** conterrà le proprietà per il modulo.

1. Impostare le dimensioni del modulo su 500 pixel di larghezza per 400 pixel di altezza.

     È possibile ridimensionare il modulo trascinando i relativi bordi finché le dimensioni corrette non compaiono nell'angolo inferiore sinistro dell'ambiente di sviluppo integrato (IDE). In alternativa, è possibile modificare i valori della proprietà **Size**.

1. Impostare il valore della proprietà **FormBorderStyle** su **Fixed3D** e la proprietà **MaximizeBox** su **False**.

     Questi valori impediranno agli esecutori del quiz di ridimensionare il modulo.

## <a name="to-create-the-time-remaining-box"></a>Per creare la casella relativa al tempo rimanente

1. Aggiungere un controllo <xref:System.Windows.Forms.Label> dalla **casella degli strumenti** e quindi impostare il valore della relativa proprietà **(Name)** su **timeLabel**.

     Questa etichetta diventerà una casella nell'angolo superiore destro in cui verrà visualizzato il numero di secondi rimanenti per il quiz.

2. Impostare la proprietà **AutoSize** su **False** in modo da poter ridimensionare la casella.

3. Impostare la proprietà **BorderStyle** su **FixedSingle** per disegnare una riga intorno alla casella.

4. Impostare la proprietà **Size** su **200, 30**.

5. Spostare l'etichetta nell'angolo superiore destro del modulo, dove verranno visualizzate righe dello spaziatore blu.

     Queste righe consentono di allineare i controlli nel modulo.

6. Nella finestra **Proprietà** scegliere la **proprietà Text** e quindi premere **BACKSPACE** per cancellarne il valore.

7. Scegliere il segno più ( ) accanto alla proprietà Font e quindi impostare il valore della proprietà **+** **Size** su **15,75.** 

     È possibile modificare diverse proprietà del tipo di carattere, come illustrato nella schermata seguente.

     ![Finestra Proprietà con la dimensione del carattere](../ide/media/express_setfontsize.png)

8. Aggiungere un altro controllo Etichetta dalla Casella **degli strumenti** e quindi impostarne le dimensioni del carattere su **15,75.**

9. Impostare la proprietà **Text** su **Tempo rimanente**.

10. Spostare l'etichetta in modo che risulti allineata a sinistra dell'etichetta **timeLabel**.

### <a name="to-add-controls-for-the-addition-problems"></a>Per aggiungere controlli per i problemi di addizione

1. Aggiungere un controllo Label dalla Casella **degli strumenti** e quindi impostarne la **proprietà Text** su **?** (punto interrogativo).

2. Impostare la proprietà **AutoSize** su **False**.

3. Impostare la proprietà **Size** su **60, 50**.

4. Impostare la dimensione del carattere su **18**.

5. Impostare la proprietà **TextAlign** su **MiddleCenter**.

6. Impostare la proprietà **Location** su **50, 75** per posizionare il controllo sul modulo.

7. Impostare la proprietà **(Name)** su **plusLeftLabel**.

8. Scegliere **l'etichetta plusLeftLabel** e quindi premere **CTRL** C o +  **Copia** dal menu **Modifica.**

9. Incollare l'etichetta tre volte scegliendo **CTRL** + **V** o **Incolla** dal menu Modifica. 

10. Disporre le tre nuove etichette in modo che risultino in fila a destra dell'etichetta **plusLeftLabel**.

     È possibile utilizzare le righe dello spaziatore per distanziarle e allinearle.

11. Impostare il valore della proprietà **Text** della seconda etichetta su **+** (segno più).

12. Impostare il valore della proprietà **(Name)** della terza etichetta su **plusRightLabel**.

13. Impostare il valore della proprietà **Text** della quarta etichetta su **=** (segno di uguale).

14. Aggiungere un controllo <xref:System.Windows.Forms.NumericUpDown> dalla **casella degli strumenti** e impostare la dimensione del carattere su **18** e la larghezza su **100**.

     Più avanti verranno fornite ulteriori informazioni su questo tipo di controllo.

15. Allineare il controllo NumericUpDown ai controlli Label per il problema di addizione.

16. Impostare il valore della proprietà **(Name)** per il controllo NumericUpDown su **somma**.

     È stata creata la prima riga, come illustrato nella figura seguente.

     ![Prima riga del quiz matematico](../ide/media/express_firstrow.png)

## <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Per aggiungere controlli per i problemi di sottrazione, moltiplicazione e divisione

1. Copiare tutti e cinque i controlli per il problema di addizione (i quattro controlli Label e il controllo NumericUpDown) e incollarli.

     Il modulo contiene cinque nuovi controlli, ancora selezionati.

2. Spostare tutti i controlli in modo che risultino allineati sotto i controlli di addizione.

     È possibile utilizzare le righe dello spaziatore per distanziare adeguatamente le due righe.

3. Impostare il valore della proprietà **Text** per la seconda etichetta su **-** (segno meno).

4. Assegnare alla prima etichetta punto interrogativo il nome **minusLeftLabel**.

5. Assegnare alla seconda etichetta punto interrogativo il nome **minusRightLabel**.

6. Denominare il controllo NumericUpDown **differenza**.

7. Incollare i cinque controlli altre due volte.

8. Per la terza riga, assegnare alla prima etichetta il nome **timesLeftLabel**, impostare la proprietà **Text** della seconda etichetta su **×** (segno di moltiplicazione), assegnare alla terza etichetta il nome **timesRightLabel** e assegnare al controllo NumericUpDown il nome **prodotto**.

9. Per la quarta riga, assegnare alla prima etichetta il nome **dividedLeftLabel**, impostare la proprietà **Text** della seconda etichetta su **÷** (segno di divisione), assegnare alla terza etichetta il nome **dividedRightLabel** e assegnare al controllo NumericUpDown il nome **quoziente**.

    > [!NOTE]
    > È possibile copiare il segno di moltiplicazione × e il segno di divisione ÷ da questa esercitazione e incollarli nel form.

## <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>Per aggiungere un pulsante di avvio e impostare l'ordine dell'indice di tabulazione

1. Aggiungere un controllo <xref:System.Windows.Forms.Button> dalla **casella degli strumenti** e quindi impostare la relativa proprietà **(Name)** su **startButton**.

2. Impostare la proprietà **Text** su **Avvia il quiz**.

3. Impostare la dimensione del carattere su **14**.

4. Impostare la proprietà **AutoSize** su **True**, in modo che il pulsante venga ridimensionato automaticamente per adattarsi al testo.

5. Centrare il pulsante nella parte inferiore del modulo.

6. Impostare il valore della proprietà **TabIndex** per il controllo **startButton** su **1**.

    > [!NOTE]
    > La **proprietà TabIndex** imposta l'ordine dei controlli quando l'emittente del quiz sceglie **tab.** Per visualizzare il funzionamento, aprire una qualsiasi finestra di dialogo, ad esempio sulla barra dei menu, scegliere **Apri** file e quindi premere  >   **TAB** più volte. Osservare il modo in cui il cursore si sposta dal controllo al controllo ogni volta che si sceglie **TAB.** Un programmatore ha deciso l'ordine quando ha creato il modulo.

7. Impostare il valore della proprietà **TabIndex** per il controllo somma NumericUpDown su **2**, per il controllo differenza su **3**, per il controllo prodotto su **4** e per il controllo quoziente su **5**.

     Il modulo dovrebbe essere simile allo screenshot seguente.

     ![Form iniziale del quiz matematico](../ide/media/express_formlaidout.png)

8. Per verificare se la proprietà **TabIndex** funziona come previsto, salvare ed eseguire il programma premendo **F5** o scegliendo **Debug** > **Avvia debug** sulla barra dei menu e quindi premere **TAB** alcune volte.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere **[Passaggio 2: Creare un problema di addizione casuale.](../ide/step-2-create-a-random-addition-problem.md)**

- Per tornare all'argomento di panoramica, vedere [Esercitazione 2: Creare un quiz matematico a tempo.](../ide/tutorial-2-create-a-timed-math-quiz.md)
