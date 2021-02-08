---
title: 'Esercitazione su Docker-parte 7: usare Docker Compose'
description: Viene descritto come installare e utilizzare Docker Compose.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: f95a4f130e8ad662b3f0eca8f6f7d2162e2d1c7e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841718"
---
# <a name="use-docker-compose"></a>Usare Docker Compose

[Docker compose](https://docs.docker.com/compose/) è uno strumento sviluppato per semplificare la definizione e la condivisione di applicazioni multicontenitore. Con Compose è possibile creare un file YAML per definire i servizi e con un unico comando, in modo da poter ruotare tutti gli elementi o ridurli tutti.

Il *grande* vantaggio dell'uso di compose è la possibilità di definire lo stack di applicazioni in un file, conservarlo alla radice del repository del progetto (ora è controllato dalla versione) e consentire facilmente a un altro utente di contribuire al progetto. Un utente deve solo clonare il repository e avviare l'app compose. In realtà, è possibile che vengano visualizzati alcuni progetti in GitHub/GitLab in questo momento.

In che modo è possibile iniziare?

## <a name="install-docker-compose"></a>Installare Docker Compose

Se è stato installato Docker desktop per Windows o Mac, si ha già Docker Compose. Anche Docker Compose installate le istanze di Play-with-docker. Se si usa un computer Linux, è necessario installare Docker Compose usando [le istruzioni](https://docs.docker.com/compose/install/)riportate qui.

Al termine dell'installazione, sarà possibile eseguire il comando seguente e visualizzare le informazioni sulla versione.

```bash
docker-compose version
```

## <a name="create-the-compose-file"></a>Creare il file compose

1. Alla radice del progetto dell'app, creare un file denominato `docker-compose.yml` .

1. Nel file compose si inizierà definendo la versione dello schema. Nella maggior parte dei casi, è preferibile usare la versione supportata più recente. È possibile esaminare il [riferimento al file compose](https://docs.docker.com/compose/compose-file/) per le versioni dello schema corrente e la matrice di compatibilità.

    ```yaml
    version: "3.7"
    ```

1. Definire quindi l'elenco dei servizi (o contenitori) che si desidera eseguire come parte dell'applicazione.

    ```yaml hl_lines="3"
    version: "3.7"

    services:
    ```

A questo punto, si inizierà a migrare un servizio alla volta nel file compose.

## <a name="define-the-app-service"></a>Definire il servizio app

Si ricordi che questo è il comando usato per definire il contenitore dell'app (sostituire i ` \ ` caratteri con `` ` `` in Windows PowerShell).

```bash
docker run -dp 3000:3000 \
  -w /app -v ${PWD}:/app \
  --network todo-app \
  -e MYSQL_HOST=mysql \
  -e MYSQL_USER=root \
  -e MYSQL_PASSWORD=secret \
  -e MYSQL_DB=todos \
  node:12-alpine \
  sh -c "yarn install && yarn run dev"
```

1. Definire prima di tutto la voce del servizio e l'immagine per il contenitore. È possibile scegliere qualsiasi nome per il servizio. Il nome diventerà automaticamente un alias di rete, che sarà utile quando si definisce il servizio MySQL.

    ```yaml hl_lines="4 5"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
    ```

1. In genere, il comando verrà visualizzato vicino alla `image` definizione, anche se non è richiesto l'ordinamento. Quindi, procedere e spostarlo nel file.

    ```yaml hl_lines="6"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
    ```

1. Eseguire la migrazione della `-p 3000:3000` parte del comando definendo `ports` per il servizio. Si userà la [sintassi breve](https://docs.docker.com/compose/compose-file/#short-syntax-1) , ma è disponibile anche una [sintassi molto](https://docs.docker.com/compose/compose-file/#long-syntax-1) più dettagliata.

    ```yaml hl_lines="7 8"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
    ```

1. Eseguire quindi la migrazione della directory di lavoro ( `-w /app` ) e del mapping del volume ( `-v ${PWD}:/app` ) utilizzando `working_dir` le `volumes` definizioni e. I volumi hanno anche una sintassi [breve](https://docs.docker.com/compose/compose-file/#short-syntax-3) e [lunga](https://docs.docker.com/compose/compose-file/#long-syntax-3) .

   Un vantaggio di Docker Compose definizioni di volume è la possibilità di usare percorsi relativi dalla directory corrente.

    ```yaml hl_lines="9 10 11"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
    ```

1. Infine, eseguire la migrazione delle definizioni delle variabili di ambiente usando la `environment` chiave.

    ```yaml hl_lines="12 13 14 15 16"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
        environment:
          MYSQL_HOST: mysql
          MYSQL_USER: root
          MYSQL_PASSWORD: secret
          MYSQL_DB: todos
    ```

### <a name="define-the-mysql-service"></a>Definire il servizio MySQL

A questo punto, è possibile definire il servizio MySQL. Il comando usato per il contenitore è il seguente (sostituire i ` \ ` caratteri con `` ` `` in Windows PowerShell):

```bash
docker run -d \
  --network todo-app --network-alias mysql \
  -v todo-mysql-data:/var/lib/mysql \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=todos \
  mysql:5.7
```

1. In primo luogo, definire il nuovo servizio e denominarlo in `mysql` modo che ottenga automaticamente l'alias di rete. Specificare anche l'immagine da usare.

    ```yaml hl_lines="6 7"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
    ```

1. Definire quindi il mapping del volume. Quando è stato eseguito il contenitore con `docker run` , il volume denominato è stato creato automaticamente. Tuttavia, non si verifica quando si esegue con compose. È necessario definire il volume nella sezione di primo livello `volumes:` e quindi specificare il mountpoint nella configurazione del servizio. Semplicemente specificando solo il nome del volume, vengono usate le opzioni predefinite. Tuttavia, sono [disponibili molte altre opzioni](https://docs.docker.com/compose/compose-file/#volume-configuration-reference) .

    ```yaml hl_lines="8 9 10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
    
    volumes:
      todo-mysql-data:
    ```

1. Infine, è sufficiente specificare le variabili di ambiente.

    ```yaml hl_lines="10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
        environment: 
          MYSQL_ROOT_PASSWORD: secret
          MYSQL_DATABASE: todos
    
    volumes:
      todo-mysql-data:
    ```

A questo punto, l'operazione completata `docker-compose.yml` dovrebbe essere simile alla seguente:

```yaml
version: "3.7"

services:
  app:
    image: node:12-alpine
    command: sh -c "yarn install && yarn run dev"
    ports:
      - 3000:3000
    working_dir: /app
    volumes:
      - ./:/app
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

  mysql:
    image: mysql:5.7
    volumes:
      - todo-mysql-data:/var/lib/mysql
    environment: 
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

volumes:
  todo-mysql-data:
```

## <a name="run-the-application-stack"></a>Eseguire lo stack di applicazioni

Ora che il file è disponibile `docker-compose.yml` , è possibile avviarlo.

1. Prima di tutto, assicurarsi che non siano in esecuzione altre copie dell'app e del database ( `docker ps` e `docker rm -f <ids>` ).

1. Avviare lo stack di applicazioni usando il `docker-compose up` comando. Aggiungere il `-d` flag per eseguire tutti gli elementi in background. In alternativa, è possibile fare clic con il pulsante destro del mouse sul file compose e selezionare l'opzione **Componi su** per la barra laterale vs code. 

    ```bash
    docker-compose up -d
    ```

    Quando si esegue questa operazione, verrà visualizzato un output simile al seguente:

    ```plaintext
    Creating network "app_default" with the default driver
    Creating volume "app_todo-mysql-data" with default driver
    Creating app_app_1   ... done
    Creating app_mysql_1 ... done
    ```

    Si noterà che il volume è stato creato e una rete. Per impostazione predefinita, Docker Compose crea automaticamente una rete in modo specifico per lo stack di applicazioni, motivo per cui non ne è stata definita una nel file compose.

1. Esaminare i log usando il `docker-compose logs -f` comando. Verranno visualizzati i log di ogni servizio con interfoliazione in un singolo flusso. Questa operazione è estremamente utile quando si desidera controllare i problemi relativi alla tempistica. Il `-f` flag "segue" il log, quindi fornirà l'output in tempo reale quando viene generato.

    Se non è già presente, verrà visualizzato un output simile al seguente:

    ```plaintext
    mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections.
    mysql_1  | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
    app_1    | Connected to mysql db at host mysql
    app_1    | Listening on port 3000
    ```

    Il nome del servizio viene visualizzato all'inizio della riga (spesso colorata) per facilitare la distinzione dei messaggi. Se si desidera visualizzare i log per un servizio specifico, è possibile aggiungere il nome del servizio alla fine del comando logs (ad esempio, `docker-compose logs -f app` ).

    > [!TIP]
    > **In attesa del database prima di avviare l'app** Quando l'app viene avviata, si trova in realtà e attende che MySQL sia pronto e pronto prima di provare a connettersi a it.DocKer non dispone di alcun supporto incorporato per attendere che un altro contenitore sia completamente attivo, in esecuzione e pronto prima di avviare un altro contenitore. Per i progetti basati su nodi, è possibile usare la dipendenza della [porta di attesa](https://github.com/dwmkerr/wait-port) . Sono presenti progetti simili per altri linguaggi/Framework.

1. A questo punto, dovrebbe essere possibile aprire l'app e visualizzarne l'esecuzione. E Hey! Si sta per andare a un singolo comando.

## <a name="see-the-app-stack-in-the-docker-extension"></a>Vedere lo stack di app nell'estensione Docker

Se si esamina l'estensione Docker, è possibile modificare le opzioni di raggruppamento usando "COG" e "Group by". In questo caso, si desidera visualizzare i contenitori raggruppati per nome progetto compose:

![Estensione di Visual Studio con compose](media/vs-app-project-collapsed.png)

Se si esegue il vorticing della rete, vengono visualizzati i due contenitori definiti nel file compose.

![Estensione VS con compose espanso](media/vs-app-project-expanded.png)

## <a name="tear-it-all-down"></a>Elimina tutto

Quando si è pronti per rimuovere tutto, è sufficiente eseguire `docker-compose down` oppure fare clic con il pulsante destro del mouse sull'applicazione nell'elenco contenitori nell'vs code estensione Docker e selezionare **Componi giù**. I contenitori verranno interrotti e la rete verrà rimossa.

> [!WARNING]
> **Rimozione di volumi** Per impostazione predefinita, i volumi denominati nel file compose non vengono rimossi durante l'esecuzione `docker-compose down` . Se si desidera rimuovere i volumi, sarà necessario aggiungere il `--volumes` flag.

Una volta eliminato, è possibile passare a un altro progetto, eseguirlo `docker-compose up` ed essere pronto per contribuire a tale progetto. Non è molto più semplice.

## <a name="recap"></a>Riepilogo

In questa sezione sono state illustrate Docker Compose e il modo in cui contribuisce a semplificare notevolmente la definizione e la condivisione di applicazioni multiservizio. È stato creato un file compose traducendo i comandi utilizzati nel formato di composizione appropriato.

A questo punto, si sta iniziando a eseguire il wrapping dell'esercitazione. Tuttavia, esistono alcune procedure consigliate per la creazione di immagini da trattare, dal momento che si è verificato un grosso problema con la Dockerfile usata. Diamo un'occhiata.

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Procedure consigliate per la creazione di immagini](image-building-best-practices.md)
