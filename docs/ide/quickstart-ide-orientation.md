---
title: "Guida introduttiva: Panoramica dell'IDE Visual Studio"
description: Informazioni su alcune finestre, menu e altre funzionalità dell'interfaccia utente di Visual Studio ide (Integrated Development Environment).
ms.custom: vs-acquisition
titleSuffix: ''
ms.date: 09/14/2021
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 2ff4270fb819c010a31e4dce9e3e3376d41cf205
ms.sourcegitcommit: 59613afd06a8f184efab8e108410066824a2b712
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/18/2021
ms.locfileid: "127920464"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Guida introduttiva: Presentazione dell'IDE di Visual Studio

In questa introduzione della durata di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio verranno presentati alcuni menu, finestre e altre funzionalità dell'interfaccia utente.

::: moniker range="vs-2017"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Pagina iniziale

Il primo elemento visualizzato dopo l'apertura di Visual Studio è molto probabilmente la **Pagina iniziale**. La **pagina iniziale** è progettata come "hub" per consentire di trovare più rapidamente i comandi e i file di progetto necessari. Nella sezione **Recenti** sono visualizzati i progetti e le cartelle usati di recente. In **Nuovo progetto** è possibile fare clic su un collegamento per visualizzare la finestra di dialogo **Nuovo progetto** o in **Apri** è possibile aprire un progetto o una cartella di codice esistente. Sulla destra è visualizzato un feed di notizie aggiornate per sviluppatori.

![Screenshot della pagina iniziale in Visual Studio 2017.](media/start-page.png)

Se si chiude la **pagina iniziale** e si vuole visualizzare di nuovo la pagina, è possibile riaprirla dal menu **File.**

![Screenshot del menu File in Visual Studio 2017.](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range="vs-2019"

## <a name="start-window"></a>Finestra iniziale

All'apertura di Visual Studio viene visualizzata la finestra iniziale. La finestra iniziale consente di iniziare a lavorare con il codice più velocemente. Contiene opzioni per clonare o estrarre il codice, aprire un progetto o una soluzione esistente, creare un nuovo progetto o semplicemente aprire una cartella contenente alcuni file di codice.

[![Screenshot della finestra Iniziale in Visual Studio 2019.](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

Se è la prima volta che si usa Visual Studio, l'elenco dei progetti recenti sarà vuoto.

Se si lavora con codebase non basate su MSBuild, usare l'opzione **Apri una cartella locale** per aprire il codice in Visual Studio. Per altre informazioni, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](develop-code-in-visual-studio-without-projects-or-solutions.md). Oppure è possibile creare un nuovo progetto o clonarne uno da un provider di origine, ad esempio GitHub o Azure DevOps.

L'opzione **Continua senza codice** apre semplicemente l'ambiente di sviluppo di Visual Studio senza caricare alcun progetto o codice specifico. Si può scegliere questa opzione per accedere a una sessione di [Live Share](/visualstudio/liveshare/) o connettersi a un processo per il debug. È anche possibile premere **ESC** per chiudere la finestra iniziale e aprire l'IDE.

::: moniker-end

::: moniker range=">=vs-2022"

## <a name="start-window"></a>Finestra iniziale

All'apertura di Visual Studio viene visualizzata la finestra iniziale. La finestra iniziale consente di iniziare a lavorare con il codice più velocemente. Sono disponibili opzioni per clonare o estrarre il codice, aprire un progetto o una soluzione esistente, creare un nuovo progetto o semplicemente aprire una cartella contenente alcuni file di codice.

:::image type="content" source="media/vs-2022/quickstart-start-window-labeled.png" border="true" alt-text="Screenshot con annotazioni che mostra la finestra iniziale in Visual Studio 2022." lightbox="media/vs-2022/quickstart-start-window-labeled.png":::

Se è la prima volta che si usa Visual Studio, l'elenco dei progetti recenti sarà vuoto.

Se si usano codebase che non usano MSBuild, si userà  l'opzione Apri una cartella locale per aprire il codice in Visual Studio. Per altre informazioni, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](develop-code-in-visual-studio-without-projects-or-solutions.md). Oppure è possibile creare un nuovo progetto o clonarne uno da un provider di origine, ad esempio GitHub o Azure DevOps.

**L'opzione Continua senza** codice apre l'Visual Studio di sviluppo senza alcun progetto o codice specifico caricato. Si può scegliere questa opzione per accedere a una sessione di [Live Share](/visualstudio/liveshare/) o connettersi a un processo per il debug. È anche possibile premere **ESC** per chiudere la finestra iniziale e aprire l'IDE.

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

Per continuare a esplorare le funzionalità di Visual Studio si procederà a creare un nuovo progetto.

::: moniker range="vs-2017"

1. Nella casella di ricerca sotto **Nuovo progetto** della **Pagina iniziale** digitare **console** per filtrare l'elenco dei tipi di progetto includendo solo quelli che contengono "console" nel nome.

   ![Screenshot che mostra un elenco di modelli di progetto nella pagina iniziale Visual Studio 2017.](media/start-page-search-templates.png)

   Visual Studio mette a disposizione diversi tipi di modelli di progetto che consentono di iniziare a scrivere codice rapidamente. Scegliere un modello di progetto **App console (.NET Core)** C#. In alternativa, gli sviluppatori di Visual Basic, C++, JavaScript o altri linguaggi possono creare un progetto in uno di questi linguaggi. L'interfaccia utente è simile per tutti i linguaggi di programmazione.

1. Nella finestra di dialogo **Nuovo progetto** visualizzata accettare il nome di progetto predefinito e scegliere **OK**.

Il progetto viene creato e nella finestra **Editor** si apre un file denominato *Program.cs*. L'**Editor** mostra il contenuto dei file ed è la posizione in cui si esegue la maggior parte delle operazioni di scrittura del codice in Visual Studio.

![Screenshot che mostra l'editor in Visual Studio 2017.](media/editor.png)

::: moniker-end

::: moniker range="vs-2019"

1. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

    :::image type="content" source="../get-started/media/vs-2019/start-window-create-new-project.png" alt-text="Screenshot della finestra &quot;Crea un nuovo progetto&quot; in Visual Studio 2019.":::

   Viene visualizzata la finestra **Crea un nuovo progetto**, che mostra diversi *modelli* di progetto. Un modello contiene i file e le impostazioni di base necessari per un determinato tipo di progetto.

   Nella finestra è possibile cercare, filtrare e selezionare un modello di progetto. La finestra include anche un elenco dei modelli di progetto usati di recente.

1. Nella casella di ricerca in alto digitare **console** per filtrare l'elenco dei tipi di progetto includendo solo quelli che contengono "console" nel nome. Perfezionare ulteriormente i risultati della ricerca selezionando **C#** (o un altro linguaggio di propria scelta) **dall'elenco a** discesa Tutti i linguaggi.

    :::image type="content" source="media/vs-2019/create-new-project.png" alt-text="Screenshot della finestra &quot;Crea un nuovo progetto&quot; Visual Studio 2019, in cui è possibile selezionare il modello desiderato.":::

1. Se è stato selezionato C#, Visual Basic o F# come linguaggio, selezionare il modello Applicazione **console** e quindi scegliere **Avanti.** Se è stato selezionato un linguaggio diverso, selezionare qualsiasi modello. L'interfaccia utente è simile per tutti i linguaggi di programmazione.

1. Nella finestra **Configura il nuovo progetto** accettare il nome e il percorso predefiniti del progetto e quindi scegliere **Avanti.**

    :::image type="content" source="media/vs-2019/configure-new-project-console.png" alt-text="Screenshot della finestra &quot;Configura un nuovo progetto&quot; in Visual Studio 2019, in cui si immette il nome del progetto.":::

1. Nella finestra **Informazioni aggiuntive** verificare che **.NET Core 3.1** sia visualizzato nel menu a discesa **Framework** di destinazione e quindi fare clic su **Crea.**

    :::image type="content" source="../get-started/media/vs-2019/create-project-additional-info.png" alt-text="Screenshot della finestra &quot;Informazioni aggiuntive&quot; in Visual Studio 2019, in cui si seleziona la versione di .NET Core Framework desiderata.":::

Il progetto viene creato e nella finestra **Editor** si apre un file denominato *Program.cs*. L'**Editor** mostra il contenuto dei file ed è la posizione in cui si esegue la maggior parte delle operazioni di scrittura del codice in Visual Studio.

![Screenshot che mostra la finestra Editor in Visual Studio 2019.](media/editor.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

    :::image type="content" source="media/vs-2022/start-window-create-new-project.png" alt-text="Screenshot della finestra &quot;Crea un nuovo progetto&quot; in Visual Studio 2022.":::

   Viene visualizzata la finestra **Crea un nuovo progetto**, che mostra diversi *modelli* di progetto. Un modello contiene i file e le impostazioni di base necessari per un determinato tipo di progetto.

   Nella finestra è possibile cercare, filtrare e selezionare un modello di progetto. La **finestra Crea un nuovo progetto** mostra anche un elenco dei modelli di progetto usati di recente.

1. Nella casella di ricerca in alto digitare *console* per filtrare l'elenco dei tipi di progetto includendo solo quelli che contengono "console" nel nome. Perfezionare ulteriormente i risultati della ricerca selezionando **C#** (o un altro linguaggio di propria scelta) dall'elenco a discesa **Tutti i** linguaggi.

    :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Screenshot della finestra &quot;Crea un nuovo progetto&quot; in Visual Studio 2022, in cui è possibile selezionare il modello desiderato.":::

1. Se è stato selezionato C#, Visual Basic o F# come linguaggio, selezionare il modello Applicazione **console** e quindi scegliere **Avanti.** Se è stata selezionata una lingua diversa, è sufficiente selezionare qualsiasi modello.

1. Nella finestra **Configura il nuovo progetto** accettare il nome e il percorso predefiniti del progetto e quindi scegliere **Avanti.**

    :::image type="content" source="media/vs-2022/quickstart-configure-new-project-console.png" alt-text="Screenshot della finestra &quot;Configura un nuovo progetto&quot; in Visual Studio 2022, in cui si immette il nome del progetto.":::

1. Nella finestra **Informazioni aggiuntive** verificare che **.NET 6.0 (anteprima)** sia visualizzato nel menu a discesa **Framework** e quindi scegliere **Crea.**

    :::image type="content" source="media/vs-2022/create-project-additional-info.png" alt-text="Screenshot della finestra &quot;Informazioni aggiuntive&quot; in Visual Studio 2022, in cui si seleziona la versione di .NET desiderata.":::

1. Viene creato il progetto. Selezionare il file di *codice Program.cs* **nella finestra Esplora soluzioni,** che in genere si trova sul lato destro del Visual Studio.

    :::image type="content" source="media/vs-2022/quickstart-opened-new-project.png" alt-text="Screenshot del nuovo progetto console C# in Visual Studio 2022.":::

Il file *Program.cs* viene aperto nella **finestra Editor.** L'**Editor** mostra il contenuto dei file ed è la posizione in cui si esegue la maggior parte delle operazioni di scrittura del codice in Visual Studio.

:::image type="content" source="media/vs-2022/editor.png" alt-text="Screenshot dell'editor in Visual Studio 2022.":::

::: moniker-end

## <a name="solution-explorer"></a>Esplora soluzioni

::: moniker range="<=vs-2019"

**Esplora soluzioni**, generalmente sul lato destro di Visual Studio, mostra una rappresentazione grafica della gerarchia di file e cartelle nella cartella del progetto, della soluzione o del codice. È possibile esplorare la gerarchia e passare a un file in **Esplora soluzioni**.

![Screenshot che mostra la Esplora soluzioni in Visual Studio.](media/quickstart-IDE-solution-explorer.png)

::: moniker-end

::: moniker range=">=vs-2022"

**Esplora soluzioni** mostra una rappresentazione grafica della gerarchia di file e cartelle nel progetto, nella soluzione o nella cartella del codice. È possibile esplorare la gerarchia e selezionare un file per aprirlo **nell'editor**.

:::image type="content" source="media/vs-2022/quickstart-ide-solution-explorer.png" alt-text="Screenshot della Esplora soluzioni in Visual Studio 2022.":::

::: moniker-end

## <a name="menus"></a>Menu

La barra dei menu nella parte superiore di Visual Studio raggruppa i comandi in categorie. Ad esempio, il menu **Progetto** contiene i comandi correlati al progetto in uso. Dal menu **Strumenti** è possibile personalizzare Visual Studio selezionando **Opzioni** oppure aggiungere funzionalità all'installazione selezionando **Ottieni strumenti e funzionalità**.

::: moniker range="vs-2017"

![Screenshot che mostra la barra dei menu in Visual Studio 2017.](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range="vs-2019"

![Screenshot che mostra la barra dei menu in Visual Studio 2019.](media/vs-2019/menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/menu-bar.png" alt-text="Screenshot della barra dei menu in Visual Studio 2022.":::

::: moniker-end

## <a name="error-list"></a>Elenco errori

**L'Elenco** errori mostra errori, avvisi e messaggi sullo stato corrente del codice. Se nel file o in un punto qualsiasi del progetto sono presenti errori, ad esempio una parentesi graffa o un punto e virgola mancanti, questi vengono elencati qui.

Per aprire la **finestra Elenco** errori, scegliere **il** menu Visualizza e quindi selezionare **Elenco errori**.

::: moniker range="<=vs-2019"

:::image type="content" source="media/quickstart-IDE-error-list.png" alt-text="Screenshot dell'elenco errori in Visual Studio 2019.":::

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/quickstart-ide-error-list.png" alt-text="Screenshot dell'elenco errori in Visual Studio 2022.":::

::: moniker-end

## <a name="output-window"></a>Output (finestra)

Nella finestra **Output** vengono visualizzati i messaggi di output generati dalla compilazione del progetto e dal provider di controllo del codice sorgente.

Ora si procederà alla compilazione del progetto per esaminare alcuni elementi di output della compilazione. Scegliere **Compila** soluzione dal menu **Compila**. La **finestra Output** ottiene automaticamente lo stato attivo e visualizza un messaggio di compilazione riuscita.

::: moniker range="<=vs-2019"

![Screenshot della finestra Output in Visual Studio.](media/build-output-minimal.png)

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/quickstart-build-output-minimal.png" alt-text="Screenshot della finestra Output in Visual Studio 2022.":::

::: moniker-end

## <a name="search-box"></a>Casella di ricerca

La casella di ricerca è un modo semplice e rapido per trovare qualsiasi elemento Visual Studio. È possibile immettere testo correlato alle attività da eseguire e verrà visualizzato un elenco di opzioni rilevanti per il testo. Si supponga, ad esempio, di voler aumentare il livello di dettaglio dell'output di compilazione per visualizzare altri dettagli sulle attività della compilazione. Ecco come si può fare:

::: moniker range="vs-2017"

1. Individuare la casella di ricerca **Avvio veloce** in alto a destra nell'IDE. In alternativa, premere **CTRL** + **Q** per accedervi.

1. Digitare **livello di dettaglio** nella casella di ricerca. Nei risultati visualizzati scegliere **Progetti e soluzioni -> Compila ed Esegui** nella categoria **Opzioni**.

   ![Screenshot della casella di ricerca Avvio veloce in Visual Studio 2017.](media/quickstart-IDE-quick-launch.png)

   Si apre la pagina delle opzioni **Compila ed esegui** della finestra di dialogo **Opzioni**.

1. In **Livello di dettaglio output in compilazione progetto MSBuild** scegliere **Normale** e quindi fare clic su **OK**.

1. Compilare di nuovo il progetto facendo clic con il pulsante destro del mouse sul progetto **ConsoleApp1** in **Esplora soluzioni** e scegliendo **Ricompila** dal menu di scelta rapida.

   Questa volta la **finestra Output** mostra una registrazione più dettagliata dal processo di compilazione, inclusi i file in cui sono stati copiati.

   ![Screenshot di un log di compilazione più dettagliato all'interno della finestra Output Visual Studio 2017.](media/build-output-verbose.png)

::: moniker-end

::: moniker range="vs-2019"

1. Premere **CTRL** + **Q** per attivare la casella di ricerca nella parte superiore dell'IDE.

1. Digitare **livello di dettaglio** nella casella di ricerca. Nei risultati visualizzati scegliere **Modifica livello di dettaglio di MSBuild**.

   ![Screenshot della casella di ricerca in Visual Studio 2019.](media/vs-2019/quick-launch-verbosity.png)

   Si apre la pagina delle opzioni **Compila ed esegui** della finestra di dialogo **Opzioni**.

1. In **Livello di dettaglio output in compilazione progetto MSBuild** scegliere **Normale** e quindi fare clic su **OK**.

1. Compilare di nuovo il progetto facendo clic con il pulsante destro del mouse sul progetto **ConsoleApp1** in **Esplora soluzioni** e scegliendo **Ricompila** dal menu di scelta rapida.

   Questa volta la **finestra Output** mostra una registrazione più dettagliata dal processo di compilazione, inclusi i file in cui sono stati copiati.

   ![Screenshot di un log di compilazione più dettagliato all'interno della finestra Output Visual Studio 2019.](media/build-output-verbose.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Premere **CTRL** + **Q** per attivare la casella di ricerca nella parte superiore dell'IDE.

1. Digitare *livello di dettaglio* nella casella di ricerca. Nei risultati visualizzati scegliere **Modifica livello di dettaglio di MSBuild**.

   :::image type="content" source="media/vs-2022/quickstart-search-verbosity.png" alt-text="Screenshot della casella di ricerca in Visual Studio 2022.":::

   Si apre la pagina delle opzioni **Compila ed esegui** della finestra di dialogo **Opzioni**.

1. In **MSBuild livello di dettaglio dell'output di** compilazione del progetto scegliere **Normale** e quindi **scegliere OK.**

1. Compilare di nuovo il progetto facendo clic con il pulsante destro del mouse sul progetto **ConsoleApp1** in **Esplora soluzioni** e scegliendo **Ricompila** dal menu di scelta rapida.

   Questa volta la **finestra Output** mostra una registrazione più dettagliata dal processo di compilazione, inclusi i file in cui sono stati copiati.

   :::image type="content" source="media/vs-2022/quickstart-build-output-verbose.png" alt-text="Screenshot di un log di compilazione più dettagliato all'interno della finestra Output Visual Studio 2022.":::

::: moniker-end

## <a name="send-feedback-menu"></a>Menu Invia commenti e suggerimenti

::: moniker range="vs-2017"

Se si verificano problemi durante l'uso di Visual Studio o se si hanno suggerimenti su come migliorare il prodotto, è possibile usare il menu **Invia commenti e suggerimenti** nella parte superiore della finestra di Visual Studio.

![Screenshot del menu Invia commenti e suggerimenti in Visual Studio 2017.](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range="vs-2019"

Se si verificano problemi durante l'uso di Visual Studio o se si hanno suggerimenti su come migliorare il prodotto, è possibile usare il menu **Invia commenti e suggerimenti** nella parte superiore della finestra di Visual Studio.

![Screenshot del menu Invia commenti e suggerimenti in Visual Studio 2019.](media/vs-2019/send-feedback-menu.png)

::: moniker-end

::: moniker range=">=vs-2022"

Se si verificano problemi durante l'uso di Visual Studio o se si hanno suggerimenti su come migliorare il prodotto, è possibile inviare commenti e suggerimenti. A tale scopo, scegliere il pulsante **Invia commenti** e suggerimenti nell'angolo superiore destro dell'IDE e usare una delle opzioni di feedback nel menu Invia **commenti e** suggerimenti.

:::image type="content" source="media/vs-2022/quickstart-ide-send-feedback.png" alt-text="Screenshot del pulsante Invia commenti e suggerimenti e del menu in Visual Studio 2022.":::

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

Sono state presentate solo alcune delle funzionalità di Visual Studio per iniziare ad acquisire familiarità con l'interfaccia utente. Per esplorare ulteriormente:

> [!div class="nextstepaction"]
> [Informazioni sull'editor del codice](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [Informazioni su progetti e soluzioni](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Vedi anche

- [Panoramica dell'IDE di Visual Studio](../get-started/visual-studio-ide.md)
- [Altre funzionalità di Visual Studio](../ide/advanced-feature-overview.md)
- [Modificare i colori del tema e del carattere](../ide/quickstart-personalize-the-ide.md)
