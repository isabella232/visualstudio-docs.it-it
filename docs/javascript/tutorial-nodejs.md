---
title: Creare un'app Node.js ed Express
description: Questa esercitazione illustra come creare un'applicazione Node.js semplice usando il framework dell'applicazione Web Express in Visual Studio.
ms.date: 09/14/2021
ms.custom: vs-acquisition
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 0dbd5b8cd41e3839c7b3c34521bc537b12b5143b
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128430470"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Esercitazione: Creare un progetto Node.js e un'app Express in Visual Studio

Questa esercitazione per lo Visual Studio usa Node.js ed Express. In questa esercitazione viene creata una semplice Node.js Web, si aggiunge codice, si esplorano alcune funzionalità dell'IDE ed è possibile eseguire l'app. 

In questa esercitazione verranno illustrate le procedure per:

> [!div class="checklist"]
> * Creare un progetto Node.js
> * Aggiungere codice
> * Usare IntelliSense per modificare il codice
> * Eseguire l'app
> * Raggiungere un punto di interruzione nel debugger

Prima di iniziare, ecco una rapida domanda frequente per presentare alcuni concetti chiave:

- **Che cos'è Node.js?**
  
  Node.js è un ambiente di runtime JavaScript lato server che esegue codice JavaScript.

- **Che cos'è npm?**
  
  Gestione pacchetti semplifica la pubblicazione e la condivisione di Node.js di codice sorgente. La gestione pacchetti predefinita per Node.js è npm. Gestione pacchetti npm semplifica l'installazione, l'aggiornamento e la disinstallazione della libreria.

- **Che cos'è Express?**
  
  Express è un framework applicazione Web server che Node.js per compilare app Web. Con Express è possibile usare framework front-end diversi per creare un'interfaccia utente. Questa esercitazione usa Pug, in precedenza chiamato Jade, per il framework front-end.

## <a name="prerequisites"></a>Prerequisiti

Questa esercitazione richiede i prerequisiti seguenti:

- Visual Studio con il carico di Node.js di sviluppo installato.
  
  Se non è ancora stato installato Visual Studio:
  
  1. Passare alla pagina [Visual Studio download per](https://visualstudio.microsoft.com/downloads) installare Visual Studio gratuitamente.
     
  1. Nella finestra Programma di installazione di Visual Studio selezionare il carico di **Node.js di** sviluppo e selezionare **Installa**.
     
     ![Screenshot che mostra il carico di lavoro Node j s selezionato nel Programma di installazione di Visual Studio.](media/quickstart-nodejs-workload.png)
  
  Se è già Visual Studio installato:
  
  1. In Visual Studio passare a **Strumenti**  >  **Ottieni strumenti e funzionalità**.
     
  1. Nella finestra Programma di installazione di Visual Studio scegliere il  caricoNode.js di sviluppo e selezionare Modifica **per** scaricare e installare il carico di lavoro.
  
- Runtime Node.js installato:
  
  Se il runtime di Node.js non è installato, installare la versione [di LTS](https://nodejs.org/en/download/)dal sito Web Node.js . La versione LTS offre la migliore compatibilità con altri framework e librerie.
  
  Gli Node.js nel carico di lavoro Visual Studio Node.js supportano entrambe le versioni dell'architettura Node.js a 32 bit e a 64 bit. Visual Studio richiede una sola versione e il Node.js di installazione supporta solo una versione alla volta.
  
  Visual Studio in genere rileva automaticamente il runtime Node.js installato. In caso contrario, è possibile configurare il progetto per fare riferimento al runtime installato:
  
  1. Dopo aver creato un progetto, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Proprietà**.
     
  1. Nel riquadro **Proprietà** impostare il percorsoNode.exe **per** fare riferimento a un'installazione globale o locale Node.js. È possibile specificare il percorso di un interprete locale in ognuno dei progetti Node.js progetto.

::: moniker range=">=vs-2022"
Questa esercitazione è stata testata con Node.js 14.17.5.
::: moniker-end
::: moniker range="<=vs-2019"
Questa esercitazione è stata testata con Node.js 8.10.0.
::: moniker-end

## <a name="create-a-new-nodejs-project"></a>Creare un nuovo progetto Node.js

Visual Studio gestisce i file per una sola applicazione in un *progetto*. Il progetto include i file di configurazione, le risorse e il codice sorgente.

In questa esercitazione si inizia con un semplice progetto con codice per un'app Node.js ed Express.

::: moniker range=">=vs-2022"
1. Aprire Visual Studio e premere **ESC** per chiudere la finestra iniziale.
   
1. Premere **CTRL** Q, digitarenode.jsnella casella di ricerca e quindi scegliere Basic + Azure Node.js Express **4 Application - JavaScript (Applicazione Azure Node.js Express 4 - JavaScript)** nell'elenco a discesa. 
   
   Se l'applicazione **Basic Azure Node.js Express 4** non è visualizzata, è necessario installare il carico di lavoro Node.js sviluppo. Per istruzioni, vedere [Prerequisiti](#prerequisites).
   
1. Nella finestra **di dialogo Configura il nuovo progetto** selezionare **Crea**.
   
   Visual Studio crea la nuova soluzione e il nuovo progetto e apre il progetto nel riquadro destro. Il *app.js* file di progetto viene aperto nell'editor nel riquadro sinistro.
   
1. Esaminare la struttura del progetto in **Esplora soluzioni** nel riquadro di destra.
   
   ![Screenshot che mostra la struttura del progetto in Esplora soluzioni.](media/vs-2022/tutorial-project-structure.png)
   
   - Al livello superiore è la *soluzione* (**1**), che per impostazione predefinita ha lo stesso nome del progetto. Una soluzione, rappresentata da un file *sln* su disco, è un contenitore per uno o più progetti correlati.
   
   - Il progetto (**2**), usando  il nome specificato nella finestra di dialogo Configura nuovo progetto , è evidenziato in grassetto. Nel file system il progetto è un file con estensione *njsproj* nella cartella del progetto.
     
     È possibile visualizzare e impostare le proprietà del progetto e le variabili di ambiente facendo clic con il pulsante destro del mouse sul progetto e **scegliendo Proprietà** dal menu di scelta rapida. È possibile usare altri strumenti di sviluppo, perché il file di progetto non apporta modifiche personalizzate all'origine Node.js progetto.
   
   - Il **nodo npm** (**3**) mostra tutti i pacchetti npm installati. È possibile fare clic con il pulsante destro del mouse sul nodo npm per cercare e installare pacchetti npm usando una finestra di dialogo.
     
     È possibile installare e aggiornare i pacchetti usando le impostazioni in *package.json* e le opzioni di clic con il pulsante destro del mouse nel **nodo npm.**
   
   - Project file (**4**) vengono visualizzati sotto il nodo del progetto. Il file di avvio del **progetto,app.js**, viene visualizzato in grassetto.
     
     Impostare il file di avvio facendo clic con il pulsante destro del mouse su un file del progetto e selezionando **Imposta come file di avvio Node.js**.

   - Npm usa il file **package.json** (**5**) per gestire le dipendenze e le versioni per i pacchetti installati localmente. Per altre informazioni, vedere [Gestire i pacchetti npm](npm-package-management.md).
   
1. Aprire il **nodo npm** per assicurarsi che siano presenti tutti i pacchetti npm necessari.
   
   Se i pacchetti vengono visualizzati **come (mancanti),** fare clic con il pulsante destro del mouse sul nodo **npm,** scegliere **Installa pacchetti npm** e installare i pacchetti mancanti.
:::moniker-end
:::moniker range="vs-2019"
1. Aprire Visual Studio.

1. Creare un nuovo progetto.

    Premere **ESC** per chiudere la finestra iniziale. Premere **CTRL+Q** per aprire la casella di ricerca, digitare **Node.js** e scegliere **Create new Basic Azure Node.js Express 4 application** (Crea nuova applicazione Basic Azure Node.js Express 4) (JavaScript). Nella finestra di dialogo visualizzata scegliere **Crea**.
    
    Se non viene visualizzato il modello di progetto **Applicazione Express 4 Node.js Azure di base** è necessario aggiungere il carico di lavoro **Sviluppo Node.js**. Per istruzioni, vedere [Prerequisiti](#prerequisites).

    Visual Studio crea la nuova soluzione e apre il progetto nel riquadro destro. Il file di progetto *app.js* verrà aperto nell'editor (riquadro a sinistra).

    ![Screenshot che mostra la struttura del progetto in Esplora soluzioni.](../javascript/media/tutorial-project-structure.png)

    (1) Il progetto viene visualizzato in **grassetto**, con il nome assegnato in precedenza nella finestra di dialogo **Nuovo progetto**. Nel file system il progetto è rappresentato da un file con estensione *njsproj* nella cartella del progetto. È possibile impostare le proprietà e le variabili di ambiente associate al progetto facendo clic con il pulsante destro del mouse sul progetto e scegliendo **Proprietà**. È possibile eseguire sequenze di andata e ritorno con altri strumenti di sviluppo, perché il file di progetto non apporta modifiche personalizzate all'origine del progetto Node.js.

    (2) Al primo livello è presente una soluzione che, per impostazione predefinita, ha lo stesso nome del progetto. Una soluzione, rappresentata da un file *sln* su disco, è un contenitore per uno o più progetti correlati.

    (3) Il nodo npm visualizza tutti i pacchetti npm eventualmente installati. È possibile fare clic con il pulsante destro del mouse sul nodo npm per cercare e installare i pacchetti npm utilizzando una finestra di dialogo o per installare e aggiornare i pacchetti usando le impostazioni in *package.json* e fare clic con il pulsante destro del mouse sulle opzioni nel nodo npm.

    (4) *package.json* è un file usato da npm per gestire le dipendenze dei pacchetti e le versioni dei pacchetti per i pacchetti installati localmente. Per altre informazioni, vedere [Gestire i pacchetti npm](../javascript/npm-package-management.md).

    (5) I file di progetto come *app.js* vengono visualizzati sotto il nodo del progetto. *app.js* è il file di avvio del progetto e per questo motivo viene visualizzata in **grassetto**. Impostare il file di avvio facendo clic con il pulsante destro del mouse su un file del progetto e selezionando **Imposta come file di avvio Node.js**.

1. Aprire il nodo **npm** e assicurarsi che siano presenti tutti i pacchetti npm necessari.

    Se mancano pacchetti (icona del punto esclamativo), è possibile fare clic con il pulsante destro del mouse sul nodo **npm** e scegliere **Installa pacchetti npm**.
:::moniker-end
:::moniker range="vs-2017"
1. Aprire Visual Studio.

1. Creare un nuovo progetto.

    Nella barra dei menu superiore scegliere **File**  >  **Nuovo**  >  **Project**. Nel riquadro di sinistra della finestra di dialogo **Nuovo progetto** espandere **JavaScript**, quindi selezionare **Node.js**. Nel riquadro centrale scegliere **Applicazione Express 4 Node.js Azure di base** e quindi scegliere **OK**.
    
    Se non viene visualizzato il modello di progetto **Applicazione Express 4 Node.js Azure di base** è necessario aggiungere il carico di lavoro **Sviluppo Node.js**. Per istruzioni, vedere [Prerequisiti.](#prerequisites)

    Visual Studio crea la nuova soluzione e apre il progetto nel riquadro destro. Il file di progetto *app.js* verrà aperto nell'editor (riquadro a sinistra).

    ![Screenshot che mostra la struttura del progetto in Esplora soluzioni.](../javascript/media/tutorial-project-structure.png)

    (1) Il progetto viene visualizzato in **grassetto**, con il nome assegnato in precedenza nella finestra di dialogo **Nuovo progetto**. Nel file system il progetto è rappresentato da un file con estensione *njsproj* nella cartella del progetto. È possibile impostare le proprietà e le variabili di ambiente associate al progetto facendo clic con il pulsante destro del mouse sul progetto e scegliendo **Proprietà**. È possibile eseguire sequenze di andata e ritorno con altri strumenti di sviluppo, perché il file di progetto non apporta modifiche personalizzate all'origine del progetto Node.js.

    (2) Al primo livello è presente una soluzione che, per impostazione predefinita, ha lo stesso nome del progetto. Una soluzione, rappresentata da un file *con estensione sln* su disco, è un contenitore per uno o più progetti correlati.

    (3) Il nodo npm visualizza tutti i pacchetti npm eventualmente installati. È possibile fare clic con il pulsante destro del mouse sul nodo npm per cercare e installare i pacchetti npm utilizzando una finestra di dialogo o per installare e aggiornare i pacchetti usando le impostazioni in *package.json* e fare clic con il pulsante destro del mouse sulle opzioni nel nodo npm.

    (4) *package.json è* un file usato da npm per gestire le dipendenze dei pacchetti e le versioni dei pacchetti per i pacchetti installati localmente. Per altre informazioni, vedere [Gestire i pacchetti npm.](../javascript/npm-package-management.md)

    (5) I file di progetto come *app.js* vengono visualizzati sotto il nodo del progetto. *app.js* è il file di avvio del progetto e per questo motivo viene visualizzata in **grassetto**. Impostare il file di avvio facendo clic con il pulsante destro del mouse su un file del progetto e selezionando **Imposta come file di avvio Node.js**.

1. Aprire il nodo **npm** e assicurarsi che siano presenti tutti i pacchetti npm necessari.

    Se mancano pacchetti (icona del punto esclamativo), è possibile fare clic con il pulsante destro del mouse sul **nodo npm** e scegliere **Installa pacchetti npm**.
    ::: moniker-end

## <a name="add-some-code"></a>Aggiungere codice

L'applicazione usa Pug per il framework JavaScript front-end. Pug usa un codice markup semplice che viene compilato in formato HTML.

Pug viene impostato come motore di visualizzazione in *app.js*, con il codice `app.set('view engine', 'pug');` .

1. In **Esplora soluzioni** aprire la **cartella views** e quindi selezionare **index.pug** per aprire il file.

1. Sostituire il contenuto del file con il markup seguente.

    ```js
    extends layout

    block content
      h1= title
      p Welcome to #{title}
      script.
        var f1 = function() { document.getElementById('myImage').src='#{data.item1}' }
      script.
        var f2 = function() { document.getElementById('myImage').src='#{data.item2}' }
      script.
        var f3 = function() { document.getElementById('myImage').src='#{data.item3}' }

      button(onclick='f1()') One!
      button(onclick='f2()') Two!
      button(onclick='f3()') Three!
      p
      a: img(id='myImage' height='300' width='300' src='')
    ```

    Il codice precedente genera dinamicamente una pagina HTML con un titolo e un messaggio di benvenuto. La pagina include anche il codice per visualizzare un'immagine che cambia ogni volta che si preme un pulsante.

1. Nella cartella **routes** aprire **index.js**.

1. Aggiungere il codice seguente prima della `router.get` chiamata di funzione:

    ```js
    var getData = function () {
        var data = {
            'item1': 'https://images.unsplash.com/photo-1563422156298-c778a278f9a5',
            'item2': 'https://images.unsplash.com/photo-1620173834206-c029bf322dba',
            'item3': 'https://images.unsplash.com/photo-1602491673980-73aa38de027a'
        }
        return data;
    }
    ````

    Questo codice crea un oggetto dati che viene passato alla pagina HTML generata in modo dinamico.

1. Sostituire la chiamata alla funzione `router.get` con il codice seguente:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    Il codice precedente imposta la pagina corrente usando l'oggetto router di Express ed esegue il rendering della pagina, passando il titolo e l'oggetto dati alla pagina. Il codice specifica il file *index.pug* come pagina da caricare quandoindex.js *esecuzione.* Il *app.js,* non illustrato qui, configura *index.js* come route predefinita.

    Per illustrare Visual Studio funzionalità, si verifica un errore intenzionale nella riga di codice che contiene `res.render` . Nella sezione successiva IntelliSense consente di correggere l'errore in modo che l'app possa essere eseguita.

## <a name="use-intellisense"></a>Usare IntelliSense

IntelliSense è uno Visual Studio che consente di scrivere codice.

1. *Nellindex.js* nell'editor Visual Studio di codice passare alla riga di codice che contiene `res.render` .

1. Posizionare il cursore dopo la `"data"` stringa e digitare `: get` . IntelliSense visualizza `getData` la funzione definita in precedenza nel codice. Selezionare `getData`.

    ::: moniker range=">=vs-2022"
    ![Screenshot che mostra l'uso di IntelliSense.](media/vs-2022/tutorial-nodejs-intellisense.png)
    ::: moniker-end
    ::: moniker range="<=vs-2019"
    ![Screenshot che mostra l'uso di IntelliSense.](../javascript/media/tutorial-nodejs-intellisense.png)
    ::: moniker-end

1. Aggiungere le parentesi per rendere il codice una chiamata di funzione: `getData()` .

1. Rimuovere la virgola prima di `"data"` . L'evidenziazione della sintassi verde viene visualizzata nell'espressione. Spostare il puntatore del mouse sull'evidenziazione della sintassi.

    ::: moniker range=">=vs-2022"
    ![Screenshot che mostra un errore di sintassi in IntelliSense.](media/vs-2022/tutorial-nodejs-syntax-checking.png)
    ::: moniker-end
    ::: moniker range="<=vs-2019"
    ![Screenshot che mostra un errore di sintassi in IntelliSense.](../javascript/media/tutorial-nodejs-syntax-checking.png)
    ::: moniker-end

    L'ultima riga del messaggio indica che l'interprete JavaScript prevedeva una virgola.

1. Nel riquadro inferiore selezionare la scheda **Elenco** errori e selezionare Compila **e IntelliSense** nell'elenco a discesa per il tipo di problemi segnalati.

    Nel riquadro vengono visualizzati l'avviso e la descrizione insieme al nome file e al numero di riga.

    ::: moniker range=">=vs-2022"
    ![Screenshot che mostra il riquadro Elenco errori con l'errore elencato.](media/vs-2022/tutorial-nodejs-error-list.png)
    ::: moniker-end
    ::: moniker range="<=vs-2019"
    ![Screenshot che mostra il riquadro Elenco errori con l'errore elencato.](../javascript/media/tutorial-nodejs-error-list.png)
    ::: moniker-end

1. Correggere il codice sostituendo la virgola prima di `"data"` .

    La riga di codice corretta dovrebbe essere simile alla seguente: `res.render('index', { title: 'Express', "data": getData() });`

## <a name="run-the-app"></a>Eseguire l'app

Eseguire quindi l'app con il debugger Visual Studio collegato. Prima di eseguire questa operazione, è necessario impostare un punto di interruzione.

### <a name="set-a-breakpoint"></a>Imposta punto di interruzione

I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica dove Visual Studio deve sospendere il codice in esecuzione. È quindi possibile osservare i valori delle variabili, il comportamento della memoria o se un ramo di codice è in esecuzione.

- Per impostare un punto di *interruzione,index.js* fare clic nella barra di sinistra prima della riga di codice seguente:

  `res.render('index', { title: 'Express', "data": getData() });`

  ::: moniker range=">=vs-2022"
  ![Screenshot che mostra l'impostazione di un punto di interruzione.](media/vs-2022/tutorial-nodejs-set-breakpoint.png)
  ::: moniker-end
  ::: moniker range="<=vs-2019"
  ![Screenshot che mostra l'impostazione di un punto di interruzione.](../javascript/media/tutorial-nodejs-set-breakpoint.png)
  ::: moniker-end

### <a name="run-the-app-in-debug-mode"></a>Eseguire l'app in modalità debug

1. Selezionare la destinazione di debug nella barra degli strumenti **Debug,** ad esempio **Server Web (Google Chrome)** o **Server Web (Microsoft Edge).**

    ::: moniker range=">=vs-2022"
    ![Screenshot che mostra la selezione della destinazione di debug.](media/vs-2022/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2019"
    ![Screenshot che mostra la selezione della destinazione di debug.](../javascript/media/vs-2019/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Screenshot che mostra la selezione della destinazione di debug.](../javascript/media/tutorial-nodejs-deploy-target.png)
    ::: moniker-end

    Se si sa che la destinazione di debug preferita è disponibile nel computer, ma non viene visualizzata come opzione, selezionare **Sfoglia** con nell'elenco a discesa della destinazione di debug. Selezionare la destinazione del browser predefinita nell'elenco e selezionare **Imposta come predefinita.**

1. Premere **F5 o** selezionare **Debug** Avvia  >  **debug per** eseguire l'app.

    Il debugger viene sospeso in corrispondenza del punto di interruzione impostato, in modo da poter controllare lo stato dell'app.

1. Passare il `getData` puntatore del mouse su per visualizzarne le proprietà in un suggerimento dati:

    ::: moniker range=">=vs-2022"
    [![Screenshot che mostra il controllo delle variabili durante il debug.](media/vs-2022/tutorial-nodejs-inspect-variables.png)](media/vs-2022/tutorial-nodejs-inspect-variables.png#lightbox)
    ::: moniker-end
    ::: moniker range="<=vs-2019"
    ![Screenshot che mostra il controllo delle variabili durante il debug.](../javascript/media/tutorial-nodejs-inspect-variables.png)
    ::: moniker-end

1. Premere **F5 o** selezionare **Debug**  >  **Continua per** continuare a eseguire l'app.

    L'app viene aperta in un browser. Nella finestra del browser dovrebbero essere visualizzati **Express** come titolo e **Welcome to Express** come primo paragrafo.

1. Selezionare **i valori One!**, **Two!** e **Three!** per visualizzare immagini diverse.

    ![Screenshot che mostra l'app in esecuzione in un browser.](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. Chiudere il Web browser.

## <a name="publish-to-azure-app-service-optional"></a>Pubblica in Servizio app di Azure (facoltativo)

::: moniker range=">=vs-2022"
1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**. 
   
   - Se richiesto, selezionare **Aggiungi un profilo di pubblicazione.**
   - Se viene richiesto di installare Azure WebJob Tools, selezionare **Installa.**
   
1. Nella prima **schermata Pubblica** selezionare **Azure** e quindi selezionare **Avanti.**
   
   ![Screenshot che mostra la finestra di dialogo Pubblica con Azure selezionato.](media/vs-2022/tutorial-nodejs-publish-azure.png)
   
   
1. Nella seconda **schermata Pubblica** selezionare Servizio app di Azure **(Windows)** e quindi selezionare **Avanti.**
   
   ![Screenshot che mostra la finestra di dialogo Pubblica Servizio app di Azure selezionata.](media/vs-2022/tutorial-nodejs-publish-azure-app.png)
   
1. Nella schermata successiva accedere ad Azure, se necessario. Selezionare la sottoscrizione di Azure, il gruppo di risorse e il servizio app in cui si vuole pubblicare e quindi selezionare **Fine.**

   - Se non si ha una sottoscrizione di Azure, un gruppo di risorse o un servizio app, è possibile crearli seguendo le istruzioni visualizzate in questa schermata.
   
   ![Screenshot che mostra la finestra di dialogo Pubblica con l'app Web di Azure selezionata.](media/vs-2022/tutorial-nodejs-publish-web-app.png)
   
   Per istruzioni più dettagliate, vedere [Pubblicare nel sito Web di Azure usando la distribuzione Web.](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy)
   
1. Esaminare la configurazione di pubblicazione e quindi selezionare **Pubblica**.

   ![Screenshot che mostra la configurazione di pubblicazione e il pulsante in Visual Studio.](media/vs-2022/tutorial-nodejs-publish-ready.png)
   
   La Visual Studio **Output mostra** lo stato di avanzamento della distribuzione di Azure.
   
1. Al completamento della distribuzione, l'app viene aperta in Servizio app di Azure in un browser. Selezionare un pulsante per visualizzare un'immagine.
   
   ![Screenshot che mostra l'app Web in esecuzione in Servizio app di Azure in un browser.](media/vs-2022/tutorial-nodejs-running-in-azure.png)

::: moniker-end
::: moniker range="<=vs-2019"
1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**.

   ![Screenshot che mostra Pubblica in Servizio app di Azure.](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. Scegliere **Servizio app di Microsoft Azure**.

    Nella finestra di dialogo **Servizio app** è possibile accedere all'account di Azure e connettersi a sottoscrizioni di Azure esistenti.

1. Seguire i passaggi rimanenti per selezionare una sottoscrizione, scegliere o creare un gruppo di risorse, scegliere o creare un piano di servizio app e quindi seguire la procedura quando viene richiesto di pubblicare in Azure. Per istruzioni più dettagliate, vedere [Pubblicare nel sito Web di Azure usando la distribuzione Web.](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy)

1. La finestra **Output** visualizza lo stato della distribuzione in Azure.

    Al termine della distribuzione, l'app viene aperta in un browser in esecuzione in Servizio app di Azure. Fare clic su un pulsante per visualizzare un'immagine.

   ![Screenshot che mostra l'app Web in esecuzione in Servizio app di Azure in un browser.](../javascript/media/tutorial-nodejs-running-in-azure.png)
::: moniker-end
L'esercitazione è stata completata.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Distribuire l'app nel servizio app di Linux](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [Estensione del servizio di linguaggio AngularJS](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio)
