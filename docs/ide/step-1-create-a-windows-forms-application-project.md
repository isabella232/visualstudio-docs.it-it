---
title: 'Passaggio 1: Creare un progetto di app Windows FormStep 1: Create a Windows Forms App project'
ms.date: 08/30/2019
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d5e34d825d2a4d296a8a394105b412195b4e3fb
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579908"
---
# <a name="step-1-create-a-windows-forms-app-project"></a>Passaggio 1: Creare un progetto di app Windows FormStep 1: Create a Windows Forms App project

Quando si crea un visualizzatore di immagini, il primo passaggio consiste nel creare un progetto di app Windows Form.When you create a picture viewer, the first step is to create a Windows Forms App project.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Aprire Visual Studio 2017

1. Nella barra dei menu scegliere **File** > **Nuovo** > **progetto**. La finestra di dialogo avrà un aspetto simile allo screenshot seguente.

     ![Finestra di dialogo Nuovo progetto](../ide/media/newprojectdialogcallouts.png)<br/>***Finestra di dialogo*** *Nuovo progetto*

2. Sul lato sinistro della finestra di dialogo **Nuovo progetto** , scegliere **Visual C,** Visual Basic o **Visual Basic**, quindi Desktop **di Windows**.

3. Nell'elenco dei modelli di progetto scegliere **App Windows Form (.NET Framework)**. Assegnare il nome *PictureViewer* al nuovo form, quindi scegliere il pulsante **OK**.

    >[!NOTE]
    >Se non viene visualizzato il modello **App Windows Forms (.NET Framework)**, usare il programma di installazione di Visual Studio per installare il carico di lavoro **Sviluppo per desktop .NET**.<br/><br/>![Carico di lavoro Sviluppo per desktop .NET nel programma di installazione di Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Per altre informazioni, vedere la pagina [Installare Visual Studio](../install/install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Aprire Visual Studio 2019

1. Nella finestra di avvio scegliere **Crea un nuovo progetto.**

   ![Visualizzare la finestra Crea un nuovo progetto](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *Windows Forms* nella casella di ricerca. Scegliere quindi **Desktop** dall'elenco **Tipo di progetto.**

   Dopo aver applicato il filtro **di tipo Progetto,** scegliere il modello **di app Windows Form (.NET Framework)** per C'è o Visual Basic e quindi scegliere **Avanti**.

   ![Scegliere il modello di C o Visual Basic per l'app Windows Form (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Se il modello di **app Windows Form (.NET Framework)** non è visualizzato, è possibile installarlo dalla finestra Crea un nuovo **progetto.** Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > ![Collegamento "Installa altri strumenti e funzionalità" nel messaggio "L'elemento cercato non è stato trovato?" nella finestra "Crea un nuovo progetto"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Scegliere quindi il carico di lavoro **Sviluppo per desktop .NET** nel programma di installazione di Visual Studio.
   >
   > ![Carico di lavoro Sviluppo per desktop .NET nel programma di installazione di Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Successivamente, scegliere il pulsante **Modifica** nel programma di installazione di Visual Studio. Quando viene richiesto, salvare il lavoro. Scegliere quindi **Continua** per installare il carico di lavoro.

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *PictureViewer* nella casella **Nome del progetto**. Scegliere quindi **Crea,** quindi Crea .

::: moniker-end

Visual Studio crea una soluzione per l'app. Una soluzione funge da contenitore per tutti i progetti e i file necessari per l'app. Questi termini verranno spiegati dettagliatamente più avanti in questa esercitazione.

## <a name="about-the-windows-forms-app-project"></a>Informazioni sul progetto App Windows Form

1. L'ambiente di sviluppo include tre finestre: una finestra principale, **Esplora soluzioni** e **Proprietà**.

     Se una di queste finestre non è presente, è possibile ripristinare il layout predefinito della finestra. Nella barra dei **Window** > menu scegliere**Ripristina layout finestra**.

     È inoltre possibile visualizzare le finestre tramite i comandi di menu. Sulla barra dei menu scegliere **Visualizza** > **finestra Proprietà** o Esplora **soluzioni**.

     Se sono aperte altre finestre, chiuderle scegliendo il pulsante **Chiudi** (x) negli angoli in alto a destra.

    ::: moniker range="vs-2017"

    * **Finestra principale** In questa finestra viene eseguita la maggior parte del lavoro, come l'utilizzo dei form e la modifica del codice. La finestra visualizza un modulo nell'**editor di moduli**. Nella parte superiore della finestra vengono visualizzate la scheda **Pagina iniziale** e la scheda **Form1.cs [Progettazione]**. In Visual Basic il nome della scheda termina con *.vb* anziché *.cs*.

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    * **Finestra principale** In questa finestra viene eseguita la maggior parte del lavoro, come l'utilizzo dei form e la modifica del codice. La finestra visualizza un modulo nell'**editor di moduli**.

    ::: moniker-end

    * **Finestra Esplora soluzioni** In questa finestra è possibile visualizzare e passare a tutti gli elementi della soluzione.

    Se si sceglie un file, cambia il contenuto della finestra **Proprietà**. Se si apre un file di codice (che termina con *estensione cs* in C , e *vb* in Visual Basic), viene visualizzato il file di codice o una finestra di progettazione per il file di codice. Una finestra di progettazione è una superficie visiva in cui è possibile aggiungere controlli quali pulsanti ed elenchi. Per i form di Visual Studio, la finestra di progettazione è denominata **Progettazione Windows Form**.

    * **Finestra Proprietà** In questa finestra è possibile modificare le proprietà degli elementi scelti nelle altre finestre. Ad esempio, se si sceglie Form1, è possibile modificarne il titolo impostando la proprietà **Text** e il colore di sfondo impostando la proprietà **Backcolor**.

      > [!NOTE]
      > Nella riga superiore in **Esplora soluzioni** è riportata la dicitura **Soluzione "PictureViewer" (1 progetto)** per indicare che è stata creata una soluzione in Visual Studio. Una soluzione può contenere più progetti, ma per ora verranno utilizzate soluzioni che contengono un solo progetto.

1. Nella barra dei menu scegliere **Salva tutto.** > **Save All**

     In alternativa, scegliere il pulsante **Salva tutto** sulla barra degli strumenti, che viene visualizzata nell'immagine seguente.

     ![Pulsante della barra degli strumenti Salva tutto](../ide/media/express_iconsaveall.png)<br/>
     ***Pulsante Salva tutto*** *della barra degli strumenti*

     In Visual Studio il nome della cartella e il nome del progetto vengono compilati automaticamente. Il progetto viene quindi salvato nella cartella dei progetti.

## <a name="next-steps"></a>Passaggi successivi

* Per andare al passaggio successivo dell'esercitazione, vedere **[Passaggio 2: Eseguire l'app.](../ide/step-2-run-your-program.md)**

* Per tornare all'argomento Panoramica, vedere [Esercitazione 1: Creare un visualizzatore di immagini](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Vedere anche

* [Esercitazione 2: Creare un quiz di matematica a tempoTutorial 2: Create a timed math quiz](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: Creare un gioco corrispondente](tutorial-3-create-a-matching-game.md)
