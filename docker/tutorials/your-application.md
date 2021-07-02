---
title: "Esercitazione su Docker - Parte 1: Compilare ed eseguire l'app di esempio todo list"
description: Panoramica dell'app di esempio todo list eseguita in Node.js.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 9229c3717b686a3f08ef49e7912ac0515864d793
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222812"
---
# <a name="build-and-run-the-todo-sample-app"></a>Compilare ed eseguire l'app di esempio todo

Per il resto di questa esercitazione, verrà utilizzato un semplice gestore di elenchi attività in esecuzione in Node.js. Se non si ha familiarità con Node.js, non c'è da preoccuparsi. Non è necessaria alcuna esperienza JavaScript reale.

A questo punto, il team di sviluppo è piuttosto piccolo e si sta semplicemente creando un'app per dimostrare l'MVP (prodotto minimo fattibile). Si vuole illustrare il funzionamento e le operazioni che può eseguire senza dover pensare al suo funzionamento per un team di grandi dimensioni, più sviluppatori e così via.

![Todo List Manager Screenshot](media/todo-list-sample.png)

## <a name="get-the-app"></a>Scaricare l'app

Prima di poter eseguire l'applicazione, è necessario ottenere il codice sorgente dell'applicazione nel computer. Per i progetti reali, in genere si clona il repo. Tuttavia, per questa esercitazione è stato creato un file ZIP contenente l'applicazione.

1. Assicurarsi di avere installato Docker per Windows o Docker Community Edition nel computer locale. Vedere [Docker per la documentazione Windows installazione.](https://docs.docker.com/docker-for-windows/install/) Il processo di installazione rende disponibile il file ZIP contenente l'esempio all'indirizzo localhost.

1. Scaricare l'origine per l'app dal repo [Docker.](https://github.com/docker/getting-started) È possibile scaricare il file ZIP per il repo. Per scaricare il file ZIP, usare il pulsante **Codice** verde e scegliere **Scarica ZIP.** Aprire il file ZIP ed Estrai tutto per estrarre l'origine dell'app dalla cartella *dell'app* in una cartella sul disco rigido.

   ![Screenshot che mostra il pulsante Codice verde e l'opzione Scarica ZIP](media/download-zip.png)

1. Dopo l'estrazione, usare l'editor di codice preferito per aprire il progetto. Se è necessario un editor, è possibile usare [Visual Studio Code](https://code.visualstudio.com/). Dovrebbero essere visualizzati `package.json` e due sottodirectory ( `src` e `spec` ).

    ![Screenshot della Visual Studio Code aperta con l'app caricata](media/ide-screenshot.png)

## <a name="building-the-apps-container-image"></a>Creazione dell'immagine del contenitore dell'app

Per compilare l'applicazione, è necessario usare un oggetto `Dockerfile` . Un Dockerfile è semplicemente uno script di istruzioni basato su testo usato per creare un'immagine del contenitore. Se i Dockerfile sono stati creati in precedenza, potrebbero verificarsi alcuni difetti nel Dockerfile seguente. Ma non c'è da preoccuparsi. Verranno trattate.

1. Creare un file `Dockerfile` denominato nella stessa cartella del file con il contenuto `package.json` seguente.

    ```dockerfile
    FROM node:12-alpine
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "/app/src/index.js"]
    ```

    Verificare che il file non `Dockerfile` abbia un'estensione come `.txt` . Alcuni editor possono aggiungere automaticamente questa estensione di file e questo genera un errore nel passaggio successivo.

1. Se non è già stato fatto, aprire un terminale e passare alla `app` directory con `Dockerfile` . Compilare ora l'immagine del contenitore usando il `docker build` comando .

    ```bash
    docker build -t getting-started .
    ```

    In alternativa, è anche possibile fare clic con il pulsante destro del mouse sul Dockerfile e scegliere **Build Image (Compila immagine)** e quindi specificare il tag al prompt.

    Questo comando ha usato il Dockerfile per creare una nuova immagine del contenitore. Si sarà notato che sono stati scaricati molti "livelli". Questo perché è stato indicato al generatore che si vuole iniziare `node:12-alpine` dall'immagine. Tuttavia, poiché non è stato installato nel computer, l'immagine deve essere scaricata.

    Dopo aver scaricato l'immagine, è stata copiata nell'applicazione e usata `yarn` per installare le dipendenze dell'applicazione. La `CMD` direttiva specifica il comando predefinito da eseguire quando si avvia un contenitore da questa immagine.

    Infine, il `-t` flag contrassegna l'immagine. Si pensi semplicemente a un nome leggibile per l'immagine finale. Poiché l'immagine è stata `getting-started` denominata , è possibile fare riferimento a tale immagine quando si esegue un contenitore.

    Alla `.` fine del comando indica che `docker build` Docker deve cercare nella directory `Dockerfile` corrente.

## <a name="starting-an-app-container"></a>Avvio di un contenitore di app

Ora che è disponibile un'immagine, eseguire l'applicazione. A tale scopo, usare il `docker run` comando (ricordarlo in precedenza?).

1. Avviare il contenitore usando `docker run` il comando e specificare il nome dell'immagine appena creata:

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

    Si ricordano `-d` i `-p` flag e ? Si esegue il nuovo contenitore in modalità "scollegato" (in background) e si crea un mapping tra la porta 3000 dell'host e la porta 3000 del contenitore. Senza il mapping delle porte, non sarebbe possibile accedere all'applicazione.

1. Dopo alcuni secondi, aprire il Web browser su [http://localhost:3000](http://localhost:3000) .
    Dovrebbe essere visualizzata l'app.

    ![Elenco attività vuoto](media/todo-list-empty.png)

1. Procedere e aggiungere uno o due elementi e verificare che funzioni come previsto. È possibile contrassegnare gli elementi come completi e rimuovere gli elementi. Il front-end sta archiviando correttamente gli elementi nel back-end. È piuttosto veloce e semplice, ma?

A questo punto, dovrebbe essere presente un gestore di elenchi attività in esecuzione con alcuni elementi, tutti creati dall'utente. A questo punto, apportare alcune modifiche e apprendere come gestire i contenitori.

Se si osserva rapidamente l'estensione VS Code, i due contenitori dovrebbero essere in esecuzione ora (questa esercitazione e il contenitore di app appena avviato).

![Estensione Docker con esercitazione e contenitori di app in esecuzione](media/vs-two-containers.png)

## <a name="recap"></a>Riepilogo

In questa breve sezione sono state apprese le nozioni di base sulla creazione di un'immagine del contenitore e si è creato un Dockerfile a tale scopo. Dopo aver creato un'immagine, è stato avviato il contenitore ed è stata visualizzata l'app in esecuzione.

Successivamente, si apprenderà come apportare una modifica all'app e come aggiornare l'applicazione in esecuzione con una nuova immagine. Lungo il percorso si apprenderanno alcuni altri comandi utili.

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Aggiornamento dell'app](update-your-app.md)
