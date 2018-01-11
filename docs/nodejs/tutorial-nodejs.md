---
title: Introduzione a Node.js in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: ghogen
dev_langs: JavaScript
ms.workload: nodejs
ms.openlocfilehash: 80822e4f323621a97beb453118d7e0836ae9ea92
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-nodejs-in-visual-studio"></a>Introduzione a Node.js in Visual Studio
In questa esercitazione per lo sviluppo in Node.js tramite Visual Studio si creerà una semplice applicazione Web Node.js e si aggiungerà codice all'app. Si esploreranno poi alcune funzionalità dell'ambiente IDE e si eseguirà l'app. Se non è ancora stato installato Visual Studio, installarlo gratuitamente [qui](http://www.visualstudio.com).  

## <a name="create-a-project"></a>Creare un progetto
Per prima cosa si crea un progetto di applicazione Web Node.js.

1. Aprire Visual Studio 2017.  

2. Nella barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.  

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **JavaScript** e quindi selezionare **Node.js**. Nel riquadro centrale scegliere **Applicazione Express 4 Node.js Azure di base** e quindi scegliere **OK**.   

     Se non viene visualizzato il modello di progetto **Applicazione Express 4 Node.js Azure di base**, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Node.js**, quindi scegliere **Modifica**. 

    Visual Studio crea la nuova soluzione e apre il progetto. Il file di progetto **app.js** verrà aperto nell'editor (riquadro a sinistra). Se non si ha familiarità con i progetti e le soluzioni di Visual Studio, vedere [Quickstart: Use Visual Studio to create your first Node.js app](../ide/quickstart-nodejs.md) (Guida introduttiva: uso di Visual Studio per creare la prima app Node.js).

## <a name="add-some-code"></a>Aggiungere codice

1. In Esplora soluzioni (riquadro a destra) aprire la cartella Visualizzazioni e quindi aprire index.pug.

1. Sostituire il contenuto con il markup seguente.

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
      a: img(id='myImage' height='200' width='200' src='')
    ```

1. Nella cartella Route aprire index.js.

1. Aggiungere il codice seguente prima della chiamata a `router.get`:

    ```js
    var getData = function () {
        var data = {
            'item1': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg',
            'item2': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg',
            'item3': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg'
        }
        return data;
    }
    ````

1. Sostituire la chiamata alla funzione `router.get` con il codice seguente:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

1. Dopo `data` digitare `: get`. IntelliSense visualizzerà la funzione getData. Selezionare `getData`.

    ![Usare IntelliSense](../nodejs/media/tutorial-nodejs-intellisense.png) 

1. Rimuovere la virgola (`,`) prima di `"data"`. Verrà visualizzata l'evidenziazione verde della sintassi per l'espressione. Spostare il puntatore del mouse sull'evidenziazione della sintassi.

    ![Visualizzazione di un errore di sintassi](../nodejs/media/tutorial-nodejs-syntax-checking.png) 

    L'ultima riga di questo messaggio indica che l'interprete JavaScript prevedeva una virgola (`,`).

1. Fare clic sulla scheda **Elenco errori**.

    Con il nome del file e il numero di riga verranno visualizzati l'avviso e la relativa descrizione.

    ![Visualizzazione dell'elenco errori](../nodejs/media/tutorial-nodejs-error-list.png)

1. Correggere il codice aggiungendo la virgola (`,`) prima di `"data"`.

## <a name="set-a-breakpoint"></a>Imposta punto di interruzione

1. In index.js fare clic sul margine a sinistra prima della riga di codice seguente per impostare un punto di interruzione:

    `res.render('index', { title: 'Express', "data": getData() });`

    I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice. 

    ![Imposta punto di interruzione](../nodejs/media/tutorial-nodejs-set-breakpoint.png) 

## <a name="run-the-application"></a>Esecuzione dell'applicazione

1. Selezionare la destinazione di debug sulla barra degli strumenti Debug.

    ![Selezione della destinazione di debug](../nodejs/media/tutorial-nodejs-deploy-target.png) 

1. Premere **CTRL+F5** per eseguire l'applicazione.

    Il debugger si fermerà in corrispondenza del punto di interruzione impostato. È ora possibile esaminare lo stato dell'app.

1. Spostare il puntatore del mouse su `getData` per visualizzarne le proprietà in un suggerimento dati

    ![Esame delle variabili](../nodejs/media/tutorial-nodejs-inspect-variables.png)

1. Premere **F5** per continuare.

    L'app verrà aperta in un browser.

    Nella finestra del browser verrà visualizzato il titolo "Express" e nel primo paragrafo verrà visualizzato il messaggio "Welcome to Express".

1. Fare clic sui pulsanti per visualizzare immagini diverse.

1. Aprire la finestra interattiva di Node.js selezionando **Visualizza > Altre finestre > Finestra interattiva di Node.js**.

   ![Apertura della finestra interattiva di Node.js](../nodejs/media/tutorial-nodejs-interactive-window.png)  

    La finestra interattiva supporta tutte le operazioni consentite nel codice, incluso l'uso di istruzioni `require()`. Il codice nello screenshot seguente definisce una variabile e visualizza la posizione dell'interprete Node.js.

   ![Finestra interattiva di Node.js](../nodejs/media/tutorial-nodejs-interactive-window-example.png)  

1. Chiudere il Web browser.  

## <a name="publish-to-azure-app-service"></a>Eseguire la pubblicazione nel servizio app di Azure

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**.

   ![Eseguire la pubblicazione nel servizio app di Azure](../nodejs/media/tutorial-nodejs-publish-to-azure.png)  

1. Scegliere **Servizio app di Microsoft Azure**.

    Nella finestra di dialogo **Servizio app** è possibile accedere all'account di Azure e connettersi a sottoscrizioni di Azure esistenti.

1. Seguire i passaggi rimanenti per selezionare una sottoscrizione, scegliere o creare un gruppo di risorse, scegliere o creare un piano di servizio app e quindi, quando richiesto, seguire i passaggi per la pubblicazione in Azure. Per istruzioni più dettagliate, vedere [Publish to Azure Website using Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy) (Pubblicare in Sito Web di Azure tramite Distribuzione Web).

1. La finestra **Output** visualizza lo stato della distribuzione in Azure.

    Al termine della distribuzione, l'app viene aperta in un browser in esecuzione in Servizio app di Azure. Fare clic su un pulsante per visualizzare un'immagine.

   ![App in esecuzione in Servizio app di Azure](../nodejs/media/tutorial-nodejs-running-in-azure.png)  

L'esercitazione è stata completata.

## <a name="next-steps"></a>Passaggi successivi 

- Altre informazioni sugli [strumenti Node.js per Visual Studio](https://github.com/Microsoft/nodejstools/wiki)  
- Altre informazioni sull'[ambiente IDE di Visual Studio](../ide/visual-studio-ide.md)  