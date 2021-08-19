---
title: 'Esercitazione su Docker - Parte 8: Usare Docker Compose'
description: Viene descritto come installare e usare Docker Compose.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 8e846388320da492ddccd7b2628112a32f0c4145
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122053436"
---
# <a name="use-docker-compose"></a>Usare Docker Compose

[Docker Compose](https://docs.docker.com/compose/) è uno strumento sviluppato per facilitare la definizione e la condivisione di applicazioni multi-contenitore. Con Compose è possibile creare un file YAML per definire i servizi e, con un singolo comando, è possibile ruotare tutto o eliminare tutto.

Il  grande vantaggio dell'uso di Compose è che è possibile definire lo stack di applicazioni in un file, mantenerlo nella radice del repo del progetto (ora è controllato dalla versione) e consentire facilmente a un altro utente di contribuire al progetto. Un utente dovrà solo clonare il proprio repo e avviare l'app Compose. In effetti, è possibile che alcuni progetti in GitHub/GitLab ese stiano eseguendo esattamente questa operazione.

Come iniziare?

## <a name="install-docker-compose"></a>Installare Docker Compose

Se Docker Desktop è stato installato per Windows o Mac, è già stato Docker Compose. Anche le istanze play-with-Docker Docker Compose installate. Se si usa un computer Linux, è necessario installare Docker Compose usando [le istruzioni riportate qui.](https://docs.docker.com/compose/install/)

Dopo l'installazione, dovrebbe essere possibile eseguire le operazioni seguenti e visualizzare le informazioni sulla versione.

```bash
docker-compose version
```

## <a name="create-the-compose-file"></a>Creare il file compose

1. Nella radice del progetto di app creare un file denominato `docker-compose.yml` .

1. Nel file compose si inizierà definendo la versione dello schema. Nella maggior parte dei casi, è meglio usare la versione supportata più recente. È possibile esaminare le informazioni di riferimento [sul file Compose](https://docs.docker.com/compose/compose-file/) per le versioni correnti dello schema e la matrice di compatibilità.

    ```yaml
    version: "3.7"
    ```

1. Definire quindi l'elenco di servizi (o contenitori) da eseguire come parte dell'applicazione.

    ```yaml hl_lines="3"
    version: "3.7"

    services:
    ```

A questo punto, si inizierà a eseguire la migrazione di un servizio alla volta nel file compose.

## <a name="define-the-app-service"></a>Definire il servizio app

Tenere presente che questo è il comando usato per definire il contenitore dell'app (sostituire i ` \ ` caratteri con `` ` `` in Windows PowerShell).

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

1. Definire prima di tutto la voce del servizio e l'immagine per il contenitore. È possibile selezionare qualsiasi nome per il servizio. Il nome diventerà automaticamente un alias di rete, che sarà utile quando si definisce il servizio MySQL.

    ```yaml hl_lines="4 5"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
    ```

1. In genere, il comando viene visualizzato vicino alla definizione, anche se non esiste `image` alcun requisito per l'ordinamento. Quindi, procedere e spostarlo nel file .

    ```yaml hl_lines="6"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
    ```

1. Eseguire la `-p 3000:3000` migrazione della parte del comando definendo per il `ports` servizio. In questo caso [](https://docs.docker.com/compose/compose-file/#short-syntax-1) si userà la sintassi breve, [](https://docs.docker.com/compose/compose-file/#long-syntax-1) ma è disponibile anche una sintassi più dettagliata e lunga.

    ```yaml hl_lines="7 8"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
    ```

1. Eseguire quindi la migrazione della directory di lavoro ( `-w /app` ) e del mapping del volume ( ) usando le `-v ${PWD}:/app` `working_dir` definizioni e `volumes` . I volumi hanno anche una [sintassi](https://docs.docker.com/compose/compose-file/#short-syntax-3) breve [e](https://docs.docker.com/compose/compose-file/#long-syntax-3) lunga.

   Uno dei vantaggi Docker Compose definizioni di volume è che è possibile usare percorsi relativi dalla directory corrente.

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

1. Eseguire infine la migrazione delle definizioni delle variabili di ambiente usando la `environment` chiave .

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

È ora possibile definire il servizio MySQL. Il comando usato per il contenitore era il seguente (sostituire i ` \ ` caratteri con `` ` `` in Windows PowerShell):

```bash
docker run -d \
  --network todo-app --network-alias mysql \
  -v todo-mysql-data:/var/lib/mysql \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=todos \
  mysql:5.7
```

1. Definire prima di tutto il nuovo servizio e assegnare al servizio il nome `mysql` in modo che oseni automaticamente l'alias di rete. Specificare anche l'immagine da usare.

    ```yaml hl_lines="6 7"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
    ```

1. Definire quindi il mapping del volume. Quando è stato eseguito il contenitore con `docker run` , il volume denominato è stato creato automaticamente. Tuttavia, questo non accade quando si esegue con Compose. È necessario definire il volume nella sezione di primo livello e quindi specificare il punto di `volumes:` montaggio nella configurazione del servizio. Specificando semplicemente il nome del volume, vengono usate le opzioni predefinite. Sono tuttavia [disponibili molte altre](https://github.com/compose-spec/compose-spec/blob/master/spec.md#volumes-top-level-element) opzioni.

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

1. Infine, è necessario specificare solo le variabili di ambiente.

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

A questo punto, il completamento `docker-compose.yml` dovrebbe essere simile al seguente:

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

## <a name="run-the-application-stack"></a>Eseguire lo stack dell'applicazione

Ora che il file è `docker-compose.yml` disponibile, è possibile avviarlo.

1. Assicurarsi prima di tutto che non siano in esecuzione altre copie dell'app e del database ( `docker ps` e `docker rm -f <ids>` ).

1. Avviare lo stack dell'applicazione usando il `docker-compose up` comando . Aggiungere il `-d` flag per eseguire tutti gli elementi in background. In alternativa, è possibile fare clic con il pulsante destro del mouse sul file Compose e selezionare **l'opzione Compose Up** (Componi su) VS Code barra laterale. 

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

    Si noterà che il volume è stato creato e una rete. Per impostazione predefinita, Docker Compose crea automaticamente una rete specifica per lo stack di applicazioni, motivo per cui non ne è stata definita una nel file compose.

1. Esaminare i log usando il `docker-compose logs -f` comando . Verranno visualizzati i log di ognuno dei servizi interfoliati in un unico flusso. Questo è estremamente utile quando si vogliono controllare i problemi relativi alla tempistica. Il `-f` flag "segue" il log, quindi restituisce l'output live non appena viene generato.

    Se non è già stato fatto, verrà visualizzato un output simile al seguente:

    ```plaintext
    mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections.
    mysql_1  | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
    app_1    | Connected to mysql db at host mysql
    app_1    | Listening on port 3000
    ```

    Il nome del servizio viene visualizzato all'inizio della riga (spesso colorato) per distinguere i messaggi. Per visualizzare i log per un servizio specifico, è possibile aggiungere il nome del servizio alla fine del comando logs, ad esempio `docker-compose logs -f app` .

    > [!TIP]
    > **Attesa del database prima di avviare l'app** Quando l'app viene avviato, in realtà si trova e attende che MySQL sia operativo e pronto prima di provare a connettersi a it.Docker non ha alcun supporto predefinito per attendere che un altro contenitore sia completamente operativo e pronto prima di avviare un altro contenitore. Per i progetti basati su Node, è possibile usare la [dipendenza della porta di](https://github.com/dwmkerr/wait-port) attesa. Sono disponibili progetti simili per altri linguaggi/framework.

1. A questo punto, dovrebbe essere possibile aprire l'app e vederla in esecuzione. E hey! È possibile eseguire un singolo comando.

## <a name="see-the-app-stack-in-the-docker-extension"></a>Visualizzare lo stack di app nell'estensione Docker

Se si osserva l'estensione Docker, è possibile modificare le opzioni di raggruppamento usando le opzioni 'cog' e 'group by'. In questo caso, si vogliono visualizzare i contenitori raggruppati per nome Project compose:

![Estensione di Visual Studio con Compose](media/vs-app-project-collapsed.png)

Se si scorre verso il basso la rete, verranno visualizzati i due contenitori definiti nel file compose.

![Estensione di Visual Studio con Compose espanso](media/vs-app-project-expanded.png)

## <a name="tear-it-all-down"></a>Disattesa tutto

Quando si è pronti per eliminare tutto, è sufficiente eseguire oppure fare clic con il pulsante destro del mouse sull'applicazione nell'elenco dei contenitori nell'estensione Docker VS Code e scegliere `docker-compose down` Componi.  I contenitori verranno arresti e la rete verrà rimossa.

> [!WARNING]
> **Rimozione di volumi** Per impostazione predefinita, i volumi denominati nel file compose NON vengono rimossi quando si esegue `docker-compose down` . Per rimuovere i volumi, è necessario aggiungere il `--volumes` flag .

Dopo l'eseparazione, è possibile passare a un altro progetto, eseguire ed essere pronti a `docker-compose up` contribuire al progetto. In realtà non è molto più semplice.

## <a name="recap"></a>Riepilogo

In questa sezione sono stati appresi i Docker Compose e come questo consente di semplificare notevolmente la definizione e la condivisione di applicazioni multi-servizio. È stato creato un file Compose traducendo i comandi in uso nel formato di composizione appropriato.

A questo punto, si inizia a completare l'esercitazione. Esistono tuttavia alcune procedure consigliate per la creazione di immagini da coprire, in quanto si verifica un problema grave con il Dockerfile in uso. Diamo quindi un'occhiata.

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Procedure consigliate per la creazione di immagini](image-building-best-practices.md)
