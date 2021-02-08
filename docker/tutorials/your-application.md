---
title: "Esercitazione su Docker-parte 1: compilare ed eseguire l'app di esempio todo list"
description: Panoramica dell'app di esempio todo list eseguita in Node.js.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: f5f5fdd51e4aa13df66470534303f7fba19e44ab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841666"
---
# <a name="build-and-run-the-todo-sample-app"></a>Compilare ed eseguire l'app di esempio TODO

Nella parte restante di questa esercitazione verrà usato un semplice gestore elenco attività in esecuzione in Node.js. Se non si ha familiarità con Node.js, non ci si deve preoccupare. Non è necessaria alcuna esperienza JavaScript reale.

A questo punto, il team di sviluppo è piuttosto piccolo e si sta semplicemente creando un'app per dimostrare il proprio MVP (il prodotto è minimo possibile). Si vuole illustrare il funzionamento e il modo in cui è in grado di eseguire questa operazione senza dover pensare a come funzionerà per un team di grandi dimensioni, più sviluppatori e così via.

![Schermata di gestione elenco TODO](media/todo-list-sample.png)

## <a name="get-the-app"></a>Scaricare l'app

Prima di poter eseguire l'applicazione, è necessario ottenere il codice sorgente dell'applicazione nel computer. Per i progetti reali, in genere il repository viene clonato. Tuttavia, per questa esercitazione è stato creato un file ZIP che contiene l'applicazione.

1. Verificare che nel computer locale sia installato Docker per Windows o Docker Community Edition. Vedere la [documentazione relativa all'installazione di Docker per Windows](https://docs.docker.com/docker-for-windows/install/). Il processo di installazione rende disponibile il file ZIP contenente l'esempio nell'indirizzo localhost.

1. [Scaricare il file zip](http://localhost/assets/app.zip). Aprire il file ZIP e assicurarsi di estrarre il contenuto.

1. Al termine dell'estrazione, usare l'editor di codice preferito per aprire il progetto. Se è necessario un editor, è possibile usare [Visual Studio Code](https://code.visualstudio.com/). Verranno visualizzate le `package.json` due sottodirectory e `src` `spec` .

    ![Screenshot dei Visual Studio Code aperti con l'app caricata](media/ide-screenshot.png)

## <a name="building-the-apps-container-image"></a>Compilazione dell'immagine del contenitore dell'app

Per compilare l'applicazione, è necessario usare un `Dockerfile` . Un Dockerfile è semplicemente uno script basato su testo di istruzioni che viene usato per creare un'immagine del contenitore. Se è stato creato Dockerfile in precedenza, è possibile che vengano visualizzati alcuni difetti nel Dockerfile di seguito. Ma non preoccuparti. Verranno esaminati.

1. Creare un file denominato `Dockerfile` nella stessa cartella del file `package.json` con il contenuto seguente.

    ```dockerfile
    FROM node:12-alpine
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "/app/src/index.js"]
    ```

    Verificare che l'estensione del file `Dockerfile` non sia simile a `.txt` . Alcuni editor possono aggiungere automaticamente questa estensione di file e questo genera un errore nel passaggio successivo.

1. Se non è già stato fatto, aprire un terminale e passare alla `app` Directory con il `Dockerfile` . A questo punto, compilare l'immagine del contenitore usando il `docker build` comando.

    ```bash
    docker build -t getting-started .
    ```

    In alternativa, è anche possibile fare clic con il pulsante destro del mouse su Dockerfile e scegliere **Compila immagine...** e quindi specificare il tag al prompt.

    Questo comando usava Dockerfile per creare una nuova immagine contenitore. Si potrebbe notare che sono stati scaricati numerosi "livelli". Questo perché è stato indicato al generatore che si desiderava iniziare dall' `node:12-alpine` immagine. Tuttavia, poiché il computer non è stato installato, è necessario scaricare l'immagine.

    Dopo che l'immagine è stata scaricata, copiata nell'applicazione e usata `yarn` per installare le dipendenze dell'applicazione. La `CMD` direttiva specifica il comando predefinito da eseguire quando si avvia un contenitore da questa immagine.

    Infine, il `-t` flag contrassegna l'immagine. È sufficiente considerarlo come nome leggibile per l'immagine finale. Poiché l'immagine è stata denominata `getting-started` , è possibile fare riferimento a tale immagine quando si esegue un contenitore.

    Alla `.` fine del `docker build` comando indica che Docker deve cercare `Dockerfile` nella directory corrente.

## <a name="starting-an-app-container"></a>Avvio di un contenitore di app

Ora che si dispone di un'immagine, eseguire l'applicazione. A tale scopo, utilizzare il `docker run` comando (tenere presente che dal precedente?).

1. Avviare il contenitore usando il `docker run` comando e specificare il nome dell'immagine appena creata:

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

    Ricordare i `-d` `-p` flag e? Il nuovo contenitore viene eseguito in modalità "scollegata" (in background) e viene creato un mapping tra la porta 3000 dell'host e la porta 3000 del contenitore. Senza il mapping delle porte, non sarà possibile accedere all'applicazione.

1. Dopo alcuni secondi, aprire il Web browser a [http://localhost:3000](http://localhost:3000) .
    Verrà visualizzata l'app.

    ![Elenco TODO vuoto](media/todo-list-empty.png)

1. Procedere con l'aggiunta di un elemento o due per verificare che funzioni come previsto. È possibile contrassegnare gli elementi come completati e rimuovere gli elementi. Il front-end archivia correttamente gli elementi nel back-end. Piuttosto veloce e facile, eh?

A questo punto, è necessario disporre di un gestore elenco attività in esecuzione con pochi elementi, tutti compilati dall'utente. Verranno ora apportate alcune modifiche e verranno fornite informazioni sulla gestione dei contenitori.

Se si esamina rapidamente l'estensione VS Code, dovrebbero essere visualizzati i due contenitori in esecuzione (questa esercitazione e il contenitore di app appena lanciato).

![Estensione Docker con esercitazione e contenitori di app in esecuzione](media/vs-two-containers.png)

## <a name="recap"></a>Riepilogo

In questa breve sezione sono state apprese le nozioni di base sulla creazione di un'immagine del contenitore e la creazione di un Dockerfile a tale scopo. Una volta creata un'immagine, il contenitore è stato avviato e l'app in esecuzione è stata avviata.

Successivamente, si apprenderà una modifica all'app e si apprenderà come aggiornare l'applicazione in esecuzione con una nuova immagine. Verranno illustrati alcuni altri comandi utili.

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Aggiornamento dell'app](update-your-app.md)
