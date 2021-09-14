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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633460"
---
# <a name="persist-your-data"></a> Rendere persistenti i dati

Nel caso in cui non si sia notato, l'elenco attività viene cancellato ogni volta che si avvia il contenitore. Perché? Verrà ora illustrato il funzionamento del contenitore.

## <a name="the-containers-filesystem"></a>File system del contenitore

Quando un contenitore viene eseguito, usa i vari livelli di un'immagine per il relativo file system. Ogni contenitore ottiene anche il proprio "spazio scratch" per creare, aggiornare o rimuovere file. Le modifiche non verranno visibili in un altro contenitore, *anche se* usano la stessa immagine.

### <a name="see-this-in-practice"></a>Vedere questo nella pratica

Per vedere che cosa succede, si avviano due contenitori e si crea un file in ognuno di essi. Si noti che i file creati in un contenitore non sono disponibili in un altro contenitore.

1. Avviare un `ubuntu` contenitore che creerà un file denominato `/data.txt` con un numero casuale compreso tra 1 e 10000.

    ```bash
    docker run -d ubuntu bash -c "shuf -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"
    ```

    Se si è incuriositi del comando, si avvia una shell Bash e si richiamano due comandi (perché ha `&&` ). La prima parte seleziona un singolo numero casuale e lo scrive in `/data.txt` . Il secondo comando è semplicemente il controllo di un file per mantenere il contenitore in esecuzione.

1. Verificare che sia possibile visualizzare l'output usando `exec` per accedere al contenitore. A tale scopo, aprire l'estensione VS Code e fare clic **sull'opzione Attach Shell (Collega** shell). Verrà utilizzato per `exec` aprire una shell nel contenitore all'interno del terminale VS Code.

    ![VS Code l'interfaccia della riga di comando nel contenitore ubuntu](media/attach_shell.png)

    Verrà visualizzato un terminale che esegue una shell nel contenitore Ubuntu. Eseguire il comando seguente per visualizzare il contenuto del `/data.txt` file. Chiudere di nuovo il terminale in un secondo momento.

    ```bash
    cat /data.txt
    ```

    Se si preferisce la riga di comando, è possibile usare `docker exec` il comando per eseguire la stessa operazione. È necessario ottenere l'ID del contenitore (usare `docker ps` per ottenerlo) e ottenere il contenuto con il comando seguente.

    ```bash
    docker exec <container-id> cat /data.txt
    ```

    Verrà visualizzato un numero casuale.

1. Avviare ora un altro contenitore (la stessa immagine) e si scoprirà che `ubuntu` non è disponibile lo stesso file.

    ```bash
    docker run -it ubuntu ls /
    ```

    E guarda! Non è presente `data.txt` alcun file. Ciò è dovuto al fatto che è stato scritto nell'spazio scratch solo per il primo contenitore.

1. Procedere e rimuovere il primo contenitore usando il `docker rm -f` comando .

## <a name="container-volumes"></a>Volumi del contenitore

Con l'esperimento precedente si è visto che ogni contenitore inizia dalla definizione dell'immagine a ogni avvio. Anche se i contenitori possono creare, aggiornare ed eliminare file, tali modifiche andranno perse quando il contenitore viene rimosso e tutte le modifiche vengono isolate in tale contenitore. Con i volumi, è possibile modificare tutto questo.

[I](https://docs.docker.com/storage/volumes/) volumi consentono di connettere percorsi specifici del file system del contenitore al computer host. Se viene montata una directory nel contenitore, le modifiche apportate a tale directory vengono anche visibili nel computer host. Se si monta la stessa directory tra i riavvii del contenitore, vengono visualizzati gli stessi file.

Esistono due tipi principali di volumi. alla fine si useranno entrambi, ma si inizierà con **i volumi denominati**.

## <a name="persist-your-todo-data"></a>Rendere persistenti i dati Todo

Per impostazione predefinita, l'app todo archivia i dati in un [database SQLite](https://www.sqlite.org/index.html) all'indirizzo `/etc/todos/todo.db` . Se non si ha familiarità con SQLite, non ci sono problemi. Si tratta semplicemente di un database relazionale in cui tutti i dati vengono archiviati in un singolo file. Anche se questo non è il modo migliore per le applicazioni su larga scala, funziona per demo di piccole dimensioni. Si parlerà del passaggio a un motore di database effettivo in un secondo momento.

Se il database è un singolo file, se è possibile rendere persistente il file nell'host e renderlo disponibile per il contenitore successivo, dovrebbe essere in grado di riprendere dal punto in cui è stato lasciato l'ultimo. Creando un volume e collegando (spesso denominato "montaggio") alla directory in cui sono archiviati i dati, è possibile rendere persistenti i dati. Quando il contenitore scrive nel file, viene salvato in modo `todo.db` permanente nell'host nel volume.

Come accennato, si userà un **volume denominato**. Un volume denominato può essere semplicemente un bucket di dati. Docker mantiene la posizione fisica sul disco ed è sufficiente ricordare il nome del volume. Ogni volta che si usa il volume, Docker verifica che siano forniti i dati corretti.

1. Creare un volume usando il `docker volume create` comando .

    ```bash
    docker volume create todo-db
    ```

1. Arrestare di nuovo il contenitore dell'app Todo nella visualizzazione Docker (o con ), perché è ancora in esecuzione `docker rm -f <id>` senza usare il volume permanente.

1. Avviare il contenitore dell'app todo, ma aggiungere il `-v` flag per specificare un montaggio del volume. Si userà il volume denominato e lo si monta in `/etc/todos` , che acquisisce tutti i file creati nel percorso.

    ```bash
    docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
    ```

1. Dopo l'avvio del contenitore, aprire l'app e aggiungere alcuni elementi all'elenco attività.

    ![Elementi aggiunti all'elenco attività](media/items-added.png)

1. Rimuovere il contenitore per l'app todo. Usare la visualizzazione Docker o `docker ps` per ottenere l'ID e `docker rm -f <id>` quindi rimuoverlo.

1. Avviare un nuovo contenitore usando lo stesso comando precedente.

1. Aprire l'app. Gli elementi dovrebbero essere ancora presenti nell'elenco.

1. Al termine dell'estrazione dell'elenco, rimuovere il contenitore.

Evviva! A questo punto si è appreso come rendere persistenti i dati.

> [!TIP]
> Anche se i volumi denominati e i bind mount (di cui si parlerà in un minuto) sono i due tipi principali di volumi supportati da un'installazione predefinita del motore Docker, sono disponibili molti plug-in di driver di volume per supportare NFS, SFTP, NetApp e altro ancora. Ciò sarà particolarmente importante quando si inizia a eseguire i contenitori in più host in un ambiente cluster con Swarm, Kubernetes e così via.

## <a name="dive-into-your-volume"></a>Approfondire il volume

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

è `Mountpoint` la posizione effettiva sul disco in cui sono archiviati i dati. Si noti che nella maggior parte dei computer è necessario disporre dell'accesso radice per accedere a questa directory dall'host. Ma è qui che si trova.

> [!NOTE]
> **Accesso ai dati dei volumi direttamente in Docker Desktop** Durante l'esecuzione in Docker Desktop, i comandi di Docker vengono effettivamente eseguiti all'interno di una macchina virtuale di piccole dimensioni nel computer. Se si vuole esaminare il contenuto effettivo della directory *Mountpoint,* è necessario prima di tutto entrare all'interno della macchina virtuale. In WSL 2 si trova all'interno di una distribuzione WSL 2 ed è accessibile tramite il Esplora file.

## <a name="recap"></a>Riepilogo

A questo punto, si dispone di un'applicazione funzionante che può superare i riavvii. È possibile mostrarlo ai propri consegni e desiderare che possano intercettare la propria visione.

Tuttavia, si è visto in precedenza che la ricompilazione delle immagini per ogni modifica richiede un po' di tempo. C'è un modo migliore per apportare modifiche, giusto? Con i bind mount (come accennato in precedenza), esiste un modo migliore. Diamo un'occhiata a questo punto.

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Uso di bind mounts](use-bind-mounts.md)
