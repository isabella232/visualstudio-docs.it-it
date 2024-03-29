---
title: "Esercitazione su Docker - Parte 3: Aggiornare l'app"
description: Descrive come aggiornare un'app Docker.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.custom: contperf-fy22q1
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 0ce798b3264eedea5826df0ca2076c7fbc6ee4c6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633452"
---
# <a name="update-the-app"></a>Aggiornare l'app

Come richiesta di funzionalità di piccole dimensioni, il team del prodotto ha chiesto di modificare il "testo vuoto" quando non sono presenti elementi dell'elenco attività. L'utente vuole eseguire la transizione a quanto segue:

> Non sono ancora presenti elementi todo. Aggiungerne uno sopra.

È piuttosto semplice, vero? Apportare la modifica.

## <a name="update-the-source-code"></a>Aggiornare il codice sorgente

1. Nel `src/static/js/app.js` file aggiornare la riga 56 per usare il nuovo testo vuoto.

    ```diff
    -                <p className="text-center">No items yet! Add one above!</p>
    +                <p className="text-center">You have no todo items yet! Add one above!</p>
    ```

1. Compilare la versione aggiornata dell'immagine usando lo stesso comando usato in precedenza.

    ```bash
    docker build -t getting-started .
    ```

1. Avviare un nuovo contenitore usando il codice aggiornato.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

**Non è** Probabilmente è stato visualizzato un errore simile al seguente (gli ID saranno diversi):

```bash
docker: Error response from daemon: driver failed programming external connectivity on endpoint laughing_burnell 
(bb242b2ca4d67eba76e79474fb36bb5125708ebdabd7f45c8eaf16caaabde9dd): Bind for 0.0.0.0:3000 failed: port is already allocated.
```

Che cosa è successo? Non è stato possibile avviare il nuovo contenitore perché il contenitore precedente è ancora in esecuzione. Questo è un problema perché il contenitore usa la porta 3000 dell'host e un solo processo nel computer (contenitori inclusi) può restare in ascolto su una porta specifica. Per risolvere il problema, rimuovere il contenitore precedente.

## <a name="replace-the-old-container"></a>Sostituire il contenitore precedente

Per rimuovere un contenitore, è prima necessario che sia arrestato. Una volta arrestata, può essere rimossa. È possibile rimuovere il contenitore precedente in due modi. È possibile scegliere il percorso con cui si ha maggiore familiarità.

### <a name="remove-a-container-using-the-cli"></a>Rimuovere un contenitore usando l'interfaccia della riga di comando

1. Ottenere l'ID del contenitore usando il `docker ps` comando .

    ```bash
    docker ps
    ```

1. Usare il `docker stop` comando per arrestare il contenitore.

    ```bash
    # Swap out <the-container-id> with the ID from docker ps
    docker stop <the-container-id>
    ```

1. Dopo aver arrestato il contenitore, è possibile rimuoverlo usando il `docker rm` comando .

    ```bash
    docker rm <the-container-id>
    ```

> [!TIP]
> È possibile arrestare e rimuovere un contenitore in un singolo comando aggiungendo il flag "force" al `docker rm` comando. ad esempio `docker rm -f <the-container-id>`

### <a name="remove-a-container-using-the-docker-view"></a>Rimuovere un contenitore usando la visualizzazione Docker

Se si apre l'VS Code, è possibile rimuovere un contenitore con due clic. È certamente molto più semplice che dover cercare l'ID contenitore e rimuoverlo.

1. Con l'estensione aperta, passare al contenitore e fare clic con il pulsante destro del mouse.

1. Fare clic **sull'opzione** Rimuovi.

1. Confermare la rimozione e l'operazione è stata completata.

![Visualizzazione Docker: rimozione di un contenitore](media/vs-removing-container.png)

### <a name="start-the-updated-app-container"></a>Avviare il contenitore di app aggiornato

1. Avviare ora l'app aggiornata.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

1. Aggiornare il browser per [http://localhost:3000](http://localhost:3000) visualizzare il testo della Guida aggiornato.

![Applicazione aggiornata con testo vuoto aggiornato](media/todo-list-updated-empty-text.png)

## <a name="recap"></a>Riepilogo

Anche se è stato possibile compilare un aggiornamento, è possibile notare due aspetti:

- Tutti gli elementi esistenti nell'elenco attività non sono più presenti. Non si tratta di un'app molto utile. Ne parleremo a breve.
- Sono stati *necessari molti* passaggi per una modifica così piccola. In una sezione successiva si apprenderà come visualizzare gli aggiornamenti del codice senza dover ricompilare e avviare un nuovo contenitore ogni volta che si apporta una modifica.

Prima di imparare a conoscere la persistenza, si apprende rapidamente come condividere queste immagini con altri utenti.

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Condivisione dell'app](share-your-app.md)
