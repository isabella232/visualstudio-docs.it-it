---
title: "Esercitazione su Docker-parte 2: aggiornare l'app"
description: Viene descritto come aggiornare un'app docker.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 4a1cba71481608803522336ad5c0f6b6354bca32
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "89178340"
---
# <a name="update-the-app"></a>Aggiornare l'app

Una piccola richiesta di funzionalità è stata richiesta dal team del prodotto per modificare il testo vuoto quando non sono presenti elementi elenco todo. Si desidera eseguire la transizione a quanto segue:

> Non sono ancora presenti elementi todo. Aggiungerne uno sopra.

Abbastanza semplice, giusto? Facciamo la modifica.

## <a name="update-the-source-code"></a>Aggiornare il codice sorgente

1. Nel `src/static/js/app.js` file aggiornare la riga 56 per usare il nuovo testo vuoto.

    ```diff
    -                <p className="text-center">No items yet! Add one above!</p>
    +                <p className="text-center">You have no todo items yet! Add one above!</p>
    ```

1. Compilare la versione aggiornata dell'immagine, usando lo stesso comando usato in precedenza.

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

Cosa è successo? Non è stato possibile avviare il nuovo contenitore perché il contenitore precedente è ancora in esecuzione. Il motivo di questo problema è che il contenitore usa la porta 3000 dell'host e un solo processo nel computer (contenitori inclusi) può restare in ascolto di una porta specifica. Per risolvere il problema, rimuovere il contenitore precedente.

## <a name="replace-the-old-container"></a>Sostituire il contenitore precedente

Per rimuovere un contenitore, è prima necessario arrestarlo. Una volta arrestato, è possibile rimuoverlo. È possibile rimuovere il contenitore precedente in due modi. È possibile scegliere il percorso con cui si è più sicuri.

### <a name="remove-a-container-using-the-cli"></a>Rimuovere un contenitore usando l'interfaccia della riga di comando

1. Ottenere l'ID del contenitore usando il `docker ps` comando.

    ```bash
    docker ps
    ```

1. Usare il `docker stop` comando per arrestare il contenitore.

    ```bash
    # Swap out <the-container-id> with the ID from docker ps
    docker stop <the-container-id>
    ```

1. Una volta arrestato il contenitore, è possibile rimuoverlo utilizzando il `docker rm` comando.

    ```bash
    docker rm <the-container-id>
    ```

> [!TIP]
> È possibile arrestare e rimuovere un contenitore in un singolo comando aggiungendo il flag "Force" al `docker rm` comando. Ad esempio: `docker rm -f <the-container-id>`

### <a name="remove-a-container-using-the-docker-dashboard"></a>Rimuovere un contenitore usando il dashboard Docker

Se si apre l'estensione VS Code, è possibile rimuovere un contenitore con due clic. È certamente molto più semplice che cercare l'ID del contenitore e rimuoverlo.

1. Con l'estensione aperta, passare al contenitore e fare clic con il pulsante destro del mouse.

1. Fare clic sull'opzione **Rimuovi** .

1. Confermare la rimozione e l'operazione è terminata.

![Dashboard Docker-rimozione di un contenitore](media/vs-removing-container.png)

### <a name="start-the-updated-app-container"></a>Avvia il contenitore dell'app aggiornato

1. A questo punto, avviare l'app aggiornata.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

1. Aggiornare il browser in [http://localhost:3000](http://localhost:3000) e dovrebbe essere visualizzato il testo della Guida aggiornato.

![Applicazione aggiornata con testo vuoto aggiornato](media/todo-list-updated-empty-text.png)

## <a name="recap"></a>Riepilogo

Sebbene sia possibile creare un aggiornamento, è possibile che si siano verificati due aspetti:

- Tutti gli elementi esistenti nell'elenco TODO sono finiti. Non è un'app molto interessante. A breve parleremo di questo.
- Per una modifica di questo tipo sono stati necessari *numerosi* passaggi. In una sezione successiva si apprenderà come visualizzare gli aggiornamenti del codice senza dover ricompilare e avviare un nuovo contenitore ogni volta che si effettua una modifica.

Prima di acquisire familiarità con la persistenza, si vedrà rapidamente come condividere tali immagini con altri utenti.

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Condivisione dell'app](share-your-app.md)
