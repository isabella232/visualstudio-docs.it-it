---
title: Creare la prima app Node.js app
ms.custom:
- vs-acquisition
- SEO-VS-2020
description: In questa guida introduttiva verrà creata un'app Node.js in Visual Studio
ms.date: 09/14/2021
ms.technology: vs-javascript
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: fceecc9110a0ae15edf4d702e5c4db19cf129905
ms.sourcegitcommit: 559c662b2d60048300b76ea6ed3defaa2a259492
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/15/2021
ms.locfileid: "127779673"
---
# <a name="quickstart-create-your-first-nodejs-app-with-visual-studio"></a>Guida introduttiva: Creare la prima app Node.js con Visual Studio

In questa introduzione di 5-10 minuti all'ambiente Visual Studio di sviluppo integrato (IDE, Integrated Development Environment) viene creata una semplice Node.js'app Web.

## <a name="prerequisites"></a>Prerequisiti

Prima di iniziare, installare Visual Studio e configurare l'Node.js virtuale.

::: moniker range=">=vs-2022"
### <a name="install-visual-studio-and-the-nodejs-workload"></a>Installare Visual Studio e il carico Node.js lavoro

Se non è ancora stato installato Visual Studio:

1. Passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installare Visual Studio 2022 gratuitamente.

1. Nel Programma di installazione di Visual Studio selezionare il carico di **Node.js sviluppo** e selezionare **Installa.**

   ![Screenshot che mostra il carico di lavoro Node j s selezionato nel Programma di installazione di Visual Studio.](../ide/media/quickstart-nodejs-workload.png)

Se è già Visual Studio installato.

1. In Visual Studio passare a **Strumenti** > **Ottieni strumenti e funzionalità.**

1. Nella finestra Programma di installazione di Visual Studio scegliere il carico **di lavoroNode.js sviluppo** e selezionare Modifica per scaricare e installare il carico di lavoro. 

### <a name="set-up-your-nodejs-environment"></a>Configurare l'ambiente Node.js

[Installare la versione LTS del runtime Node.js .](https://nodejs.org/en/download/) La versione LTS offre la migliore compatibilità con altri framework e librerie.

Sebbene Node.js sia compilato per architetture a 32 bit e a 64 bit, il programma di installazione Node.js supporta solo una versione alla volta.

Visual Studio in genere rileva il runtime installato, ma in caso contrario, è possibile configurare il progetto per fare riferimento al runtime installato:

   1. Dopo [aver creato il progetto,](#create-your-app-project)fare clic con il pulsante destro del mouse sul nodo del progetto.

   1. Selezionare **Proprietà** e impostare il **percorsoNode.exe.** È possibile usare un'installazione Node.js globale o specificare il percorso di un interprete locale per qualsiasi Node.js progetto.

:::moniker-end
::: moniker range="vs-2019"
### <a name="install-visual-studio"></a>Installare Visual Studio

Se non è ancora stato installato Visual Studio 2019, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.
::: moniker-end
::: moniker range="vs-2017"
### <a name="install-visual-studio"></a>Installare Visual Studio

Se Visual Studio 2017 non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.
::: moniker-end

::: moniker range="<=vs-2019"
### <a name="set-up-your-nodejs-environment"></a>Configurare l'ambiente Node.js

Visual Studio consente di configurare l'ambiente, inclusa l'installazione di strumenti comuni con Node.js sviluppo.

1. In Visual Studio passare a **Strumenti** > **Ottieni strumenti e funzionalità.**

1. Nel Programma di installazione di Visual Studio scegliere il carico di **lavoroNode.js sviluppo** e selezionare **Modifica** per scaricare e installare il carico di lavoro.

    ![Screenshot che mostra il carico di lavoro Node J S selezionato nel Programma di installazione di Visual Studio.](../ide/media/quickstart-nodejs-workload.png)

1. Installare la versione LTS del [ runtimeNode.js](https://nodejs.org/en/download/). È consigliabile usare la versione LTS per una migliore compatibilità con framework e librerie esterni.

    Anche Node.js è compilato per architetture a 32 bit e a 64 bit, il programma di installazione di Node.js supporta solo una versione installata alla volta.

1. Se Visual Studio non rileva il runtime installato (in genere), configurare il progetto in modo che punti al runtime installato:

   1. Dopo aver creato [il progetto ,](#create-your-app-project)fare clic con il pulsante destro del mouse sul nodo del progetto.

   1. Selezionare **Proprietà** e impostare il **Node.exe percorso .** È possibile usare un'installazione globale di Node.js o specificare il percorso di un interprete locale in ogni progetto Node.js progetto.

::: moniker-end
## <a name="create-your-app-project"></a>Creare il progetto di app

In Visual Studio creare un nuovo Node.js progetto.

::: moniker range=">=vs-2022"

1. Avviare Visual Studio e quindi premere **ESC** per chiudere la finestra iniziale.

1. Premere **CTRL** + **Q** e  quindi digitarenode.jsnella casella di ricerca.

1. Selezionare **Blank Node.js Web Application (Applicazione Web vuota).**

1. Nella finestra di dialogo selezionare **Crea**.

::: moniker-end

::: moniker range="vs-2019"

1. Premere **ESC** per chiudere la finestra iniziale.

1. Premere **CTRL+Q** per aprire la casella di ricerca, quindi **digitareNode.js**.

1. Scegliere **Vuoto Node.js'applicazione Web (JavaScript).** Nella finestra di dialogo selezionare **Crea.**

::: moniker-end

::: moniker range="vs-2017"
1. Nella barra dei menu superiore scegliere **File** > **Nuovo** > **Project**.

1. Nel riquadro sinistro della finestra **di dialogo Project,** espandere **JavaScript** e scegliere **Node.js**.

1. Nel riquadro centrale scegliere Blank **(Vuoto) Node.js Web application (Applicazione Web)** e selezionare **OK.**

::: moniker-end
Visual Studio crea e apre il progetto. Il file di *server.js* del progetto viene aperto nell'editor.

Se il modello di progetto Applicazione **Web Node.js** vuoto non è visualizzato, è necessario aggiungere il carico di **lavoro** sviluppoNode.js distribuzione. Per istruzioni, vedere [Prerequisiti.](#prerequisites)

## <a name="explore-the-ide"></a>Esplorare l'IDE

::: moniker range=">=vs-2022"
Visual Studio consente di configurare l'ambiente, inclusa l'installazione di strumenti comuni con Node.js sviluppo.

1. Nel riquadro destro esaminare il Esplora soluzioni **.**
   
   - Al livello superiore è disponibile *una soluzione*, che per impostazione predefinita ha lo stesso nome del progetto. Una soluzione, rappresentata da un file *con estensione sln* su disco, è un contenitore per uno o più progetti correlati.
   - Il progetto, con il nome usato al momento della configurazione, è evidenziato in grassetto. Su disco, il progetto è rappresentato da un file con estensione *njsproj* nella cartella del progetto.
   - Il **nodo npm** mostra i pacchetti npm installati. È possibile fare clic con il pulsante destro del mouse sul nodo **npm** per cercare e installare i pacchetti npm usando una finestra di dialogo.

   ![Screenshot che mostra il Esplora soluzioni dettagli.](../ide/media/vs-2022/quickstart-nodejs-solution-explorer.png)

1. Per installare i pacchetti npm o Node.js comandi da un prompt dei comandi, fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Apri prompt dei comandi qui.**

   ![Screenshot che mostra Apri prompt dei comandi qui nel menu di scelta rapida del progetto.](../ide/media/vs-2022/quickstart-nodejs-command-prompt.png)

1. Per testare la navigazione nel codice sorgente, nel file *server.js* aperto selezionare e premere F12 oppure fare clic con il pulsante destro del mouse e scegliere Vai a `createServer` definizione dal menu di scelta  `createServer` rapida.  Questo comando consente di accedere alla definizione della `createServer` funzione in *http.d.ts*.

   ![Screenshot che mostra Vai a definizione nel menu di scelta rapida createServer.](../ide/media/vs-2022/quickstart-nodejs-go-to-definition.png)

1. Tornare a *server.js*, individuare questa riga di codice: `res.end('Hello World\n');` e modificarla in:

   `res.end('Hello World\n' + res.connection.`

   Quando si digita `connection.` , IntelliSense fornisce opzioni per il completamento automatico della voce di codice.

   ![Screenshot che mostra le opzioni di completamento automatico di IntelliSense.](../ide/media/vs-2022/quickstart-nodejs-intellisense.png)

1. Scegliere `localPort` e digitare per `);` completare l'istruzione:

    `res.end('Hello World\n' + res.connection.localPort);`

::: moniker-end

::: moniker range="<=vs-2019"
1. Nel riquadro destro esaminare il Esplora soluzioni **.**
   
   - Al livello superiore è disponibile *una soluzione*, che per impostazione predefinita ha lo stesso nome del progetto. Una soluzione, rappresentata da un file *con estensione sln* su disco, è un contenitore per uno o più progetti correlati.
   - Il progetto, con il nome usato al momento della configurazione, è evidenziato in grassetto. Su disco, il progetto è rappresentato da un file con estensione *njsproj* nella cartella del progetto.
   - Il **nodo npm** mostra i pacchetti npm installati. È possibile fare clic con il pulsante destro del mouse sul nodo **npm** per cercare e installare i pacchetti npm usando una finestra di dialogo.

   ![Screenshot che mostra il Esplora soluzioni dettagli.](../ide/media/quickstart-nodejs-solution-explorer.png)

1. Per installare i pacchetti npm o Node.js comandi da un prompt dei comandi, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Apri prompt** dei comandi qui dal menu di scelta rapida.

   ![Screenshot che mostra Apri prompt dei comandi qui nel menu di scelta rapida del progetto.](../ide/media/quickstart-nodejs-command-prompt.png)

1. Per testare la navigazione nel codice sorgente, nel file *server.js* aperto selezionare **http.createServer** e premere **F12** oppure scegliere **Vai** a definizione dal menu di scelta rapida. Questo comando consente di accedere alla definizione della `createServer` funzione in *http.d.ts*.

   ![Screenshot che mostra Vai a definizione nel menu di scelta rapida createServer.](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Tornare a *server.js*, individuare questa riga di codice: `res.end('Hello World\n');` e modificarla in:

   `res.end('Hello World\n' + res.connection.`

   Quando si digita **connection.**, IntelliSense fornisce opzioni per il completamento automatico della voce di codice.

   ![Screenshot che mostra le opzioni di completamento automatico di IntelliSense.](../ide/media/quickstart-nodejs-intellisense.png)

1. Scegliere **localPort** e digitare per `);` completare l'istruzione:

    `res.end('Hello World\n' + res.connection.localPort);`
:::moniker-end

## <a name="run-the-app"></a>Eseguire l'app

1. Premere **CTRL** + **F5 o** selezionare **Debug** Avvia senza eseguire  >  **debug** per eseguire l'app.
 
   L'app viene aperta in un browser.

1. Nel browser verificare che sia visualizzato un messaggio Hello World **e** il numero di porta locale.

Congratulazioni! È stata creata una semplice app Node.js con Visual Studio. Per approfondire la conoscenza, passare alla **sezione Esercitazioni** del sommario.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Distribuire l'app nel servizio app di Linux](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [Tutorial for Node.js and Express](../javascript/tutorial-nodejs.md) (Esercitazione per Node.js ed Express)

> [!div class="nextstepaction"]
> [Tutorial for Node.js and React](../javascript/tutorial-nodejs-with-react-and-jsx.md) (Esercitazione per Node.js e React)

