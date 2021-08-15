---
title: Presentazione dell'IDE di Visual Studio
description: Informazioni sull'Visual Studio di sviluppo integrato (IDE), incluse le finestre, i menu e altre funzionalità dell'interfaccia utente usate più di frequente.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/05/2019
ms.topic: quickstart
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
ms.workload:
- multiple
ms.openlocfilehash: 0801f2748a94aac09faa56148340796baf19e30e99706ea5faf007d13aef9401
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121398934"
---
# <a name="first-look-at-the-visual-studio-ide"></a>Presentazione dell'IDE di Visual Studio

In questa introduzione della durata di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio verranno presentati alcuni menu, finestre e altre funzionalità dell'interfaccia utente.

::: moniker range="vs-2017"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Finestra iniziale

All'avvio di Visual Studio viene visualizzata la finestra iniziale. La finestra iniziale consente di iniziare a lavorare con il codice più velocemente. Contiene opzioni per chiudere o estrarre il codice, aprire un progetto o una soluzione esistente, creare un nuovo progetto o semplicemente aprire una cartella contenente alcuni file di codice.

[![Finestra iniziale in Visual Studio 2019](media/vs-2019/start-window.png)](media/vs-2019/start-window.png)

Se è la prima volta che si usa Visual Studio, l'elenco dei progetti recenti sarà vuoto.

Se si lavora con codebase non basate su MSBuild, usare l'opzione **Apri una cartella locale** per aprire il codice in Visual Studio. Per altre informazioni, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](develop-javascript-code-without-solutions-projects.md). Oppure è possibile creare un nuovo progetto o clonarne uno da un provider di origine, ad esempio GitHub o Azure DevOps.

L'opzione **Continua senza codice** apre semplicemente l'ambiente di sviluppo di Visual Studio senza caricare alcun progetto o codice specifico. Si può scegliere questa opzione per accedere a una sessione di [Live Share](/visualstudio/liveshare/) o connettersi a un processo per il debug. È anche possibile premere **ESC** per chiudere la finestra iniziale e aprire l'IDE.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Pagina iniziale

La prima cosa che verrà visualizzata dopo l'avvio Visual Studio è molto probabilmente la **pagina iniziale**. La **pagina iniziale** è progettata come "hub" per consentire di trovare più rapidamente i comandi e i file di progetto necessari. Nella sezione **Recenti** sono visualizzati i progetti e le cartelle usati di recente. In **Nuovo progetto** è possibile fare clic su un collegamento per visualizzare la finestra di dialogo **Nuovo progetto** o in **Apri** è possibile aprire un progetto o una cartella di codice esistente. Sulla destra è visualizzato un feed di notizie aggiornate per sviluppatori.

![Pagina iniziale di Visual Studio](media/start-page.png)

Se si chiude la **pagina iniziale** e si vuole visualizzare di nuovo la pagina, è possibile riaprirla dal menu **File.**

![Menu File di Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

Per continuare a esplorare le funzionalità di Visual Studio si procederà a creare un nuovo progetto.

::: moniker range=">=vs-2019"

1. Nella Finestra iniziale selezionare **Crea un nuovo progetto** e quindi nella casella di ricerca digitare **javascript** per filtrare l'elenco dei tipi di progetto in modo da visualizzare soltanto quelli che contengono "javascript" nel nome o tipo di linguaggio.

   Visual Studio mette a disposizione diversi tipi di modelli di progetto che consentono di iniziare a scrivere codice rapidamente. In alternativa, gli sviluppatori di TypeScript possono creare un progetto nel linguaggio TypeScript. L'interfaccia utente è simile per tutti i linguaggi di programmazione.

   ![Cercare modelli di progetto nella finestra iniziale di Visual Studio](media/vs-2019/create-new-project.png)

1. Scegliere un modello di progetto **Applicazione Web Node.js vuota** e fare clic su **Avanti**.

1. Nella finestra di dialogo **Configura il nuovo progetto** visualizzata accettare il nome di progetto predefinito e scegliere **Crea**.

::: moniker-end

::: moniker range="vs-2017"

1. Nella **Pagina iniziale** nella casella di ricerca in **Nuovo progetto** digitare **javascript** per applicare un filtro all'elenco dei tipi di progetto in modo da visualizzare soltanto quelli che contengono "javascript" nel nome o nel tipo di linguaggio.

   ![Cercare nei modelli di progetto nella Pagina iniziale di Visual Studio](media/start-page-search-templates.png)

   Visual Studio mette a disposizione diversi tipi di modelli di progetto che consentono di iniziare a scrivere codice rapidamente. Scegliere un modello di progetto **Applicazione Web Node.js vuota**. In alternativa, gli sviluppatori di TypeScript possono creare un progetto nel linguaggio TypeScript. L'interfaccia utente è simile per tutti i linguaggi di programmazione.

1. Nella finestra di dialogo **Nuovo progetto** visualizzata accettare il nome di progetto predefinito e scegliere **OK**.
::: moniker-end

   Il progetto viene creato e viene aperto *server.js* file denominato nella **finestra Editor.** **L'editor** mostra il contenuto dei file ed è la posizione in cui si eservirà la maggior parte del lavoro di scrittura del codice Visual Studio.

   ![Editor di Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Esplora soluzioni

**Esplora soluzioni**, generalmente sul lato destro di Visual Studio, mostra una rappresentazione grafica della gerarchia di file e cartelle nella cartella del progetto, della soluzione o del codice. È possibile esplorare la gerarchia e passare a un file in **Esplora soluzioni**.

![Esplora soluzioni di Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menu

La barra dei menu nella parte superiore di Visual Studio raggruppa i comandi in categorie. Ad esempio, il menu **Progetto** contiene i comandi correlati al progetto in uso. Dal menu **Strumenti** è possibile personalizzare Visual Studio selezionando **Opzioni** oppure aggiungere funzionalità all'installazione selezionando **Ottieni strumenti e funzionalità**.

![Barra dei menu di Visual Studio](media/quickstart-IDE-menu-bar.png)

Aprire la finestra **Elenco errori** scegliendo il menu **Visualizza** e quindi Elenco **errori**.

## <a name="error-list"></a>Elenco errori

**L'Elenco** errori mostra errori, avvisi e messaggi relativi allo stato corrente del codice. Se il file o il progetto in uso contiene errori, ad esempio una parentesi o un punto e virgola mancante, verranno elencati in questa posizione.

![Elenco errori in Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Output (finestra)

Nella finestra **Output** vengono visualizzati i messaggi di output generati dalla compilazione del progetto e dal provider di controllo del codice sorgente.

Ora si procederà alla compilazione del progetto per esaminare alcuni elementi di output della compilazione. Scegliere **Compila** soluzione dal menu **Compila**. La **finestra Output** ottiene automaticamente lo stato attivo e visualizza un messaggio di compilazione riuscita.

![Finestra Output di Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Casella di ricerca

La casella di ricerca è un modo rapido e semplice per eseguire pressoché qualsiasi operazione in Visual Studio. È possibile immettere testo correlato all'operazione che si vuole eseguire e verrà visualizzato un elenco di opzioni pertinenti. Ad esempio, si supponga di voler aumentare il livello di dettaglio dell'output di compilazione per visualizzare più informazioni sulle operazioni eseguite esattamente dalla compilazione. Ecco come si può fare:

1. Digitare **livello di dettaglio** nella casella di ricerca. Nei risultati visualizzati scegliere **Progetti e soluzioni -> Compila ed Esegui** nella categoria **Opzioni**.

   ![Casella di ricerca in Visual Studio](media/quickstart-IDE-quick-launch.png)

   Si apre la pagina delle opzioni **Compila ed esegui** della finestra di dialogo **Opzioni**.

1. In **Livello di dettaglio output in compilazione progetto MSBuild** scegliere **Normale** e quindi fare clic su **OK**.

1. Compilare di nuovo il progetto facendo clic con il pulsante destro del mouse sul progetto **NodejsWebApp1** in **Esplora soluzioni** e scegliendo **Ricompila** dal menu di scelta rapida.

   Questa volta la **finestra Output** mostra una registrazione più dettagliata dal processo di compilazione, inclusi i file in cui sono stati copiati.

   ![Output di compilazione dettagliato in Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Menu Invia commenti e suggerimenti

Se si verificano problemi durante l'uso di Visual Studio o se si hanno suggerimenti su come migliorare il prodotto, è possibile usare il menu **Invia commenti e suggerimenti** nella parte superiore della finestra di Visual Studio.

![Inviare commenti e suggerimenti in Visual Studio](../ide/media/quickstart-ide-send-feedback.png)

## <a name="next-steps"></a>Passaggi successivi

Sono state presentate solo alcune delle funzionalità di Visual Studio per iniziare ad acquisire familiarità con l'interfaccia utente. Per esplorare ulteriormente:

> [!div class="nextstepaction"]
> [Informazioni sull'editor del codice](write-and-edit-code.md)

> [!div class="nextstepaction"]
> [Informazioni su progetti e soluzioni](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Vedi anche

- [Panoramica dell'IDE di Visual Studio](../get-started/visual-studio-ide.md)
- [Altre funzionalità di Visual Studio 2017](../ide/advanced-feature-overview.md)
- [Modificare i colori del tema e del carattere](../ide/quickstart-personalize-the-ide.md)
