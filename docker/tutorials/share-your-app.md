---
title: "Esercitazione su Docker-parte 3: condividere l'app"
description: Descrive come condividere immagini Docker usando il registro di sistema Docker Hub.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 46f91b3bf163f3847492a7727fa72a39908d441c
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2020
ms.locfileid: "89485535"
---
# <a name="share-your-app"></a>Condividere l'app

Ora che è stata creata un'immagine, è possibile condividerla. Per condividere le immagini Docker, è necessario usare un registro docker. Il registro predefinito è Docker Hub ed è il punto in cui provengono tutte le immagini usate.

## <a name="create-a-repo"></a>Creare un repository

Per eseguire il push di un'immagine, è prima di tutto necessario creare un repository nell'hub docker.

1. Passare all' [Hub Docker](https://hub.docker.com) ed eseguire l'accesso se necessario.

1. Fare clic sul pulsante **Crea repository** .

1. Per il nome del repository, usare `getting-started` . Assicurarsi che la visibilità sia `Public` .

1. Fare clic sul pulsante **Crea** .

Se si osserva il lato destro della pagina, verrà visualizzata una sezione denominata **comandi di Docker**. Viene visualizzato un comando di esempio che sarà necessario eseguire per effettuare il push a questo repository.

![Comando di Docker con esempio di push](media/push-command.png)

## <a name="push-the-image"></a>Eseguire il push dell'immagine

1. Nella riga di comando provare a eseguire il comando Push visualizzato nell'hub docker. Si noti che il comando utilizzerà lo spazio dei nomi, non "Docker".

    ```plaintext
    $ docker push docker/getting-started
    The push refers to repository [docker.io/docker/getting-started]
    An image does not exist locally with the tag: docker/getting-started
    ```

    Perché ha avuto esito negativo? Il comando Push cercava un'immagine denominata Docker/Getting-Started, ma non ne è stata trovata una. Se si esegue `docker image ls` , non verrà visualizzato uno di questi due valori.

    Per risolvere il problema, è necessario "contrassegnare" l'immagine esistente creata per assegnarle un altro nome.

1. Accedere all'hub Docker usando il comando `docker login -u <username>` .

1. Usare il `docker tag` comando per assegnare all' `getting-started` immagine un nuovo nome. Assicurarsi di sostituire `<username>` con l'ID docker.

    ```bash
    docker tag getting-started <username>/getting-started
    ```

1. A questo punto provare a eseguire di nuovo il comando Push. Se si sta copiando il valore dall'hub Docker, è possibile eliminare la `tagname` parte, perché non è stato aggiunto un tag al nome dell'immagine. Se non si specifica un tag, Docker userà un tag denominato `latest` .

    ```bash
    docker push <username>/getting-started
    ```

    Al posto della riga di comando, è anche possibile fare clic con il pulsante destro del mouse sul tag immagine nella sezione **Immagini** della visualizzazione Docker e scegliere **push...**, quindi scegliere **Connetti registro di sistema** e quindi **Hub Docker**.

## <a name="run-the-image-on-a-new-instance"></a>Eseguire l'immagine in una nuova istanza

Ora che l'immagine è stata compilata e inserita in un registro, provare a eseguire l'app in una nuova istanza che non ha mai visto questa immagine del contenitore. A tale scopo, si userà Play con Docker.

1. Aprire il browser per [giocare con Docker](http://play-with-docker.com).

1. Accedere con l'account Docker Hub.

1. Una volta effettuato l'accesso, fare clic sul collegamento "+ Aggiungi nuova istanza" sulla barra laterale sinistra. Se non viene visualizzato, rendere il browser leggermente più ampio. Dopo alcuni secondi, nel browser verrà aperta una finestra del terminale.

    ![Riproduci con Docker Aggiungi nuova istanza](media/pwd-add-new-instance.png)

1. Nel terminale avviare l'app appena inserita.

    ```bash
    docker run -dp 3000:3000 <username>/getting-started
    ```

    Si noterà che l'immagine viene ritirata e infine avviata.

1. Fai clic sul badge 3000 quando viene visualizzato per visualizzare l'app con le modifiche. Evviva! Se la notifica 3000 non viene visualizzata, è possibile fare clic sul pulsante **Apri porta** e digitare 3000.

## <a name="recap"></a>Riepilogo

In questa sezione si è appreso come condividere le immagini eseguendone il push in un registro. Si è quindi passati a una nuova istanza e è stato possibile eseguire l'immagine appena inserita. Si tratta di un'operazione molto comune nelle pipeline CI, in cui la pipeline creerà l'immagine e ne effettuerà il push in un registro e l'ambiente di produzione potrà usare la versione più recente dell'immagine.

Ora che è stato individuato, ricordare che alla fine dell'ultima sezione, dopo aver riavviato l'app, tutti gli elementi dell'elenco TODO sono stati persi. Ovviamente, non si tratta di un'esperienza utente eccezionale, quindi si apprenderà come è possibile rendere permanente i dati tra i riavvii.

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Salvataggio permanente del database](persist-your-data.md)