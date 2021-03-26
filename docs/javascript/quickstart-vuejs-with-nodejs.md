---
title: 'Guida introduttiva: creare la prima app Vue.js'
description: In questa Guida introduttiva viene spiegato come creare un'app Vue.js in Visual Studio usando Node.js Tools for Visual Studio
ms.custom: ''
ms.date: 10/31/2019
ms.topic: quickstart
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: ad2892ab7c605ba25902ac2c4c24e68236a5d740
ms.sourcegitcommit: 00e16b9afe6b22ba0591e4d0d92690544e6d4357
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/26/2021
ms.locfileid: "105616974"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Guida introduttiva: Creare per la prima volta un'app Vue.js con Visual Studio

In questa introduzione di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio si creerà ed eseguirà una semplice applicazione Web Vue.js.

> [!IMPORTANT]
> Questo articolo richiede il modello Vue.js disponibile a partire da Visual Studio 2017 versione 15.8.

## <a name="prerequisites"></a>Prerequisiti

* È necessario che siano installati Visual Studio e il carico di lavoro di sviluppo Node.js.

    ::: moniker range=">=vs-2019"
    Se Visual Studio 2019 non è ancora installato, passare alla pagina dei [download di Visual Studio](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Se Visual Studio 2017 non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
    ::: moniker-end

    Se è necessario installare il carico di lavoro ma si dispone già di Visual Studio, passare a **strumenti**  >  **Ottieni strumenti e funzionalità...**, che consente di aprire la programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Node.js**, quindi scegliere **Modifica**.

    ![Carico di lavoro Node.js nel programma di installazione di Visual Studio](../ide/media/quickstart-nodejs-workload.png)

* Il runtime di Node.js deve essere installato.

    Se non è installato, è consigliabile installare la versione LTS dal sito Web [Node.js](https://nodejs.org/en/download/) per una migliore compatibilità con i Framework e le librerie esterni. Node.js è compilato per le architetture a 32 bit e a 64 bit. Gli strumenti Node.js in Visual Studio, inclusi nel carico di lavoro Node.js, supportano entrambe le versioni. Ne è necessario solo uno e il programma di installazione di Node.js ne supporta solo uno in fase di installazione.
    
    In generale, Visual Studio rileva automaticamente il runtime di Node.js installato. Se non rileva un Runtime installato, è possibile configurare il progetto in modo che faccia riferimento al runtime installato nella pagina delle proprietà (dopo aver creato un progetto, fare clic con il pulsante destro del mouse sul nodo del progetto, scegliere **Proprietà** e impostare il **percorso diNode.exe**). È possibile usare un'installazione globale di Node.js oppure è possibile specificare il percorso di un interprete locale in ogni progetto Node.js. 

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa si crea un progetto di applicazione Web Vue.js.

1. Se il runtime di Node.js non è già installato, installare la versione LTS dal sito Web [Node.js](https://nodejs.org/en/download/).

    Per ulteriori informazioni, vedere i prerequisiti.

1. Aprire Visual Studio.

1. Creare un nuovo progetto.

    ::: moniker range=">=vs-2019"
    Premere **ESC** per chiudere la finestra iniziale. Premere **CTRL+Q** per aprire la casella di ricerca, digitare **Vue.js base** e quindi scegliere **applicazione Web Vue.js di base** (JavaScript o TypeScript). Nella finestra di dialogo visualizzata digitare il nome **basic-vuejs**, quindi scegliere **Crea**.

    ![Modello Vue.js](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dalla barra dei menu in alto scegliere **file**  >  **nuovo**  >  **progetto**. Nel riquadro di sinistra della finestra di dialogo **Nuovo progetto** espandere **JavaScript** o **TypeScript**, quindi scegliere **Node.js**. Nel riquadro centrale scegliere **Applicazione Web Vue.js di base**, digitare il nome **basic-vuejs** e scegliere **OK**.

    ![Modello Vue.js](../javascript/media/vuejs-template.png)
    ::: moniker-end
    Se il modello di progetto **Applicazione Web Vue.js di base** non compare, è necessario installare prima il carico di lavoro **Sviluppo Node.js**. Per istruzioni dettagliate, vedere i [Prerequisiti](#prerequisites).

    Visual Studio crea il nuovo progetto. Il nuovo progetto viene aperto in Esplora soluzioni (riquadro a destra).

1. Controllare nella finestra Output, riquadro inferiore, lo stato di avanzamento dell'installazione dei pacchetti npm necessari per l'applicazione.

1. In Esplora soluzioni aprire il nodo **npm** e assicurarsi che tutti i pacchetti npm necessari siano installati.

    Se uno o più pacchetti risultano mancanti (icona con il punto esclamativo), fare clic con il pulsante destro del mouse sul nodo **npm** e scegliere **Installa pacchetti npm mancanti**.

## <a name="explore-the-ide"></a>Esplorare l'IDE

1. Osservare **Esplora soluzioni** nel riquadro a destra.

     ![Soluzione Vue.js](../javascript/media/vuejs-solution.png)

   - Il progetto viene visualizzato in grassetto, con il nome assegnato in precedenza nella finestra di dialogo **Nuovo progetto**. Sul disco, questo progetto è rappresentato da un oggetto. file *njsproj* nella cartella del progetto.

   - Al primo livello è presente una soluzione che, per impostazione predefinita, ha lo stesso nome del progetto. Una soluzione, rappresentata da un oggetto. il file *sln* su disco è un contenitore per uno o più progetti correlati.

   - Il nodo **NPM** Mostra tutti i pacchetti NPM installati. È possibile fare clic con il pulsante destro del mouse sul nodo npm per cercare e installare pacchetti npm tramite una finestra di dialogo.

2. Se si vuole installare pacchetti npm o eseguire comandi Node.js da un prompt dei comandi, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Apri prompt dei comandi qui**.

## <a name="add-a-vue-file-to-the-project"></a>Aggiungere un file con estensione vue al progetto

1. In Esplora soluzioni fare clic con il pulsante destro del mouse su una cartella, ad esempio la cartella *src/components*, quindi scegliere **Aggiungi** > **Nuovo elemento**.

1. Selezionare **Componente file singoli Vue JavaScript** oppure **Componente file singoli Vue TypeScript**, quindi fare clic su **Aggiungi**.

    Visual Studio aggiunge il nuovo file al progetto.

## <a name="build-the-project"></a>Compilare il progetto

::: moniker range=">=vs-2019"
1. In seguito, scegliere **Compila** > **Compila soluzione** per compilare il progetto.

1. Controllare i risultati della compilazione nella finestra **Output** e scegliere **Compila** dall'elenco **Mostra output di**.
::: moniker-end
::: moniker range="vs-2017"
1. (Solo per progetti TypeScript) Da Visual Studio scegliere **Compila** > **Pulisci soluzione**.

1. In seguito, scegliere **Compila** > **Compila soluzione** per compilare il progetto.

1. Controllare i risultati della compilazione nella finestra **Output** e scegliere **Compila** dall'elenco **Mostra output di**.
::: moniker-end

Il modello di progetto Vue.js JavaScript (e le versioni precedenti del modello TypeScript) usano lo `build` script NPM configurando un evento di post-compilazione. Se si vuole modificare questa impostazione, aprire il file di progetto (con *\<projectname\> estensione njsproj*) da Esplora risorse e individuare questa riga di codice:

```xml
<PostBuildEvent>npm run build</PostBuildEvent>
```

## <a name="run-the-application"></a>Eseguire l'applicazione

1. Premere **CTRL** + **F5** (o **debug > avvia senza eseguire debug**) per eseguire l'applicazione.

   Nella console un messaggio avvisa che è in corso *l'avvio del server di sviluppo*.

   Quindi, l'app verrà aperta in un browser.
   
   Se l'app in esecuzione non è visibile, aggiornare la pagina.

   ![App Vue.js in esecuzione nel browser](../javascript/media/vuejs-running-app.png)

1. Chiudere il Web browser.

La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per iniziare ad apprendere l'uso dell'IDE di Visual Studio con Vue.js. Se si vuole approfondire la conoscenza relativa alle funzionalità, scegliere un'esercitazione nella sezione del sommario relativa alle **esercitazioni**.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Creare un'app Vue.js](create-application-with-vuejs.md)

> [!div class="nextstepaction"]
> [Distribuire l'app nel servizio app di Linux](../javascript/publish-nodejs-app-azure.md)