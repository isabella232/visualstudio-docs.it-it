---
title: "Esercitazione su Docker - Parte 2: Compilare ed eseguire l'app di esempio todo list"
description: Panoramica dell'app di esempio todo list eseguita in Node.js.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: a80358f74d949eb10686004466d91a8116101a1f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122053475"
---
# <a name="build-and-run-the-todo-sample-app"></a>Compilare ed eseguire l'app di esempio todo

>[!NOTE]
> Questa è una continuazione di un'esercitazione che inizia [qui](docker-tutorial.md)

Per il resto di questa esercitazione, si lavora con un semplice gestore di elenchi attività in esecuzione in Node.js. Se non si ha familiarità con Node.js, non è necessario preoccuparsi. Non è necessaria alcuna esperienza JavaScript reale.

A questo punto, il team di sviluppo è piuttosto piccolo e si sta semplicemente creando un'app per dimostrare il proprio MVP (prodotto con validità minima). Si vuole mostrare come funziona e cosa è in grado di fare senza dover pensare a come funzionerà per un team di grandi dimensioni, più sviluppatori e così via.

![Todo List Manager Screenshot](media/todo-list-sample.png)

## <a name="get-the-app"></a>Scaricare l'app

Prima di poter eseguire l'applicazione, è necessario ottenere il codice sorgente dell'applicazione nel computer. Per i progetti reali, in genere si clona il repo. Tuttavia, per questa esercitazione è stato creato un file ZIP contenente l'applicazione.

1. Se si usa Windows, assicurarsi di avere installato Docker per Windows o Docker Community Edition nel computer locale. Vedere [Docker per la Windows di installazione.](https://docs.docker.com/docker-for-windows/install/) Il processo di installazione rende disponibile il file ZIP contenente l'esempio all'indirizzo localhost. Per Mac, installare [Docker Desktop per Mac.](https://docs.docker.com/docker-for-mac/install/)

1. Scaricare l'origine per l'app dal repo [Docker.](https://github.com/docker/getting-started) È possibile scaricare il file ZIP per il repo. Per scaricare il file ZIP, usare il pulsante **Codice** verde e scegliere **Scarica ZIP.** Aprire il file ZIP ed Estrai tutto per estrarre l'origine dell'app dalla cartella *dell'app* in una cartella sul disco rigido.

   ![Screenshot che mostra il pulsante Codice verde e l'opzione Scarica ZIP](media/download-zip.png)

1. Dopo l'estrazione, usare l'editor di codice preferito per aprire il progetto. Se si ha bisogno di un editor, è possibile [usare](https://code.visualstudio.com/)Visual Studio Code . Dovrebbero essere visualizzati i due sottodirectory e `package.json` ( e `src` `spec` ).

    ![Screenshot della Visual Studio Code aperta con l'app caricata](media/ide-screenshot.png)

## <a name="building-the-apps-container-image"></a>Creazione dell'immagine del contenitore dell'app

Per compilare l'applicazione, è necessario usare `Dockerfile` . Un Dockerfile è semplicemente uno script basato su testo di istruzioni che viene usato per creare un'immagine del contenitore. Se Dockerfiles è stato creato in precedenza, potrebbero verificarsi alcuni difetti nel Dockerfile seguente. Ma non è un problema. Verranno trattate.

1. Creare un file `Dockerfile` denominato nella stessa cartella del file con il contenuto `package.json` seguente.

    ```dockerfile
    FROM node:12-alpine
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "/app/src/index.js"]
    ```

    Verificare che il file `Dockerfile` non abbia un'estensione come `.txt` . Alcuni editor possono aggiungere automaticamente questa estensione di file e questo genera un errore nel passaggio successivo.

1. Se non è già stato fatto, aprire un terminale e passare alla `app` directory con `Dockerfile` . Compilare ora l'immagine del contenitore usando il `docker build` comando .

    ```bash
    docker build -t getting-started .
    ```

    In alternativa, è anche possibile fare clic con il pulsante destro del mouse sul Dockerfile e scegliere Compila immagine **e** quindi specificare il tag al prompt.

    Questo comando ha usato Dockerfile per compilare una nuova immagine del contenitore. Si potrebbe notare che sono stati scaricati molti "livelli". Questo perché è stato indicato al generatore che si desidera iniziare `node:12-alpine` dall'immagine. Tuttavia, dal momento che non si disponeva di tale immagine nel computer, era necessario scaricare l'immagine.

    Dopo aver scaricato l'immagine, è stata copiata nell'applicazione e usata per installare le `yarn` dipendenze dell'applicazione. La `CMD` direttiva specifica il comando predefinito da eseguire quando si avvia un contenitore da questa immagine.

    Infine, il `-t` flag contrassegna l'immagine. Si pensi semplicemente a un nome leggibile dall'utente per l'immagine finale. Poiché l'immagine è stata denominata `getting-started` , è possibile fare riferimento a tale immagine quando si esegue un contenitore.

    Alla `.` fine del comando indica che `docker build` Docker deve cercare nella directory `Dockerfile` corrente.

## <a name="starting-an-app-container"></a>Avvio di un contenitore di app

Ora che si dispone di un'immagine, eseguire l'applicazione. A tale scopo, usare il `docker run` comando (ricordarlo in precedenza?).

1. Avviare il contenitore usando `docker run` il comando e specificare il nome dell'immagine appena creata:

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

    Si ricordano `-d` i `-p` flag e ? Si esegue il nuovo contenitore in modalità "scollegato" (in background) e si crea un mapping tra la porta 3000 dell'host e la porta 3000 del contenitore. Senza il mapping delle porte, non sarebbe possibile accedere all'applicazione.

1. Dopo alcuni secondi, aprire il Web browser in [http://localhost:3000](http://localhost:3000) .
    Verrà visualizzata l'app.

    ![Elenco attività vuoto](media/todo-list-empty.png)

1. Procedere e aggiungere uno o due elementi e verificare che funzioni come previsto. È possibile contrassegnare gli elementi come completi e rimuovere gli elementi. Il front-end sta archiviando correttamente gli elementi nel back-end. Piuttosto veloce e facile, eh?

A questo punto, dovrebbe essere presente un gestore di elenchi attività in esecuzione con alcuni elementi, tutti creati dall'utente. A questo punto, apportare alcune modifiche e informazioni sulla gestione dei contenitori.

Se si osserva rapidamente l'estensione VS Code, i due contenitori dovrebbero essere in esecuzione ora (questa esercitazione e il contenitore di app appena avviato).

![Estensione Docker con esercitazione e contenitori di app in esecuzione](media/vs-two-containers.png)

## <a name="recap"></a>Riepilogo

In questa breve sezione sono state apprese le nozioni di base sulla creazione di un'immagine del contenitore e si è creato un Dockerfile a tale scopo. Dopo aver creato un'immagine, è stato avviato il contenitore e è stata visualizzata l'app in esecuzione.

Successivamente, si apprenderà come apportare una modifica all'app e come aggiornare l'applicazione in esecuzione con una nuova immagine. Lungo il percorso, si apprenderanno alcuni altri comandi utili.

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Aggiornamento dell'app](update-your-app.md)
