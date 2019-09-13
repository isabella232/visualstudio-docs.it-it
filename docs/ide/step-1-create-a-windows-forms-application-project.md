---
title: 'Passaggio 1: Creare un progetto di app Windows Forms'
ms.date: 08/30/2019
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65339eabcffdf0f333036442ea8473ecf8c8f06e
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70888019"
---
# <a name="step-1-create-a-windows-forms-app-project"></a>Passaggio 1: Creare un progetto di app Windows Forms

Quando si crea un visualizzatore di immagini, il primo passaggio consiste nel creare un progetto di app Windows Forms.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Aprire Visual Studio 2017

1. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**. La finestra di dialogo avrà un aspetto simile allo screenshot seguente.

     ![Finestra di dialogo Nuovo progetto](../ide/media/newprojectdialogcallouts.png)<br/>***Finestra di dialogo*** *Nuovo progetto*

2. Sul lato sinistro della finestra di dialogo **nuovo progetto** scegliere **Visual C#**  o **Visual Basic**, quindi scegliere **desktop di Windows**.

3. Nell'elenco dei modelli di progetto scegliere **Windows Forms app (.NET Framework)** . Assegnare il nome *PictureViewer* al nuovo form, quindi scegliere il pulsante **OK**.

    >[!NOTE]
    >Se non viene visualizzato il modello **App Windows Forms (.NET Framework)** , usare il programma di installazione di Visual Studio per installare il carico di lavoro **Sviluppo per desktop .NET**.<br/><br/>![Carico di lavoro Sviluppo per desktop .NET nel programma di installazione di Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Per altre informazioni, vedere la pagina [Installare Visual Studio](../install/install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Aprire Visual Studio 2019

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

   ![Visualizzare la finestra Crea un nuovo progetto](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *Windows Forms* nella casella di ricerca. Scegliere quindi **Desktop** dall'elenco **tipo di progetto** .

   Dopo aver applicato il filtro del **tipo di progetto** , scegliere il modello **App Windows Forms (.NET Framework)** per C# o Visual Basic, quindi scegliere **Avanti**.

   ![Scegliere il C# modello per l'app Windows Forms (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Se non viene visualizzato il modello **App Windows Forms (.NET Framework)** , è possibile installarlo dalla finestra **Crea un nuovo progetto** . Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > ![Collegamento "Installa altri strumenti e funzionalità" nel messaggio "L'elemento cercato non è stato trovato?" nella finestra "Crea un nuovo progetto"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Scegliere quindi il carico di lavoro **Sviluppo per desktop .NET** nel programma di installazione di Visual Studio.
   >
   > ![Carico di lavoro Sviluppo per desktop .NET nel programma di installazione di Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Scegliere quindi il pulsante **Modifica** nel programma di installazione di Visual Studio. Quando viene richiesto, salvare il lavoro. Scegliere quindi **Continua** per installare il carico di lavoro.

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *PictureViewer* nella casella **Nome del progetto**. Scegliere **Crea**.

::: moniker-end

Visual Studio crea una soluzione per l'app. Una soluzione funge da contenitore per tutti i progetti e i file necessari per l'app. Questi termini verranno spiegati dettagliatamente più avanti in questa esercitazione.

## <a name="about-the-windows-forms-app-project"></a>Informazioni sul progetto app Windows Forms

1. L'ambiente di sviluppo include tre finestre: una finestra principale, **Esplora soluzioni** e **Proprietà**.

     Se una di queste finestre non è presente, è possibile ripristinare il layout predefinito della finestra. Sulla barra dei menu scegliere **finestra** > **Reimposta layout finestra**.

     È inoltre possibile visualizzare le finestre tramite i comandi di menu. Sulla barra dei menu scegliere **Visualizza** > **Finestra Proprietà** o **Esplora soluzioni**.

     Se sono aperte altre finestre, chiuderle scegliendo il pulsante **Chiudi** (x) negli angoli in alto a destra.

    ::: moniker range="vs-2017"

    * **Finestra principale** In questa finestra viene eseguita la maggior parte del lavoro, come l'utilizzo dei form e la modifica del codice. La finestra visualizza un modulo nell'**editor di moduli**. Nella parte superiore della finestra vengono visualizzate la scheda **Pagina iniziale** e la scheda **Form1.cs [Progettazione]** . In Visual Basic il nome della scheda termina con l'estensione *VB* invece di *CS*.

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    * **Finestra principale** In questa finestra viene eseguita la maggior parte del lavoro, come l'utilizzo dei form e la modifica del codice. La finestra visualizza un modulo nell'**editor di moduli**.

    ::: moniker-end

    * **Finestra Esplora soluzioni** In questa finestra è possibile visualizzare tutti gli elementi della soluzione e spostarsi tra di essi.

    Se si sceglie un file, cambia il contenuto della finestra **Proprietà**. Se si apre un file di codice (che termina con *. cs* in C# e *. vb* in Visual Basic), viene visualizzato il file di codice o una finestra di progettazione per il file di codice. Una finestra di progettazione è una superficie visiva in cui è possibile aggiungere controlli quali pulsanti ed elenchi. Per i moduli di Visual Studio, la finestra di progettazione è denominata **Progettazione Windows Form**.

    * **Finestra Proprietà** In questa finestra è possibile modificare le proprietà degli elementi scelti nelle altre finestre. Ad esempio, se si sceglie Form1, è possibile modificarne il titolo impostando la proprietà **Text** e il colore di sfondo impostando la proprietà **Backcolor**.

      > [!NOTE]
      > Nella riga superiore in **Esplora soluzioni** è riportata la dicitura **Soluzione "PictureViewer" (1 progetto)** per indicare che è stata creata una soluzione in Visual Studio. Una soluzione può contenere più progetti, ma per ora verranno utilizzate soluzioni che contengono un solo progetto.

1. Sulla barra dei menu scegliere **File** > **Salva tutto**.

     In alternativa, scegliere il pulsante **Salva tutto** sulla barra degli strumenti, mostrata nell'immagine seguente.

     ![Pulsante della barra degli strumenti Salva tutto](../ide/media/express_iconsaveall.png)<br/>
     ***Salva tutto*** *pulsante della barra degli strumenti*

     In Visual Studio il nome della cartella e il nome del progetto vengono compilati automaticamente. Il progetto viene quindi salvato nella cartella dei progetti.

## <a name="next-steps"></a>Passaggi successivi

* Per andare al passaggio successivo dell'esercitazione, vedere  **[passaggio 2: Eseguire l'app](../ide/step-2-run-your-program.md).**

* Per tornare all'argomento introduttivo, vedere [Esercitazione 1: Creare un visualizzatore di immagini](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Vedere anche

* [Esercitazione 2: Creare un quiz matematico a tempo](tutorial-2-create-a-timed-math-quiz.md)
* [Esercitazione 3: Creare un gioco di abbinamenti](tutorial-3-create-a-matching-game.md)
