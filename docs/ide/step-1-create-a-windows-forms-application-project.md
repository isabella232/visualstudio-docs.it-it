---
title: 'Passaggio 1: Creare un progetto di Windows Forms Application'
ms.date: 03/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f529d737816406b3a4f6aa9921a8dc6b902d2fb
ms.sourcegitcommit: b14b7a938a2aba9fcce4d5e813aadf2040b0dcda
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2019
ms.locfileid: "58647362"
---
# <a name="step-1-create-a-windows-forms-application-project"></a>Passaggio 1: Creare un progetto di Windows Forms Application

Quando si crea un visualizzatore di immagini, il primo passaggio consiste nella creazione di un progetto di Windows Forms Application.

 > [!TIP]
 > ![Collegamento a video](../data-tools/media/playvideo.gif)Per una versione video di questo argomento, vedere [Esercitazione 1: Creare un visualizzatore di immagini in Visual Basic - Video 1](http://go.microsoft.com/fwlink/?LinkId=205209) o [Esercitazione 1: Creare un visualizzatore immagini in C# - Video 1](http://go.microsoft.com/fwlink/?LinkId=205199). In questi video viene usata una versione precedente di Visual Studio, pertanto vi sono piccole differenze in alcuni comandi di menu e altri elementi dell'interfaccia utente. Tuttavia, i concetti e le procedure funzionano in modo analogo nella versione corrente di Visual Studio.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Aprire Visual Studio 2017

1. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**. Verrà visualizzata una finestra di dialogo simile alla seguente.

     ![Finestra di dialogo Nuovo progetto](../ide/media/newprojectdialogcallouts.png)<br/>
*Finestra di dialogo **Nuovo progetto***

2. Scegliere **Visual C#** o **Visual Basic** sul lato destro della finestra di dialogo **Nuovo progetto**.

3. Nell'elenco dei modelli scegliere **App Windows Forms (.NET Framework)**. Assegnare il nome **PictureViewer** al nuovo form, quindi scegliere il pulsante **OK**.

    >[!NOTE]
    >Se non viene visualizzato il modello **App Windows Forms (.NET Framework)**, usare il programma di installazione di Visual Studio per installare il carico di lavoro **Sviluppo per desktop .NET**.<br/><br/>![Carico di lavoro Sviluppo per desktop .NET nel programma di installazione di Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Per altre informazioni, vedere la pagina [Installare Visual Studio](../install/install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Aprire Visual Studio 2019

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

   ![Visualizzare la finestra "Crea un nuovo progetto" ](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *Windows Forms* nella casella di ricerca. Quindi scegliere **Visual Basic** dall'elenco Linguaggio e **Windows** dall'elenco Piattaforma. 

   Dopo aver applicato i filtri di linguaggio e piattaforma, scegliere il modello **App Windows Forms (.NET Core)** e quindi scegliere **Avanti**.

   ![Scegliere il modello Visual Basic per l'app Windows Forms (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Se il modello **App Windows Forms (.NET Core)** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo progetto**. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
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

Visual Studio crea una soluzione per il programma. Una soluzione funge da contenitore per tutti i progetti e i file richiesti dal programma. Questi termini verranno spiegati dettagliatamente più avanti in questa esercitazione.

## <a name="about-the-windows-forms-application-project"></a>Informazioni sul progetto Applicazione Windows Forms

1. L'ambiente di sviluppo include tre finestre: una finestra principale, **Esplora soluzioni** e **Proprietà**.

     Se manca una di queste finestre, ripristinare il layout di finestra predefinito, scegliendo **Finestra** > **Reimposta layout finestra** sulla barra dei menu. È inoltre possibile visualizzare le finestre tramite i comandi di menu. Sulla barra dei menu scegliere **Visualizza** > **Finestra Proprietà** o **Esplora soluzioni**. Se sono aperte altre finestre, chiuderle scegliendo il pulsante **Chiudi** (x) negli angoli in alto a destra.

    ::: moniker range="vs-2017"

    - **Finestra principale** In questa finestra viene eseguita la maggior parte del lavoro, come l'utilizzo dei form e la modifica del codice. La finestra visualizza un modulo nell'**editor di moduli**. Nella parte superiore della finestra vengono visualizzate la scheda **Pagina iniziale** e la scheda **Form1.cs [Progettazione]**. In Visual Basic il nome della scheda termina con l'estensione *VB* invece di *CS*.

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    - **Finestra principale** In questa finestra viene eseguita la maggior parte del lavoro, come l'utilizzo dei form e la modifica del codice. La finestra visualizza un modulo nell'**editor di moduli**.

    ::: moniker-end

    - **Finestra Esplora soluzioni** In questa finestra è possibile visualizzare tutti gli elementi della soluzione e spostarsi tra di essi. Se si sceglie un file, cambia il contenuto della finestra **Proprietà**. Se si apre un file di codice (che termina con l'estensione *CS* in Visual C# e *VB* in Visual Basic), viene visualizzato il file stesso o la relativa finestra di progettazione. Una finestra di progettazione è una superficie visiva in cui è possibile aggiungere controlli quali pulsanti ed elenchi. Per i moduli di Visual Studio, la finestra di progettazione è denominata **Progettazione Windows Form**.

    - **Finestra Proprietà** In questa finestra è possibile modificare le proprietà degli elementi scelti nelle altre finestre. Ad esempio, se si sceglie Form1, è possibile modificarne il titolo impostando la proprietà **Text** e il colore di sfondo impostando la proprietà **Backcolor**.

    > [!NOTE]
    > Nella riga superiore in **Esplora soluzioni** è riportata la dicitura **Soluzione "PictureViewer" (1 progetto)** per indicare che è stata creata una soluzione in Visual Studio. Una soluzione può contenere più progetti, ma per ora verranno utilizzate soluzioni che contengono un solo progetto.

1. Sulla barra dei menu scegliere **File** > **Salva tutto**.

     In alternativa, scegliere il pulsante **Salva tutto** sulla barra degli strumenti, come illustrato nella figura seguente.

     ![Pulsante della barra degli strumenti Salva tutto](../ide/media/express_iconsaveall.png)<br/>
     *Pulsante della barra degli strumenti **Salva tutto***

     In Visual Studio il nome della cartella e il nome del progetto vengono compilati automaticamente. Il progetto viene quindi salvato nella cartella dei progetti.

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per procedere al passaggio successivo dell'esercitazione, vedere [Passaggio 2: Eseguire il programma](../ide/step-2-run-your-program.md).

- Per tornare all'argomento introduttivo, vedere [Esercitazione 1: Creare un visualizzatore di immagini](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Vedere anche

- [Creazione di un nuovo Windows Form](/dotnet/framework/winforms/creating-a-new-windows-form/)