---
title: 'Guida introduttiva: Creare la prima app Vue.js'
description: In questa Guida introduttiva viene spiegato come creare un'app Vue.js in Visual Studio usando Node.js Tools for Visual Studio
ms.custom: seodec18
ms.date: 09/24/2018
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: ac09fa17ea550df127660a56a04d315f8f1a788f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55911169"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Guida introduttiva: Usare Visual Studio per creare la prima app Vue.js

In questa introduzione di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio si creerà ed eseguirà una semplice applicazione Web Vue.js. Se Visual Studio 2017 non è ancora installato, accedere alla pagina [Download di Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) per installarlo gratuitamente.

> [!IMPORTANT]
> Questo articolo richiede il modello Vue.js disponibile a partire da Visual Studio 2017 versione 15.8.

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa si crea un progetto di applicazione Web Vue.js.

1. Se il runtime di Node.js non è già installato, installare la versione LTS dal sito Web [Node.js](https://nodejs.org/en/download/).

    In generale, Visual Studio rileva automaticamente il runtime di Node.js installato. Se non viene rilevato un runtime installato, è possibile usare la pagina delle proprietà per configurare il progetto in modo che faccia riferimento al runtime installato (dopo aver creato un progetto, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Proprietà**).

1. Aprire Visual Studio 2017.

1. Sulla barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.

1. Nella finestra di dialogo **Nuovo progetto**, in corrispondenza di **JavaScript** > **Node.js** oppure di **TypeScript** > **Node.js**, scegliere **Applicazione Web Vue.js di base**. Immettere un nome di progetto e fare clic su **OK**.

     ![Modello Vue.js](../javascript/media/vuejs-template.png)

    Visual Studio crea il nuovo progetto. Il nuovo progetto viene aperto in Esplora soluzioni (riquadro a destra).

     Se il modello di progetto **Applicazione Web Vue.js di base** non viene visualizzato, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Node.js**, quindi scegliere **Modifica**.

     ![Carico di lavoro Node.js nel programma di installazione di Visual Studio](../ide/media/quickstart-nodejs-workload.png)

    Visual Studio crea la nuova soluzione e apre il progetto.

1. Controllare nella finestra Output, riquadro inferiore, lo stato di avanzamento dell'installazione dei pacchetti npm necessari per l'applicazione.

1. In Esplora soluzioni aprire il nodo **npm** e assicurarsi che tutti i pacchetti npm necessari siano installati.

    Se uno o più pacchetti risultano mancanti (icona con il punto esclamativo), fare clic con il pulsante destro del mouse sul nodo **npm** e scegliere **Installa pacchetti npm mancanti**.

## <a name="explore-the-ide"></a>Esplorare l'IDE

1. Osservare **Esplora soluzioni** nel riquadro a destra.

     ![Soluzione Vue.js](../javascript/media/vuejs-solution.png)

   - Il progetto viene visualizzato in grassetto, con il nome assegnato in precedenza nella finestra di dialogo **Nuovo progetto**. Sul disco, questo progetto è rappresentato nella cartella del progetto da un file con estensione *njsproj*.

   - Al primo livello è presente una soluzione che, per impostazione predefinita, ha lo stesso nome del progetto. Una soluzione, rappresentata su disco da un file con estensione *sln*, è un contenitore per uno o più progetti correlati.

   - Il nodo **npm** visualizza tutti i pacchetti npm installati. È possibile fare clic con il pulsante destro del mouse sul nodo npm per cercare e installare pacchetti npm tramite una finestra di dialogo.

2. Se si vuole installare pacchetti npm o eseguire comandi Node.js da un prompt dei comandi, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Apri prompt dei comandi qui**.

## <a name="add-a-vue-file-to-the-project"></a>Aggiungere un file con estensione vue al progetto

1. In Esplora soluzioni fare clic con il pulsante destro del mouse su una cartella, ad esempio la cartella *src/components*, quindi scegliere **Aggiungi** > **Nuovo elemento**.

1. Selezionare **Componente file singoli Vue JavaScript** oppure **Componente file singoli Vue TypeScript**, quindi fare clic su **Aggiungi**.

    Visual Studio aggiunge il nuovo file al progetto.

## <a name="build-the-project"></a>Compilare il progetto

1. (Solo per progetti TypeScript) Da Visual Studio scegliere **Compila** > **Pulisci soluzione**.

1. In seguito, scegliere **Compila** > **Compila soluzione** per compilare il progetto. Controllare i risultati della compilazione nella finestra **Output** e scegliere **Compila** dall'elenco **Mostra output di**.

    Il modello di progetto Vue.js usa lo script npm `build` tramite la configurazione di un evento di post-compilazione. Se si desidera modificare questa impostazione, aprire il file di progetto (*\<projectname\>.njsproj*) da Esplora risorse e individuare la seguente riga di codice:

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>Esecuzione dell'applicazione

1. Premere **Ctrl**+**F5** (o scegliere **Debug > Avvia senza eseguire debug**) per eseguire l'applicazione.

   Nella console un messaggio avvisa che è in corso *l'avvio del server di sviluppo* .

   Quindi, l'app verrà aperta in un browser.

   ![App Vue.js in esecuzione nel browser](../javascript/media/vuejs-running-app.png)

1. Chiudere il Web browser.

La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per iniziare ad apprendere l'uso dell'IDE di Visual Studio con Vue.js. Se si vuole approfondire la conoscenza relativa alle funzionalità, scegliere un'esercitazione nella sezione del sommario relativa alle **esercitazioni**.

## <a name="next-steps"></a>Passaggi successivi

- Completare l'[Esercitazione per Node.js e Express](../nodejs/tutorial-nodejs.md)
- Completare l'[Esercitazione per Node.js e React](/visualstudio/javascript/tutorial-nodejs-with-react-and-jsx)
- [Distribuire l'app nel Servizio app di Linux](../javascript/publish-nodejs-app-azure.md)