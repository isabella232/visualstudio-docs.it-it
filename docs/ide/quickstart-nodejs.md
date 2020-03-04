---
title: "Guida introduttiva: Creare per la prima volta un'app Node.js con Visual Studio"
description: In questa guida introduttiva verrà creata un'app Node.js in Visual Studio
ms.date: 06/27/2018
ms.technology: vs-javascript
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
ms.openlocfilehash: f716421da3b9f888dbb7656c55db6814de88332b
ms.sourcegitcommit: 9eff8371b7a79a637ebb6850f775dd3eed343d8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2020
ms.locfileid: "78235054"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Guida introduttiva: Creare per la prima volta un'app Node.js con Visual Studio

In questa introduzione di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio si creerà una semplice applicazione Web Node.js.

## <a name="prerequisites"></a>Prerequisites

* È necessario che siano installati Visual Studio e il carico di lavoro di sviluppo Node.js.

    ::: moniker range=">=vs-2019"
    Se Visual Studio 2019 non è ancora installato, accedere alla pagina  [Download di Visual Studio](https://visualstudio.microsoft.com/downloads)  per installarlo gratuitamente.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Se Visual Studio 2017 non è ancora installato, accedere alla pagina  [Download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)  per installarlo gratuitamente.
    ::: moniker-end

    Se occorre installare il carico di lavoro, ma si ha già Visual Studio, passare a **Strumenti** > **Ottieni strumenti e funzionalità**, che apre il programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Node.js**, quindi scegliere **Modifica**.

    ![Carico di lavoro Node.js nel programma di installazione di Visual Studio](../ide/media/quickstart-nodejs-workload.png)

* Il runtime di Node.js deve essere installato.

    Se non è installato, è consigliabile installare la versione LTS dal sito Web [node. js](https://nodejs.org/en/download/) per una migliore compatibilità con i Framework e le librerie esterni. Node. js è compilato per le architetture a 32 bit e a 64 bit. Gli strumenti node. js in Visual Studio, inclusi nel carico di lavoro node. js, supportano entrambe le versioni. Ne è necessario solo uno e il programma di installazione di node. js ne supporta solo uno che viene installato alla volta.
    
    In generale, Visual Studio rileva automaticamente il runtime di Node.js installato. Se non rileva un Runtime installato, è possibile configurare il progetto in modo che faccia riferimento al runtime installato nella pagina proprietà (dopo aver creato un progetto, fare clic con il pulsante destro del mouse sul nodo del progetto, scegliere **Proprietà**e impostare il **percorso di node. exe**). È possibile usare un'installazione globale di node. js oppure è possibile specificare il percorso di un interprete locale in ogni progetto node. js. 

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa si crea un progetto di applicazione Web Node.js.

1. Se il runtime di Node.js non è già installato, installare la versione LTS dal sito Web [Node.js](https://nodejs.org/en/download/).

    Per ulteriori informazioni, vedere i prerequisiti.

1. Aprire Visual Studio.

1. Creare un nuovo progetto.

    ::: moniker range=">=vs-2019"
    Premere **ESC** per chiudere la finestra iniziale. Premere **CTRL+Q** per aprire la casella di ricerca, digitare **Node.js**, quindi scegliere **Create new Blank Node.js Web application project** (Crea nuovo progetto applicazione Web Node.js vuoto) (JavaScript). Nella finestra di dialogo visualizzata scegliere **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **JavaScript**, quindi scegliere **Node.js**. Nel riquadro centrale scegliere **Applicazione Web Node.js vuota**, quindi scegliere **OK**.
    ::: moniker-end
    Se il modello di progetto **Applicazione Web Node.js vuota** non compare, è necessario installare prima il carico di lavoro **Sviluppo Node.js**. Per istruzioni dettagliate, vedere i [Prerequisiti](#prerequisites).

    Visual Studio crea la nuova soluzione e apre il progetto. Nell'editor nel riquadro sinistro si apre *server.js*.

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

## <a name="run-the-application"></a>Eseguire l'applicazione

1. Premere **Ctrl**+**F5** (o scegliere **Debug > Avvia senza eseguire debug**) per eseguire l'applicazione. L'app verrà aperta in un browser.

1. Nella finestra del browser viene visualizzato "Hello World" e il numero della porta locale.

1. Chiudere il Web browser.

È stata completata la Guida introduttiva che ha fornito una panoramica dell'IDE di Visual Studio e di Node.js. Se si vuole approfondire la conoscenza relativa alle funzionalità, scegliere un'esercitazione nella sezione del sommario relativa alle **esercitazioni**.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Distribuire l'app nel Servizio app di Linux](../javascript/publish-nodejs-app-azure.md)

- [Tutorial for Node.js and Express](../javascript/tutorial-nodejs.md) (Esercitazione per Node.js ed Express)
- [Tutorial for Node.js and React](../javascript/tutorial-nodejs-with-react-and-jsx.md) (Esercitazione per Node.js e React)