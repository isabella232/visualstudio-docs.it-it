---
title: 'Esercitazione su Docker - Parte 5: Rendere persistenti i dati'
description: Informazioni su come rendere persistenti i dati in un database e condividere le directory in un contenitore montando un volume.
ms.date: 08/06/2021
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-docker
ms.custom: contperf-fy22q1
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 36c7a2dbada3dd1f23b45019dc0690f3ba1ab5f1
ms.sourcegitcommit: f930bc28bdb0ba01d6f7cb48f229afecfa0c90cd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/18/2021
ms.locfileid: "122334466"
---
# <a name="persist-your-data"></a> Rendere persistenti i dati

Se non si è notato, l'elenco attività viene cancellato ogni volta che si avvia il contenitore. Perché? Verrà ora illustrato il funzionamento del contenitore.

## <a name="the-containers-filesystem"></a>File system del contenitore

Quando un contenitore viene eseguito, usa i vari livelli di un'immagine per il file system. Ogni contenitore ottiene anche il proprio "spazio scratch" per creare, aggiornare o rimuovere file. Le modifiche non verranno viste in un altro contenitore, *anche se* usano la stessa immagine.

### <a name="see-this-in-practice"></a>Vedere questo nella pratica

Per visualizzare questa operazione in azione, si inizieranno due contenitori e si creerà un file in ognuno di essi. Si noti che i file creati in un contenitore non sono disponibili in un altro.

1. Avviare un `ubuntu` contenitore che creerà un file denominato `/data.txt` con un numero casuale compreso tra 1 e 10000.

    ```bash
    docker run -d ubuntu bash -c "shuf -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"
    ```

    Nel caso in cui si sia incuriositi del comando, si avvia una shell bash e si richiamano due comandi (perché ha `&&` ). La prima parte seleziona un singolo numero casuale e lo scrive in `/data.txt` . Il secondo comando è semplicemente guardare un file per mantenere il contenitore in esecuzione.

1. Verificare che sia possibile visualizzare l'output usando `exec` per accedere al contenitore. A tale scopo, aprire l'estensione VS Code e fare clic **sull'opzione Collega** shell. Verrà utilizzata per `exec` aprire una shell nel contenitore all'interno del VS Code terminale.

    ![VS Code'interfaccia della riga di comando nel contenitore ubuntu](media/attach_shell.png)

    Verrà visualizzato un terminale che esegue una shell nel contenitore Ubuntu. Eseguire il comando seguente per visualizzare il contenuto del `/data.txt` file. Chiudere di nuovo questo terminale in seguito.

    ```bash
    cat /data.txt
    ```

    Se si preferisce la riga di comando, è possibile usare `docker exec` il comando per eseguire la stessa operazione. È necessario ottenere l'ID del contenitore (usare per `docker ps` ottenerlo) e ottenere il contenuto con il comando seguente.

    ```bash
    docker exec <container-id> cat /data.txt
    ```

    Verrà visualizzato un numero casuale.

1. Avviare ora un altro contenitore (la stessa immagine) e si scoprirà che non `ubuntu` è disponibile lo stesso file.

    ```bash
    docker run -it ubuntu ls /
    ```

    E guarda. Non è presente `data.txt` alcun file. Questo perché è stato scritto nello spazio scratch solo per il primo contenitore.

1. Procedere e rimuovere il primo contenitore usando il `docker rm -f` comando .

## <a name="container-volumes"></a>Volumi di contenitori

Con l'esperimento precedente si è visto che ogni contenitore inizia dalla definizione dell'immagine a ogni avvio. Anche se i contenitori possono creare, aggiornare ed eliminare file, tali modifiche andranno perse quando il contenitore viene rimosso e tutte le modifiche vengono isolate in tale contenitore. Con i volumi è possibile modificare tutto questo.

[I](https://docs.docker.com/storage/volumes/) volumi consentono di connettere percorsi di file system specifici del contenitore al computer host. Se viene montata una directory nel contenitore, le modifiche apportate a tale directory vengono anche viste nel computer host. Se si monta la stessa directory tra i riavvii del contenitore, vengono visualizzati gli stessi file.

Esistono due tipi principali di volumi. alla fine si useranno entrambi, ma si inizieranno con **i volumi denominati**.

## <a name="persist-your-todo-data"></a>Rendere persistenti i dati todo

Per impostazione predefinita, l'app todo archivia i dati in un [database SQLite](https://www.sqlite.org/index.html) in `/etc/todos/todo.db` . Se non si ha familiarità con SQLite, non c'è problema. Si tratta semplicemente di un database relazionale in cui tutti i dati vengono archiviati in un singolo file. Anche se questo non è il migliore per le applicazioni su larga scala, funziona per le demo di piccole dimensioni. In un secondo momento si parlerà del passaggio a un motore di database effettivo.

Se il database è un singolo file, se è possibile rendere persistente il file nell'host e renderlo disponibile per il contenitore successivo, dovrebbe essere in grado di riprendere il punto in cui è rimasto l'ultimo. Creando un volume e collegando (spesso denominato "montaggio") alla directory in cui sono archiviati i dati, è possibile rendere persistenti i dati. Quando il contenitore scrive nel file, viene salvato in modo `todo.db` permanente nell'host nel volume.

Come accennato, si userà un **volume denominato**. Un volume denominato può essere semplicemente un bucket di dati. Docker mantiene la posizione fisica sul disco ed è sufficiente ricordare il nome del volume. Ogni volta che si usa il volume, Docker si assicura che siano forniti i dati corretti.

1. Creare un volume usando il `docker volume create` comando .

    ```bash
    docker volume create todo-db
    ```

1. Arrestare di nuovo il contenitore di app todo nella visualizzazione Docker (o con ), perché è ancora in esecuzione `docker rm -f <id>` senza usare il volume permanente.

1. Avviare il contenitore dell'app todo, ma aggiungere il `-v` flag per specificare un montaggio del volume. Si userà il volume denominato e lo si monta in `/etc/todos` , che acquisisce tutti i file creati nel percorso.

    ```bash
    docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
    ```

1. Dopo l'avvio del contenitore, aprire l'app e aggiungere alcuni elementi all'elenco attività.

    ![Elementi aggiunti all'elenco attività](media/items-added.png)

1. Rimuovere il contenitore per l'app todo. Usare la visualizzazione Docker o `docker ps` per ottenere l'ID e `docker rm -f <id>` quindi rimuoverlo.

1. Avviare un nuovo contenitore usando lo stesso comando dall'alto.

1. Aprire l'app. Gli elementi dovrebbero essere ancora presenti nell'elenco.

1. Procedere e rimuovere il contenitore al termine del check-out dell'elenco.

Evviva! A questo punto si è appreso come rendere persistenti i dati.

> [!TIP]
> Sebbene i volumi denominati e i montamenti di binding (di cui si parlerà in un minuto) siano i due tipi principali di volumi supportati da un'installazione predefinita del motore Docker, sono disponibili molti plug-in di driver di volume per supportare NFS, SFTP, NetApp e altro ancora. Questo sarà particolarmente importante quando si avvia l'esecuzione di contenitori in più host in un ambiente cluster con Swarm, Kubernetes e così via.

## <a name="dive-into-your-volume"></a>Approfondimento del volume

Molte persone spesso chiedono "Dove docker *archivia* effettivamente i dati quando si usa un volume denominato?" Se si vuole sapere, è possibile usare il `docker volume inspect` comando .

```bash
docker volume inspect todo-db
[
    {
        "CreatedAt": "2019-09-26T02:18:36Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/todo-db/_data",
        "Name": "todo-db",
        "Options": {},
        "Scope": "local"
    }
]
```

è `Mountpoint` la posizione effettiva sul disco in cui vengono archiviati i dati. Si noti che nella maggior parte dei computer è necessario disporre dell'accesso root per accedere a questa directory dall'host. Ma è qui che si trova.

> [!NOTE]
> **Accesso ai dati del volume direttamente in Docker Desktop** Durante l'esecuzione in Docker Desktop, i comandi Docker vengono effettivamente eseguiti all'interno di una macchina virtuale di piccole dimensioni nel computer. Se si vuole esaminare il contenuto effettivo della directory *Mountpoint,* è prima necessario accedere alla macchina virtuale. In WSL 2 si trova all'interno di una distribuzione WSL 2 ed è possibile accedervi tramite il Esplora file.

## <a name="recap"></a>Riepilogo

A questo punto, si dispone di un'applicazione funzionante che può sopravvivere ai riavvii. È possibile mostrarlo agli investitori e sperano che possano intravasare la tua visione.

Tuttavia, si è visto in precedenza che la ricompilazione delle immagini per ogni modifica richiede un po' di tempo. Deve esserci un modo migliore per apportare modifiche, giusto? Con i montanti di binding (come accennato in precedenza), esiste un modo migliore. Diamo un'occhiata a questo punto.

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Uso di montanti di binding](use-bind-mounts.md)
