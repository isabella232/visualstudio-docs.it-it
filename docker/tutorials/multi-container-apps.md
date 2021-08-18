---
title: 'Esercitazione su Docker - Parte 7: App multi-contenitore'
description: Come configurare la rete tra contenitori e aggiungere un contenitore per un database MySQL.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: a006435b6513d3cecf87f61c576dd253e3a68ef6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045515"
---
# <a name="multi-container-apps"></a>App con più contenitori

Fino a questo punto, si è lavorato con app a contenitore singolo. Si aggiungerà tuttavia MySQL nello stack dell'applicazione. Spesso si pone la domanda seguente: "Dove verrà eseguito MySQL? Installarlo nello stesso contenitore o eseguirlo separatamente?" In generale, **ogni contenitore deve eseguire una sola operazione e farlo bene.** Alcuni motivi:

- È probabile che sia necessario ridimensionare le API e i front-end in modo diverso rispetto ai database
- I contenitori separati consentono di creare versioni e aggiornare le versioni in isolamento
- Anche se è possibile usare un contenitore per il database in locale, è possibile usare un servizio gestito per il database nell'ambiente di produzione. Non si vuole quindi spedire il motore di database con l'app.
- L'esecuzione di più processi richiede un gestore di processi (il contenitore avvia un solo processo), che aggiunge complessità all'avvio/arresto del contenitore.

E ci sono altri motivi. Si aggiornerà quindi l'applicazione in modo che funzioni nel modo seguente:

![App Todo connessa al contenitore MySQL](media/multi-app-architecture.png)

## <a name="container-networking"></a>Rete del contenitore

Tenere presente che, per impostazione predefinita, i contenitori vengono eseguiti in isolamento e non conoscono altri processi o contenitori nello stesso computer. Quindi, come si consente a un contenitore di parlare con un altro? La risposta è **rete**. A questo punto, non è necessario essere un tecnico di rete (hooray!). È sufficiente ricordare questa regola...

> [!NOTE]
> Se due contenitori sono nella stessa rete, possono parlare tra loro. In caso contrario, non è possibile.

## <a name="start-mysql"></a>Avviare MySQL

Esistono due modi per inserire un contenitore in una rete: assegnarlo all'avvio o connettere un contenitore esistente. Per il momento, si creerà prima di tutto la rete e si collega il contenitore MySQL all'avvio.

1. Creare la rete.

    ```bash
    docker network create todo-app
    ```

1. Avviare un contenitore MySQL e collegarlo alla rete. Verranno anche definite alcune variabili di ambiente che verranno usate dal database per inizializzare il database (vedere la sezione "Variabili di ambiente" nell'elenco di [Docker Hub MySQL)](https://hub.docker.com/_/mysql/)(sostituire i caratteri con ` \ ` in `` ` `` Windows PowerShell).

    ```bash
    docker run -d \
        --network todo-app --network-alias mysql \
        -v todo-mysql-data:/var/lib/mysql \
        -e MYSQL_ROOT_PASSWORD=secret \
        -e MYSQL_DATABASE=todos \
        mysql:5.7
    ```

    Si può anche vedere che è stato specificato il `--network-alias` flag . Si tornerà a questo in un momento.

    > [!TIP]
    > Si noterà che si sta usando un nome di volume e lo si monta in , dove `todo-mysql-data` `/var/lib/mysql` MySQL archivia i dati. Tuttavia, non è mai stato eseguito un `docker volume create` comando. Docker riconosce che si vuole usare un volume denominato e ne crea automaticamente uno.

1. Per verificare che il database sia operativo, connettersi al database e verificare che si connetta.

    ```bash
    docker exec -it <mysql-container-id> mysql -p
    ```

    Quando viene visualizzata la richiesta della password, digitare **il segreto**. Nella shell MySQL elencare i database e verificare che sia `todos` visualizzato.

    ```cli
    mysql> SHOW DATABASES;
    ```

    Verrà visualizzato un output simile al seguente:

    ```plaintext
    +--------------------+
    | Database           |
    +--------------------+
    | information_schema |
    | mysql              |
    | performance_schema |
    | sys                |
    | todos              |
    +--------------------+
    5 rows in set (0.00 sec)
    ```

    Evviva! Il `todos` database è disponibile ed è pronto per l'uso.

## <a name="connect-to-mysql"></a>Connettersi a MySQL

Ora che Si è a sapere che MySQL è in esecuzione, è possibile usarlo. Ma la domanda è... Come? Se si esegue un altro contenitore nella stessa rete, come si trova il contenitore (tenere presente che ogni contenitore ha un proprio indirizzo IP)?

Per capirlo, si userà il contenitoreka/netshoot, fornito con  molti strumenti utili per la risoluzione o il debug dei problemi di rete. [](https://github.com/nicolaka/netshoot)

1. Avviare un nuovo contenitore usando `nicolaka/netshoot` l'immagine. Assicurarsi di connetterlo alla stessa rete.

    ```bash
    docker run -it --network todo-app nicolaka/netshoot
    ```

1. All'interno del contenitore `dig` usare il comando , che è un utile strumento DNS. Cercare l'indirizzo IP per il nome host `mysql` .

    ```bash
    dig mysql
    ```

    Si otterrà un output simile al seguente:

    ```text
    ; <<>> DiG 9.14.1 <<>> mysql
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 32162
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

    ;; QUESTION SECTION:
    ;mysql.             IN  A

    ;; ANSWER SECTION:
    mysql.          600 IN  A   172.23.0.2

    ;; Query time: 0 msec
    ;; SERVER: 127.0.0.11#53(127.0.0.11)
    ;; WHEN: Tue Oct 01 23:47:24 UTC 2019
    ;; MSG SIZE  rcvd: 44
    ```

    Nella sezione "ANSWER SECTION" verrà visualizzato un record per che si risolve in (l'indirizzo IP avrà `A` `mysql` probabilmente un valore `172.23.0.2` diverso). Anche se in genere non è un nome host valido, Docker è stato in grado di risolverlo nell'indirizzo IP del contenitore che aveva tale alias di rete (ricordare il flag usato in `mysql` `--network-alias` precedenza? ).

    Questo significa... L'app deve semplicemente connettersi a un host denominato `mysql` e si connetterà al database. Non è molto più semplice.

## <a name="run-your-app-with-mysql"></a>Eseguire l'app con MySQL

L'app todo supporta l'impostazione di alcune variabili di ambiente per specificare le impostazioni di connessione mySQL. ovvero:

- `MYSQL_HOST` : nome host per il server MySQL in esecuzione
- `MYSQL_USER` : nome utente da usare per la connessione
- `MYSQL_PASSWORD` : password da usare per la connessione
- `MYSQL_DB` : database da usare dopo la connessione

> [!WARNING]
> **Impostazione della connessione Impostazioni variabili di ambiente** Sebbene l'uso delle variabili di ambiente per impostare le impostazioni di connessione sia in genere un'opzione utile per lo sviluppo, è sconsigliato quando si eseguono applicazioni nell'ambiente di produzione. Per comprendere il motivo, vedere [Perché non è consigliabile usare le variabili di ambiente per i dati segreti.](https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/)
> Un meccanismo più sicuro è l'uso del supporto dei segreti fornito dal framework di orchestrazione dei contenitori. Nella maggior parte dei casi, questi segreti vengono montati come file nel contenitore in esecuzione. Si può vedere che molte app, tra cui l'immagine MySQL e l'app todo, supportano anche le var di ambiente con un suffisso per puntare a un `_FILE` file contenente il file.
> Ad esempio, se si imposta var, l'app userà il contenuto del file a `MYSQL_PASSWORD_FILE` cui si fa riferimento come password di connessione. Docker non fa nulla per supportare queste var di ambiente. L'app dovrà sapere di cercare la variabile e ottenere il contenuto del file.

Con tutte le informazioni illustrate, avviare il contenitore pronto per lo sviluppo.

1. Specificare ognuna delle variabili di ambiente precedenti e connettere il contenitore alla rete di app (sostituire i ` \ ` caratteri con `` ` `` in Windows PowerShell).

    ```bash hl_lines="3 4 5 6 7"
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

1. Se si osservano i log per il contenitore ( ), verrà visualizzato un messaggio che indica che sta `docker logs <container-id>` usando il database MySQL.

    ```plaintext hl_lines="7"
    # Previous log messages omitted
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Connected to mysql db at host mysql
    Listening on port 3000
    ```

1. Aprire l'app nel browser e aggiungere alcuni elementi all'elenco attività.

1. Connessione al database MySQL e dimostrare che gli elementi vengono scritti nel database. Tenere presente che la password è **il segreto**.

    ```bash
    docker exec -ti <mysql-container-id> mysql -p todos
    ```

    Nella shell di MySQL eseguire il comando seguente:

    ```plaintext
    mysql> select * from todo_items;
    +--------------------------------------+--------------------+-----------+
    | id                                   | name               | completed |
    +--------------------------------------+--------------------+-----------+
    | c906ff08-60e6-44e6-8f49-ed56a0853e85 | Do amazing things! |         0 |
    | 2912a79e-8486-4bc3-a4c5-460793a575ab | Be awesome!        |         0 |
    +--------------------------------------+--------------------+-----------+
    ```

    Ovviamente, la tabella avrà un aspetto diverso perché contiene gli elementi. Ma dovrebbero essere archiviati qui.

Se si osserva rapidamente l'estensione Docker, si nota che sono in esecuzione due contenitori di app. Tuttavia, non vi è alcuna indicazione reale che siano raggruppati in una singola app. A breve si scoprirà come migliorare questa soluzione.

![Estensione Docker che mostra due contenitori di app non raggruppati](media/vs-multi-container-app.png)

## <a name="recap"></a>Riepilogo

A questo punto, si dispone di un'applicazione che ora archivia i dati in un database esterno in esecuzione in un contenitore separato. Sono state apprese informazioni sulla rete dei contenitori e si è visto come è possibile eseguire l'individuazione dei servizi tramite DNS.

Tuttavia, c'è una buona probabilità che si inizi a essere un po' sovraccaricati di tutto ciò che è necessario fare per avviare questa applicazione. È necessario creare una rete, avviare i contenitori, specificare tutte le variabili di ambiente, esporre le porte e altro ancora. Si tratta di una situazione molto complessa da ricordare e che rende sicuramente più difficile passare le cose a un altro utente.

Nella sezione successiva si parlerà di Docker Compose. Con Docker Compose, è possibile condividere gli stack di applicazioni in modo molto più semplice e lasciare che altri utenti li spin up con un singolo (e semplice) comando.

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Uso di Docker Compose](use-docker-compose.md)
