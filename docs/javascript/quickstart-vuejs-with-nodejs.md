---
title: 'Guida introduttiva: Creare la prima app Vue.js'
description: In questa Guida introduttiva viene spiegato come creare un'app Vue.js in Visual Studio usando Node.js Tools for Visual Studio
ms.custom: ''
ms.date: 10/31/2019
ms.topic: quickstart
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 882c3a148164ab88412a817abd72d0608fadf9b2
ms.sourcegitcommit: 5c804c42d24d35dcf2ba195aba9ce07031743f62
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "81744984"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Guida introduttiva: Creare per la prima volta un'app Vue.js con Visual Studio

In questa introduzione di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio si creerà ed eseguirà una semplice applicazione Web Vue.js.

> [!IMPORTANT]
> Questo articolo richiede il modello Vue.js disponibile a partire da Visual Studio 2017 versione 15.8.

## <a name="prerequisites"></a>Prerequisiti

* È necessario che siano installati Visual Studio e il carico di lavoro di sviluppo Node.js.

    ::: moniker range=">=vs-2019"
    Se non hai ancora installato Visual Studio 2019, vai alla pagina dei [download](https://visualstudio.microsoft.com/downloads/) di Visual Studio per installarlo gratuitamente.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Se non hai ancora installato Visual Studio 2017, vai alla pagina dei [download](https://visualstudio.microsoft.com/downloads/) di Visual Studio per installarlo gratuitamente.
    ::: moniker-end

    Se è necessario installare il carico di lavoro ma si dispone già di Visual Studio, passare a **Strumenti** > **Get Tools and Features...**, che apre il programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Node.js**, quindi scegliere **Modifica**.

    ![Carico di lavoro Node.js nel programma di installazione di Visual Studio](../ide/media/quickstart-nodejs-workload.png)

* Il runtime di Node.js deve essere installato.

    Se non è installato, si consiglia di installare la versione LTS dal sito [Web Node.js](https://nodejs.org/en/download/) per la migliore compatibilità con framework e librerie esterni. Node.js è progettato per architetture a 32 e 64 bit. Gli strumenti Node.js in Visual Studio, inclusi nel carico di lavoro Node.js, supportano entrambe le versioni. Ne è richiesto solo uno e il programma di installazione Node.js supporta solo uno in fase di installazione alla volta.
    
    In generale, Visual Studio rileva automaticamente il runtime di Node.js installato. Se non rileva un runtime installato, è possibile configurare il progetto in modo che faccia riferimento al runtime installato nella pagina delle proprietà (dopo aver creato un progetto, aver fatto clic con il pulsante destro del mouse sul nodo del progetto, scegliere **Proprietà**e impostare il **percorso di Node.exe**). È possibile utilizzare un'installazione globale di Node.js oppure è possibile specificare il percorso di un interprete locale in ognuno dei progetti Node.js. 

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa si crea un progetto di applicazione Web Vue.js.

1. Se il runtime di Node.js non è già installato, installare la versione LTS dal sito Web [Node.js](https://nodejs.org/en/download/).

    Per altre informazioni, vedere i prerequisiti.

1. Aprire Visual Studio.

1. Creare un nuovo progetto.

    ::: moniker range=">=vs-2019"
    Premere **ESC** per chiudere la finestra iniziale. Premere **CTRL+Q** per aprire la casella di ricerca, digitare **Vue.js base** e quindi scegliere **applicazione Web Vue.js di base** (JavaScript o TypeScript). Nella finestra di dialogo visualizzata digitare il nome **basic-vuejs**, quindi scegliere **Crea**.

    ![Modello Vue.js](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dalla barra dei menu superiore, scegliere **File** > **Nuovo** > **progetto**. Nel riquadro di sinistra della finestra di dialogo **Nuovo progetto** espandere **JavaScript** o **TypeScript**, quindi scegliere **Node.js**. Nel riquadro centrale scegliere **Applicazione Web Vue.js di base**, digitare il nome **basic-vuejs** e scegliere **OK**.

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

   - Il progetto viene visualizzato in grassetto, con il nome assegnato in precedenza nella finestra di dialogo **Nuovo progetto**. Su disco, questo progetto è rappresentato da un oggetto . *njsproj* nella cartella del progetto.

   - Al primo livello è presente una soluzione che, per impostazione predefinita, ha lo stesso nome del progetto. Una soluzione, rappresentata da un oggetto . *sln* file su disco, è un contenitore per uno o più progetti correlati.

   - Il nodo **npm** mostra tutti i pacchetti npm installati. È possibile fare clic con il pulsante destro del mouse sul nodo npm per cercare e installare pacchetti npm tramite una finestra di dialogo.

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

Il modello di progetto Vue.js JavaScript (e le `build` versioni precedenti del modello TypeScript) usano lo script npm configurando un evento post-compilazione. Se si desidera modificare questa impostazione, aprire il file di progetto (*\<nomeprogetto\>.njsproj*) da Esplora risorse e individuare questa riga di codice:

```xml
<PostBuildEvent>npm run build</PostBuildEvent>
```

## <a name="run-the-application"></a>Eseguire l'applicazione

1. Premere **CTRL**+**F5** (o **Esegui debug > Avvia senza eseguire debug**) per eseguire l'applicazione.

   Nella console un messaggio avvisa che è in corso *l'avvio del server di sviluppo *.

   Quindi, l'app verrà aperta in un browser.
   
   Se non vedi l'app in esecuzione, aggiorna la pagina.

   ![App Vue.js in esecuzione nel browser](../javascript/media/vuejs-running-app.png)

1. Chiudere il Web browser.

La guida introduttiva è stata completata. Ci auguriamo che sia stata utile per iniziare ad apprendere l'uso dell'IDE di Visual Studio con Vue.js. Se si vuole approfondire la conoscenza relativa alle funzionalità, scegliere un'esercitazione nella sezione del sommario relativa alle **esercitazioni**.

## <a name="next-steps"></a>Passaggi successivi

- Vai attraverso l'articolo per [Vue.js](create-application-with-vuejs.md)
- Completare l'[Esercitazione per Node.js e Express](tutorial-nodejs.md)
- [Distribuire l'app nel servizio app di Linux](../javascript/publish-nodejs-app-azure.md)