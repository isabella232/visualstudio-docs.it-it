---
title: "Guida introduttiva: Panoramica dell'IDE Visual Studio"
description: Informazioni su alcune finestre, menu e altre funzionalità dell'interfaccia utente di Visual Studio ide (Integrated Development Environment).
ms.custom: vs-acquisition
titleSuffix: ''
ms.date: 03/02/2021
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: eb31e62a74b9309d86a02005047fd0c96bb2e1e4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635971"
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

![Pagina iniziale di Visual Studio](media/start-page.png)

Se si chiude la **pagina iniziale** e si vuole visualizzare di nuovo la pagina, è possibile riaprirla dal menu **File.**

![Menu File di Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Finestra iniziale

All'apertura di Visual Studio viene visualizzata la finestra iniziale. La finestra iniziale consente di iniziare a lavorare con il codice più velocemente. Contiene opzioni per clonare o estrarre il codice, aprire un progetto o una soluzione esistente, creare un nuovo progetto o semplicemente aprire una cartella contenente alcuni file di codice.

[![Finestra iniziale in Visual Studio 2019](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

Se è la prima volta che si usa Visual Studio, l'elenco dei progetti recenti sarà vuoto.

Se si lavora con codebase non basate su MSBuild, usare l'opzione **Apri una cartella locale** per aprire il codice in Visual Studio. Per altre informazioni, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](develop-code-in-visual-studio-without-projects-or-solutions.md). Oppure è possibile creare un nuovo progetto o clonarne uno da un provider di origine, ad esempio GitHub o Azure DevOps.

L'opzione **Continua senza codice** apre semplicemente l'ambiente di sviluppo di Visual Studio senza caricare alcun progetto o codice specifico. Si può scegliere questa opzione per accedere a una sessione di [Live Share](/visualstudio/liveshare/) o connettersi a un processo per il debug. È anche possibile premere **ESC** per chiudere la finestra iniziale e aprire l'IDE.

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

Per continuare a esplorare le funzionalità di Visual Studio si procederà a creare un nuovo progetto.

::: moniker range="vs-2017"

1. Nella casella di ricerca sotto **Nuovo progetto** della **Pagina iniziale** digitare **console** per filtrare l'elenco dei tipi di progetto includendo solo quelli che contengono "console" nel nome.

   ![Cercare nei modelli di progetto nella Pagina iniziale di Visual Studio](media/start-page-search-templates.png)

   Visual Studio mette a disposizione diversi tipi di modelli di progetto che consentono di iniziare a scrivere codice rapidamente. Scegliere un modello di progetto **App console (.NET Core)** C#. In alternativa, gli sviluppatori che usano Visual Basic, C++, Javascript o altri linguaggi possono creare liberamente un progetto in uno di questi linguaggi. L'interfaccia utente è simile per tutti i linguaggi di programmazione.

1. Nella finestra di dialogo **Nuovo progetto** visualizzata accettare il nome di progetto predefinito e scegliere **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Nella finestra iniziale scegliere **Crea un nuovo progetto.**

    :::image type="content" source="../get-started/media/vs-2019/start-window-create-new-project.png" alt-text="Screenshot della finestra &quot;Crea un nuovo progetto&quot; in Visual Studio 2019.":::

   Viene visualizzata la finestra **Crea un nuovo progetto**, che mostra diversi *modelli* di progetto. Un modello contiene i file e le impostazioni di base necessari per un determinato tipo di progetto.

   Nella finestra è possibile cercare, filtrare e selezionare un modello di progetto. La finestra include anche un elenco dei modelli di progetto usati di recente.

1. Nella casella di ricerca in alto digitare **console** per filtrare l'elenco dei tipi di progetto includendo solo quelli che contengono "console" nel nome. Perfezionare ulteriormente i risultati della ricerca selezionando **C#** (o un altro linguaggio di propria scelta) **dall'elenco a** discesa Tutti i linguaggi.

    :::image type="content" source="media/vs-2019/create-new-project.png" alt-text="Screenshot della finestra &quot;Crea un nuovo progetto&quot; Visual Studio 2019, in cui si seleziona il modello desiderato.":::

1. Se è stato selezionato C#, Visual Basic o F# come linguaggio, selezionare il modello Applicazione **console** e quindi scegliere **Avanti.** Se è stato selezionato un linguaggio diverso, selezionare qualsiasi modello. L'interfaccia utente è simile per tutti i linguaggi di programmazione.

1. Nella finestra **Configura il nuovo progetto** accettare il nome e il percorso predefiniti del progetto e quindi scegliere **Avanti.**

    :::image type="content" source="media/vs-2019/configure-new-project-console.png" alt-text="Screenshot della finestra &quot;Configura un nuovo progetto&quot; in Visual Studio 2019, in cui si immette il nome del progetto.":::

1. Nella finestra **Informazioni aggiuntive** verificare che **.NET Core 3.1** sia visualizzato nel menu a discesa **Framework** di destinazione e quindi fare clic su **Crea.**

    :::image type="content" source="../get-started/media/vs-2019/create-project-additional-info.png" alt-text="Screenshot della finestra &quot;Informazioni aggiuntive&quot; in Visual Studio 2019, in cui si seleziona la versione di .NET Core Framework desiderata.":::

::: moniker-end

   Il progetto viene creato e nella finestra **Editor** si apre un file denominato *Program.cs*. L'**Editor** mostra il contenuto dei file ed è la posizione in cui si esegue la maggior parte delle operazioni di scrittura del codice in Visual Studio.

   ![Editor di Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Esplora soluzioni

**Esplora soluzioni**, generalmente sul lato destro di Visual Studio, mostra una rappresentazione grafica della gerarchia di file e cartelle nella cartella del progetto, della soluzione o del codice. È possibile esplorare la gerarchia e passare a un file in **Esplora soluzioni**.

![Esplora soluzioni di Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menu

La barra dei menu nella parte superiore di Visual Studio raggruppa i comandi in categorie. Ad esempio, il menu **Progetto** contiene i comandi correlati al progetto in uso. Dal menu **Strumenti** è possibile personalizzare Visual Studio selezionando **Opzioni** oppure aggiungere funzionalità all'installazione selezionando **Ottieni strumenti e funzionalità**.

::: moniker range="vs-2017"

![Barra dei menu di Visual Studio 2017](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Barra dei menu di Visual Studio 2019](media/vs-2019/menu-bar.png)

::: moniker-end

## <a name="error-list"></a>Elenco errori

Aprire la finestra **Elenco errori** scegliendo **Elenco errori** dal menu **Visualizza**.

**L'Elenco** errori mostra errori, avvisi e messaggi relativi allo stato corrente del codice. Se il file o il progetto in uso contiene errori, ad esempio una parentesi o un punto e virgola mancante, verranno elencati in questa posizione.

![Elenco errori in Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Output (finestra)

Nella finestra **Output** vengono visualizzati i messaggi di output generati dalla compilazione del progetto e dal provider di controllo del codice sorgente.

Ora si procederà alla compilazione del progetto per esaminare alcuni elementi di output della compilazione. Scegliere **Compila** soluzione dal menu **Compila**. La **finestra Output** ottiene automaticamente lo stato attivo e visualizza un messaggio di compilazione riuscita.

![Finestra Output di Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Casella di ricerca

La casella di ricerca è un modo rapido e semplice per eseguire pressoché qualsiasi operazione in Visual Studio. È possibile immettere testo correlato all'operazione che si vuole eseguire e verrà visualizzato un elenco di opzioni pertinenti. Ad esempio, si supponga di voler aumentare il livello di dettaglio dell'output di compilazione per visualizzare più informazioni sulle operazioni eseguite esattamente dalla compilazione. Ecco come si può fare:

::: moniker range="vs-2017"

1. Individuare la casella di ricerca **Avvio veloce** in alto a destra nell'IDE. In alternativa, premere **CTRL** + **Q** per accedervi.

2. Digitare **livello di dettaglio** nella casella di ricerca. Nei risultati visualizzati scegliere **Progetti e soluzioni -> Compila ed Esegui** nella categoria **Opzioni**.

   ![Casella di ricerca di Avvio veloce in Visual Studio 2017](media/quickstart-IDE-quick-launch.png)

   Si apre la pagina delle opzioni **Compila ed esegui** della finestra di dialogo **Opzioni**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Premere **CTRL** + **Q** per attivare la casella di ricerca nella parte superiore dell'IDE.

2. Digitare **livello di dettaglio** nella casella di ricerca. Nei risultati visualizzati scegliere **Modifica livello di dettaglio di MSBuild**.

   ![Casella di ricerca in Visual Studio 2019](media/vs-2019/quick-launch-verbosity.png)

   Si apre la pagina delle opzioni **Compila ed esegui** della finestra di dialogo **Opzioni**.

::: moniker-end

3. In **Livello di dettaglio output in compilazione progetto MSBuild** scegliere **Normale** e quindi fare clic su **OK**.

4. Compilare di nuovo il progetto facendo clic con il pulsante destro del mouse sul progetto **ConsoleApp1** in **Esplora soluzioni** e scegliendo **Ricompila** dal menu di scelta rapida.

   Questa volta la **finestra Output** mostra una registrazione più dettagliata dal processo di compilazione, inclusi i file in cui sono stati copiati.

   ![Output di compilazione dettagliato in Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Menu Invia commenti e suggerimenti

Se si verificano problemi durante l'uso di Visual Studio o se si hanno suggerimenti su come migliorare il prodotto, è possibile usare il menu **Invia commenti e suggerimenti** nella parte superiore della finestra di Visual Studio.

::: moniker range="vs-2017"

![Menu commenti e suggerimenti in Visual Studio 2017](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Menu commenti e suggerimenti in Visual Studio 2019](media/vs-2019/send-feedback-menu.png)

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
