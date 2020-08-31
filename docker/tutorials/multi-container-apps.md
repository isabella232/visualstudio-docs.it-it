---
title: 'Esercitazione su Docker-parte 6: app multicontenitore'
description: Come configurare la rete tra i contenitori e aggiungere un contenitore per un database MySQL.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 9513a3414a38aa02f6a4607a8c95bbf02c0e1cf6
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2020
ms.locfileid: "89178300"
---
# <a name="multi-container-apps"></a>App con più contenitori

Fino a questo punto, hai lavorato con le app a singolo contenitore. A questo punto, si aggiungerà MySQL allo stack dell'applicazione. Si pone spesso la domanda seguente: "dove viene eseguito MySQL? Installarlo nello stesso contenitore o eseguirlo separatamente? " In generale, **ogni contenitore deve eseguire una sola operazione ed eseguire questa operazione.** Alcuni motivi:

- C'è la possibilità di ridimensionare le API e i front-end in modo diverso rispetto ai database
- Contenitori distinti che consentono di aggiornare le versioni e le versioni in isolamento
- Sebbene sia possibile utilizzare un contenitore per il database in locale, potrebbe essere necessario utilizzare un servizio gestito per il database in produzione. Non si vuole distribuire il motore di database con l'app.
- L'esecuzione di più processi richiede un gestore di processi (il contenitore avvia solo un processo), che aggiunge complessità all'avvio/arresto del contenitore.

E ci sono più motivi. Quindi, l'applicazione verrà aggiornata in modo che funzioni come segue:

![App Todo connessa al contenitore MySQL](media/multi-app-architecture.png)

## <a name="container-networking"></a>Rete del contenitore

Tenere presente che, per impostazione predefinita, i contenitori vengono eseguiti in isolamento e non conoscono altri processi o contenitori nello stesso computer. Quindi, come si consente a un contenitore di comunicare con un altro? La risposta è la **rete**. A questo punto, non è necessario essere un tecnico di rete (evviva!). Basta ricordare questa regola...

> [!NOTE]
> Se due contenitori si trovano nella stessa rete, possono comunicare tra loro. In caso affermativo, non possono.

## <a name="start-mysql"></a>Avviare MySQL

Esistono due modi per inserire un contenitore in una rete: assegnarlo all'avvio o connettere un contenitore esistente. Per il momento si creerà prima la rete e si collegherà il contenitore MySQL all'avvio.

1. Creare la rete.

    ```bash
    docker network create todo-app
    ```

1. Avviare un contenitore MySQL e collegarlo alla rete. Si definiranno anche alcune variabili di ambiente che verranno usate dal database per inizializzare il database. vedere la sezione relativa alle variabili di ambiente nell' [elenco di hub Docker di MySQL](https://hub.docker.com/_/mysql/), sostituendo i ` \ ` caratteri con `` ` `` in Windows PowerShell.

    ```bash
    docker run -d \
        --network todo-app --network-alias mysql \
        -v todo-mysql-data:/var/lib/mysql \
        -e MYSQL_ROOT_PASSWORD=secret \
        -e MYSQL_DATABASE=todos \
        mysql:5.7
    ```

    Si noterà anche che è stato specificato il `--network-alias` flag. Torniamo a questo punto tra poco.

    > [!TIP]
    > Si noterà che si sta usando un nome di volume e lo si sta `todo-mysql-data` montando in `/var/lib/mysql` , dove MySQL archivia i dati. Tuttavia, non è mai stato eseguito alcun `docker volume create` comando. Docker riconosce che si vuole usare un volume denominato e ne crea uno automaticamente.

1. Per verificare che il database sia in esecuzione, connettersi al database e verificare che sia connesso.

    ```bash
    docker exec -it <mysql-container-id> mysql -p
    ```

    Quando viene visualizzata la richiesta della password, digitare **Secret**. In MySQL Shell, elencare i database e verificare che il database sia visualizzato `todos` .

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

    Evviva! Il database è `todos` pronto per l'uso.

## <a name="connect-to-mysql"></a>Connettersi a MySQL

Ora che MySQL è operativo, è possibile usarlo. Tuttavia, la domanda è... come? Se si esegue un altro contenitore nella stessa rete, come si individua il contenitore. tenere presente che ogni contenitore ha il proprio indirizzo IP?

Per scoprirlo, si userà il contenitore [nicolaka/NetShoot](https://github.com/nicolaka/netshoot) , fornito con *numerosi* strumenti utili per la risoluzione dei problemi di rete o il debug.

1. Avviare un nuovo contenitore usando l' `nicolaka/netshoot` immagine. Assicurarsi di connetterlo alla stessa rete.

    ```bash
    docker run -it --network todo-app nicolaka/netshoot
    ```

1. All'interno del contenitore, usare il `dig` comando, che è uno strumento DNS utile. Cercare l'indirizzo IP per il nome host `mysql` .

    ```bash
    dig mysql
    ```

    Si otterrà un output simile al seguente...

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

    Nella sezione "risposta", viene visualizzato un `A` record per che viene `mysql` risolto in `172.23.0.2` (l'indirizzo IP avrà probabilmente un valore diverso). Anche se in `mysql` genere non è un nome host valido, Docker è riuscito a risolverlo nell'indirizzo IP del contenitore con tale alias di rete (ricordare il `--network-alias` flag usato in precedenza?).

    Cosa significa... l'app deve semplicemente connettersi a un host denominato per `mysql` comunicare con il database. Non è molto più semplice.

## <a name="run-your-app-with-mysql"></a>Eseguire l'app con MySQL

L'app todo supporta l'impostazione di alcune variabili di ambiente per specificare le impostazioni di connessione di MySQL. I peering sono i seguenti:

- `MYSQL_HOST` : il nome host per il server MySQL in esecuzione
- `MYSQL_USER` : nome utente da usare per la connessione
- `MYSQL_PASSWORD` -password da usare per la connessione
- `MYSQL_DB` -database da usare una volta connessi

> [!WARNING]
> **Impostazione delle impostazioni di connessione tramite le variabili di ambiente** Quando si usano le variabili di ambiente per impostare le impostazioni di connessione è in genere accettabile per lo sviluppo, è molto sconsigliato quando si eseguono applicazioni in produzione. Per capire perché, vedere [perché non usare le variabili di ambiente per i dati segreti](https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/).
> Un meccanismo più sicuro consiste nell'usare il supporto Secret fornito dal framework dell'orchestrazione del contenitore. Nella maggior parte dei casi, questi segreti sono montati come file nel contenitore in esecuzione. Verranno visualizzate molte app (incluse l'immagine MySQL e l'app Todo) che supportano anche ENV Vars con un `_FILE` suffisso che punta a un file contenente il file.
> Ad esempio, se si imposta `MYSQL_PASSWORD_FILE` var, l'app userà il contenuto del file a cui si fa riferimento come password di connessione. Docker non esegue alcuna operazione per supportare questi env var. L'app deve essere in grado di cercare la variabile e ottenere il contenuto del file.

Con tutte queste spiegazioni, avviare il contenitore pronto per lo sviluppo.

1. Specificare tutte le variabili di ambiente precedenti e connettere il contenitore alla rete dell'app (sostituire i ` \ ` caratteri con `` ` `` in Windows PowerShell).

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

1. Se si esaminano i log per il contenitore ( `docker logs <container-id>` ), verrà visualizzato un messaggio che indica che viene usato il database MySQL.

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

1. Connettersi al database MySQL e dimostrare che gli elementi vengono scritti nel database. Tenere presente che la password è **segreta**.

    ```bash
    docker exec -ti <mysql-container-id> mysql -p todos
    ```

    In MySQL Shell eseguire quanto segue:

    ```plaintext
    mysql> select * from todo_items;
    +--------------------------------------+--------------------+-----------+
    | id                                   | name               | completed |
    +--------------------------------------+--------------------+-----------+
    | c906ff08-60e6-44e6-8f49-ed56a0853e85 | Do amazing things! |         0 |
    | 2912a79e-8486-4bc3-a4c5-460793a575ab | Be awesome!        |         0 |
    +--------------------------------------+--------------------+-----------+
    ```

    Ovviamente, la tabella avrà un aspetto diverso perché contiene gli elementi. Ma dovrebbero essere visualizzati qui.

Se si esamina rapidamente l'estensione Docker, si noterà che sono in esecuzione due contenitori di app. Tuttavia, non c'è alcuna indicazione reale che siano raggruppati in una singola app. Si vedrà come migliorare a breve.

![Estensione Docker che mostra due contenitori di app non raggruppati](media/vs-multi-container-app.png)

## <a name="recap"></a>Riepilogo

A questo punto si dispone di un'applicazione che ora archivia i dati in un database esterno in esecuzione in un contenitore separato. Si è appreso come eseguire l'individuazione dei servizi usando DNS.

Tuttavia, c'è una grande probabilità che si stia iniziando a ricorrere a una grande quantità di elementi necessari per avviare l'applicazione. È necessario creare una rete, avviare contenitori, specificare tutte le variabili di ambiente, esporre le porte e altro ancora. Questo è molto importante da ricordare ed è molto più difficile passare a un altro utente.

Nella sezione successiva parleremo di Docker Compose. Con Docker Compose è possibile condividere gli stack dell'applicazione in modo molto più semplice e consentire ad altri utenti di avviarli con un unico comando (e semplice).

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Utilizzo di Docker Compose](use-docker-compose.md)
