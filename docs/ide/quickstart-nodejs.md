---
title: 'Guida introduttiva: Usare Visual Studio per creare la prima app Node.js'
description: In questa guida introduttiva verrà creata un'app Node.js in Visual Studio
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-nodejs
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
ms.openlocfilehash: f11396527208862428483744bc1ac3b02583f4c8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955492"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Guida introduttiva: Usare Visual Studio per creare la prima app Node.js

In questa introduzione di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio si creerà una semplice applicazione Web Node.js. Se Visual Studio 2017 non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) per installarlo gratuitamente.

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa si crea un progetto di applicazione Web Node.js.

1. Se il runtime di Node.js non è già installato, installare la versione LTS dal sito Web [Node.js](https://nodejs.org/en/download/).

    In generale, Visual Studio rileva automaticamente il runtime di Node.js installato. Se non viene rilevato un runtime installato, è possibile usare la pagina delle proprietà per configurare il progetto in modo che faccia riferimento al runtime installato (dopo aver creato un progetto, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Proprietà**).

1. Aprire Visual Studio 2017.

1. Sulla barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.

1. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **JavaScript** e quindi selezionare **Node.js**. Nel riquadro centrale scegliere **Applicazione Web Node.js vuota**, quindi scegliere **OK**.

     Se non viene visualizzato il modello di progetto **Applicazione Web Node.js vuota**, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Node.js**, quindi scegliere **Modifica**.

     ![Carico di lavoro Node.js nel programma di installazione di Visual Studio](../ide/media/quickstart-nodejs-workload.png)

    Dopo che si è scelto il modello **Applicazione Web Node.js vuota** seguito da **OK**, Visual Studio crea la nuova soluzione e apre il progetto. Nell'editor nel riquadro sinistro si apre *server.js*.

## <a name="explore-the-ide"></a>Esplorare l'IDE

1. Osservare **Esplora soluzioni** nel riquadro a destra.

   ![Esplora soluzioni](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Il progetto viene visualizzato in grassetto, con il nome assegnato in precedenza nella finestra di dialogo **Nuovo progetto**. Sul disco, questo progetto è rappresentato da un file con estensione *.njsproj* nella cartella del progetto.

   - Al primo livello è presente una soluzione che, per impostazione predefinita, ha lo stesso nome del progetto. Una soluzione, rappresentata su disco da un file con estensione *sln*, è un contenitore per uno o più progetti correlati.

   - Il nodo npm visualizza tutti i pacchetti npm eventualmente installati. È possibile fare clic con il pulsante destro del mouse sul nodo npm per cercare e installare pacchetti npm tramite una finestra di dialogo.

1. Se si vuole installare pacchetti npm o comandi Node.js da un prompt dei comandi, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Apri prompt dei comandi qui**.

   ![Prompt dei comandi node.js](../ide/media/quickstart-nodejs-command-prompt.png)

1. Nel file *server.js* dell'editor (riquadro sinistro), scegliere `http.createServer` e premere **F12** oppure scegliere **Vai a definizione** dal menu di scelta rapida (attivato con il clic destro del mouse). Questo comando consente di passare alla definizione della funzione `createServer` in *index.d.ts*.

   ![Menu di scelta rapida Vai a definizione](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Ritornare a *server.js*, posizionare il cursore alla fine della stringa di questa riga di codice, `res.end('Hello World\n');`, e modificarla come visualizzato di seguito:

    `res.end('Hello World\n' + res.connection.`

    Quando si digita `connection.` IntelliSense offre opzioni per il completamento automatico dell'immissione di codice.

   ![Completamento automatico di IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)

1. Scegliere **localPort**, quindi digitare `);` per completare l'istruzione in modo che risulti simile alla seguente:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Esecuzione dell'applicazione

1. Premere **Ctrl**+**F5** (o scegliere **Debug > Avvia senza eseguire debug**) per eseguire l'applicazione. L'app verrà aperta in un browser.

1. Nella finestra del browser viene visualizzato "Hello World" e il numero della porta locale.

1. Chiudere il Web browser.

È stata completata la Guida introduttiva che ha fornito una panoramica dell'IDE di Visual Studio e di Node.js. Se si vuole approfondire la conoscenza relativa alle funzionalità, scegliere un'esercitazione nella sezione del sommario relativa alle **esercitazioni**.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Distribuire l'app nel Servizio app di Linux](../javascript/publish-nodejs-app-azure.md)

- [Tutorial for Node.js and Express](../javascript/tutorial-nodejs.md) (Esercitazione per Node.js ed Express)
- [Tutorial for Node.js and React](../javascript/tutorial-nodejs-with-react-and-jsx.md) (Esercitazione per Node.js e React)