---
title: 'Passaggio 1: Creare un progetto e aggiungere una tabella al modulo'
description: Informazioni su come creare il progetto Matching Game e aggiungere una tabella al modulo.
ms.custom: SEO-VS-2020
ms.date: 10/15/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ed4c6b3c65cc7a4c68288c01964388bbf8ec54a0
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306423"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>Passaggio 1: Creare un progetto e aggiungere una tabella al modulo

Il primo passaggio nella creazione di un gioco delle coppie consiste nel creare il progetto e aggiungere una tabella al form. La tabella consente di allineare le icone in una griglia ordinata 4x4. È inoltre possibile impostare diverse proprietà per migliorare l'aspetto della tavola da gioco.

## <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Per creare un progetto e aggiungere una tabella al form

::: moniker range="vs-2017"

1. Sulla barra dei menu scegliere **File** > **nuovo** > **progetto**.

1. Scegliere **Visual C#** o **Visual Basic** sul lato destro della finestra di dialogo **Nuovo progetto** e quindi scegliere **Desktop di Windows**.

1. Nell'elenco di modelli scegliere il modello **App Windows Forms (.NET Framework)**, assegnare il nome *MatchingGame* e quindi scegliere il pulsante **OK**.

    Verrà visualizzato un modulo con nome *Form1.cs* o *Form1.vb*, a seconda del linguaggio di programmazione scelto.

   > [!NOTE]
   > Se non viene visualizzato il modello **App Windows Forms (.NET Framework)**, usare il programma di installazione di Visual Studio per installare il carico di lavoro **Sviluppo per desktop .NET**.<br/><br/>![Carico di lavoro Sviluppo per desktop .NET nel programma di installazione di Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Per altre informazioni, vedere la pagina [Installare Visual Studio](../install/install-visual-studio.md).

::: moniker-end

::: moniker range=">=vs-2019"

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

   ![Visualizzare la finestra Crea un nuovo progetto](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *Windows Forms* nella casella di ricerca. Scegliere Quindi Desktop **dall'elenco Tipo di** progetto. 

   Dopo aver applicato **il** filtro Tipo di progetto, scegliere il modello app Windows Forms **(.NET Framework)** per C# o Visual Basic e quindi scegliere **Avanti.**

   ![Scegliere il modello C# o Visual Basic per l'app Windows Forms (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Se il modello **App Windows Forms (.NET Core)** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo progetto**. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**.
   >
   > ![Collegamento "Installa altri strumenti e funzionalità" nel messaggio "L'elemento cercato non è stato trovato?" nella finestra "Crea un nuovo progetto"](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Scegliere quindi il carico di lavoro **Sviluppo per desktop .NET** nel programma di installazione di Visual Studio.
   >
   > ![Carico di lavoro Sviluppo per desktop .NET nel programma di installazione di Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Successivamente, scegliere il pulsante **Modifica** nel programma di installazione di Visual Studio. Quando viene richiesto, salvare il lavoro. Scegliere quindi **Continua** per installare il carico di lavoro.

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *MatchingGame* nella casella **Nome del progetto**. Scegliere quindi **Crea**.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Per impostare le proprietà per un modulo

1. Nella finestra **Proprietà** impostare le proprietà del form seguenti.

   1. Modificare la proprietà **Text** del form da **Form1** a **Matching Game**. Questo testo viene visualizzato nella parte superiore della finestra del gioco.

   2. Impostare le dimensioni del form su 550 pixel di larghezza per 550 pixel di altezza. A tale scopo, impostare la proprietà **Size** su **550, 550** o trascinare l'angolo del form fino a raggiungere le dimensioni corrette nell'angolo inferiore destro dell'IDE (Integrated Development Environment).

2. Per visualizzare la casella degli strumenti, selezionare la scheda **Casella degli strumenti** sul lato sinistro dell'IDE.

3. Trascinare un controllo <xref:System.Windows.Forms.TableLayoutPanel> dalla categoria **Contenitori** nella casella degli strumenti e quindi impostare le proprietà seguenti.

   1. Impostare la proprietà **BackColor** su **CornflowerBlue**. A tale scopo, aprire la finestra di dialogo **Colore sfondo** scegliendo la freccia a discesa accanto alla proprietà **BackColor** nella finestra **Proprietà**.  Quindi, scegliere la scheda **Web** nella finestra di dialogo **Colore sfondo** per visualizzare un elenco di nomi di colore disponibili.

      > [!NOTE]
      > I colori non sono in ordine alfabetico e **CornflowerBlue** è verso la fine dell'elenco.

   2. Impostare la proprietà **Dock** su **Fill** scegliendo il pulsante a discesa accanto alla proprietà, quindi il pulsante grande al centro. La tabella verrà espansa per includere l'intero form.

   3. Impostare la proprietà **CellBorderStyle** su **Inset**. Verranno creati bordi visivi tra ogni cella nella lavagna.

   4. Scegliere il pulsante triangolare nell'angolo superiore destro di TableLayoutPanel per visualizzarne il menu delle attività.

   5. Nel menu delle attività scegliere **Aggiungi riga** due volte per aggiungere altre due righe, quindi scegliere **Aggiungi colonna** due volte per aggiungere altre due colonne.

   6. Nel menu delle attività scegliere **Modifica righe e colonne** per aprire la finestra **Stili di riga e colonna**. Scegliere ognuna delle colonne, fare clic sul pulsante di opzione **%** e quindi impostare la larghezza di ogni colonna sul 25% della larghezza totale. Selezionare quindi **Righe** dalla casella a discesa nella parte superiore della finestra e impostare l'altezza di ogni riga su 25%. Al termine dell'operazione, fare clic su **OK**.

      TableLayoutPanel dovrebbe essere ora costituito da una griglia 4x4 con sedici celle quadrate di dimensioni uguali. In queste righe e colonne appariranno in un secondo momento le immagini icona.

4. Accertarsi che TableLayoutPanel sia selezionato nell'editor del form. A tale scopo, verificare che **tableLayoutPanel1** sia visualizzato nella parte superiore della finestra **Proprietà**. Se non è già selezionato, scegliere TableLayoutPanel nel form oppure nel controllo a discesa nella parte superiore della finestra **Proprietà**.

    Mentre TableLayoutPanel è selezionato, aprire la casella degli strumenti e aggiungere un controllo <xref:System.Windows.Forms.Label> (che si trova nella categoria **Controlli comuni**) alla cella superiore sinistra di TableLayoutPanel. Il controllo etichetta dovrebbe ora essere selezionato nell'IDE. Impostare le proprietà indicate di seguito.

   1. Verificare che la proprietà **BackColor** dell'etichetta sia impostata su **CornflowerBlue**.

   2. Impostare la proprietà **AutoSize** su **False**.

   3. Impostare la proprietà **Dock** su **Fill**.

   4. Impostare la proprietà **TextAlign** su **MiddleCenter** scegliendo il pulsante a discesa accanto alla proprietà, quindi il pulsante al centro. In questo modo l'icona verrà visualizzata al centro della cella.

   5. Scegliere la proprietà **Font**. Verrà visualizzato un pulsante con i puntini di sospensione (**...**).

   6. Scegliere il pulsante con i puntini di sospensione e impostare **Tipo di carattere** su **Webdings**, **Stile** su **Grassetto** e **Dimensione** su **48**.

   7. Impostare la proprietà **Text** dell'etichetta sulla lettera **c**.

        La cella superiore sinistra in TableLayoutPanel dovrebbe ora contenere un riquadro nero al centro su uno sfondo blu.

       > [!NOTE]
       > Il tipo di carattere Webdings include una serie di icone ed è fornito con il sistema operativo Windows. Nel gioco delle coppie, il giocatore deve riuscire ad accoppiare le icone, per cui si utilizza questo tipo di carattere per visualizzare le icone da accoppiare. Anziché inserire **c** nella proprietà **Text**, provare a immettere lettere diverse per vedere quali icone vengono visualizzate. Il punto esclamativo equivale a un ragno, la N maiuscola a un occhio e la virgola a un peperoncino.

5. Scegliere il controllo Label e copiarlo nella cella successiva in TableLayoutPanel. (Scegliere **CTRL** + **Tasti C** oppure sulla barra dei menu scegliere  >  **Modifica copia.** Incollarlo quindi. (Scegliere **CTRL** + **Tasti V** oppure sulla barra dei menu scegliere **Modifica**  >  **Incolla.** Nella seconda cella di TableLayoutPanel viene visualizzata una copia della prima etichetta. Incollare di nuovo e nella terza cella verrà visualizzata un'altra etichetta. Continuare a incollare i controlli Label fino a riempire tutte le celle.

   > [!NOTE]
   > Se si incolla troppe volte, l'IDE aggiunge una nuova riga a TableLayoutPanel, in modo da creare una posizione dove aggiungere il nuovo controllo Label. L'azione può essere annullata. Per rimuovere la nuova cella, premere **CTRL** Z oppure scegliere Modifica Annulla sulla +  barra dei   >  menu.

    A questo punto il modulo è strutturato. Dovrebbe essere simile all'immagine seguente.

    ![Form iniziale del gioco di abbinamenti](../ide/media/express_tut4step1.png)<br/>*Form iniziale del gioco di abbinamenti*

## <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione

- Per andare al passaggio successivo dell'esercitazione, vedere [Passaggio 2: Aggiungere un oggetto casuale e un elenco di icone](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

- Per tornare all'argomento introduttivo, vedere [Esercitazione 3: Creare un gioco di abbinamenti](../ide/tutorial-3-create-a-matching-game.md).
