---
title: "Esercitazione su Docker - Parte 2: Condividere l'app"
description: Descrive come condividere immagini Docker usando il registro Docker Hub dati.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.custom: contperf-fy22q1
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 0367ca6b2ab6219ab50030df0b80a6aed213854f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633459"
---
# <a name="share-your-app"></a>Condividere l'app

Ora che è stata creata un'immagine, è possibile condividerla. Per condividere immagini Docker, è necessario usare un registro Docker. Il registro predefinito Docker Hub ed è la posizione da cui provengono tutte le immagini usate.

## <a name="create-a-repo"></a>Creare un repo

Per eseguire il push di un'immagine, è prima necessario creare un Docker Hub.

1. Passare a [Docker Hub](https://hub.docker.com/signup/msftedge?utm_source=msftedge) accedere, se necessario.

1. Fare clic **sul pulsante Crea** repository.

1. Per il nome del repo, usare `getting-started` . Assicurarsi che Visibility sia `Public` .

1. Fare clic **sul pulsante** Crea.

Se si osserva sul lato destro della pagina, verrà visualizzata una sezione denominata **Comandi di Docker.** Viene visualizzato un comando di esempio che sarà necessario eseguire per eseguire il push in questo repo.

![Comando Docker con esempio di push](media/push-command.png)

## <a name="push-the-image"></a>Eseguire il push dell'immagine

1. Nella riga di comando provare a eseguire il comando push visualizzato in Docker Hub. Si noti che il comando usa lo spazio dei nomi, non "docker".

    ```plaintext
    $ docker push docker/getting-started
    The push refers to repository [docker.io/docker/getting-started]
    An image does not exist locally with the tag: docker/getting-started
    ```

    Perché ha avuto esito negativo? Il comando push cercava un'immagine denominata docker/getting-started, ma non ne trovava una. Se si esegue `docker image ls` , non ne verrà visualizzato uno.

    Per risolvere questo problema, è necessario "contrassegnare" l'immagine esistente creata per assegnargli un altro nome.

1. Accedere al Docker Hub usando il comando `docker login -u <username>` .

1. Usare il `docker tag` comando per assegnare un `getting-started` nuovo nome all'immagine. Assicurarsi di sostituire con `<username>` l'ID Docker.

    ```bash
    docker tag getting-started <username>/getting-started
    ```

1. Provare a eseguire di nuovo il comando push. Se si copia il valore da Docker Hub, è possibile eliminare la parte, perché non è stato aggiunto `tagname` un tag al nome dell'immagine. Se non si specifica un tag, Docker userà un tag denominato `latest` .

    ```bash
    docker push <username>/getting-started
    ```

    **Invece** della riga di comando, è anche possibile fare  clic con il pulsante destro del mouse sul tag dell'immagine nella sezione Immagini della visualizzazione Docker e scegliere **Push...**, quindi scegliere registro Connessione **e** quindi Docker Hub .

## <a name="run-the-image-on-a-new-instance"></a>Eseguire l'immagine in una nuova istanza

Ora che l'immagine è stata compilata e inserita in un registro, provare a eseguire l'app in un'istanza completamente nuova che non ha mai visto questa immagine del contenitore. A tale scopo, si userà Play with Docker (Riproduci con Docker).

1. Aprire il browser per [riprodurre con Docker.](http://play-with-docker.com)

1. Accedere con l'account Docker Hub personale.

1. Dopo aver eseguito l'accesso, fare clic sul collegamento "+ ADD NEW INSTANCE" (+ AGGIUNGI NUOVA ISTANZA) nella barra laterale sinistra. Se non viene visualizzato, rendere il browser un po' più ampio. Dopo alcuni secondi verrà aperta una finestra del terminale nel browser.

    ![Riprodurre con l'aggiunta di una nuova istanza di Docker](media/pwd-add-new-instance.png)

1. Nel terminale avviare l'app appena inserita.

    ```bash
    docker run -dp 3000:3000 <username>/getting-started
    ```

    Si dovrebbe vedere che l'immagine viene trascinata verso il basso e alla fine si avvia.

1. Fare clic sul badge 3000 quando viene visualizzato per visualizzare l'app con le modifiche apportate. Evviva! Se il badge 3000 non viene visualizzato, è possibile fare clic sul pulsante **Apri** porta e digitare 3000.

## <a name="recap"></a>Riepilogo

In questa sezione si è appreso come condividere immagini tramite il push in un registro. Si è quindi passati a un'istanza completamente nuova ed è stato possibile eseguire l'immagine appena inserita. Questo è piuttosto comune nelle pipeline DI, in cui la pipeline creerà l'immagine ed eserne il push in un registro e quindi l'ambiente di produzione potrà usare la versione più recente dell'immagine.

A questo punto, tenere presente che alla fine dell'ultima sezione, quando è stata riavviata l'app, sono stati persi tutti gli elementi dell'elenco attività. Ovviamente non si tratta di un'esperienza utente ottimale, quindi si apprenderà come rendere persistenti i dati tra i riavvii.

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Persistenza del database](persist-your-data.md)
