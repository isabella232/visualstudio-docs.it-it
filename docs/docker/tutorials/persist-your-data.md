---
title: 'Esercitazione su Docker-parte 4: salvare in permanente i dati'
description: Panoramica dell'app di esempio todo list eseguita in Node.js.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 36def9749dc75faa96dc3cdd171e17258f44e011
ms.sourcegitcommit: f4d734329c82f2c8005b36af4b2b5516d90e6c63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "89039175"
---
# <a name="persist-your-data"></a> Rendere persistenti i dati

Nel caso in cui non si sia notato, l'elenco attività verrà cancellato a ogni singolo avvio del contenitore. Perché? Esaminiamo il funzionamento del contenitore.

## <a name="the-containers-filesystem"></a>Filesystem del contenitore

Quando viene eseguito, un contenitore usa i vari livelli di un'immagine per il file System. Ogni contenitore ottiene anche la propria "area scratch" per la creazione, l'aggiornamento o la rimozione di file. Eventuali modifiche non verranno visualizzate in un altro contenitore, *anche se* usano la stessa immagine.

### <a name="see-this-in-practice"></a>Vedere questa procedura in pratica

Per verificarlo, verranno avviati due contenitori e verrà creato un file in ognuno di essi. Si noterà che i file creati in un contenitore non sono disponibili in un altro contenitore.

1. Avviare un `ubuntu` contenitore che creerà un file denominato `/data.txt` con un numero casuale compreso tra 1 e 10000.

    ```bash
    docker run -d ubuntu bash -c "shuf -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"
    ```

    Se si è curiosi del comando, si avvia una shell bash e si richiamano due comandi (perché ha `&&` ). La prima parte sceglie un singolo numero casuale e lo scrive in `/data.txt` . Il secondo comando sta semplicemente osservando un file per il mantenimento dell'esecuzione del contenitore.

1. Verificare che sia possibile visualizzare l'output usando `exec` per accedere al contenitore. A tale scopo, aprire l'estensione VS Code e fare clic sull'opzione **Connetti Shell** . Verrà usato `exec` per aprire una shell nel contenitore all'interno del vs code terminale.

    ![VS Code aprire l'interfaccia della riga di comando nel contenitore Ubuntu](media/attach_shell.png)

    Verrà visualizzato un terminale che esegue una shell nel contenitore Ubuntu. Eseguire il comando seguente per visualizzare il contenuto del `/data.txt` file. Chiudere di nuovo il terminale.

    ```bash
    cat /data.txt
    ```

    Se si preferisce la riga di comando, è possibile usare il `docker exec` comando per eseguire la stessa operazione. È necessario ottenere l'ID del contenitore (usare `docker ps` per ottenerlo) e ottenere il contenuto con il comando seguente.

    ```bash
    docker exec <container-id> cat /data.txt
    ```

    Verrà visualizzato un numero casuale.

1. A questo punto, avviare un altro `ubuntu` contenitore (la stessa immagine) e si noterà che non si ha lo stesso file.

    ```bash
    docker run -it ubuntu ls /
    ```

    Ecco Nessun file disponibile `data.txt` . Questo perché è stato scritto nell'area scratch solo per il primo contenitore.

1. Andare avanti e rimuovere il primo contenitore usando il `docker rm -f` comando.

## <a name="container-volumes"></a>Volumi del contenitore

Con l'esperimento precedente si è visto che ogni contenitore inizia dalla definizione dell'immagine ogni volta che viene avviato. Sebbene i contenitori possano creare, aggiornare ed eliminare file, tali modifiche andranno perse quando il contenitore viene rimosso e tutte le modifiche sono isolate in tale contenitore. Con i volumi, è possibile modificare tutto questo.

I [volumi](https://docs.docker.com/storage/volumes/) consentono di connettere i percorsi di file System specifici del contenitore al computer host. Se viene montata una directory nel contenitore, nel computer host vengono visualizzate anche le modifiche apportate alla directory. Se si monta la stessa directory tra i riavvii del contenitore, vengono visualizzati gli stessi file.

Esistono due tipi principali di volumi. verranno usati entrambi, ma si inizierà con i **volumi denominati**.

## <a name="persist-your-todo-data"></a>Mantieni i dati todo

Per impostazione predefinita, l'app Todo archivia i dati in un [database SQLite](https://www.sqlite.org/index.html) all'indirizzo `/etc/todos/todo.db` . Se non si ha familiarità con SQLite, non ci sono problemi. Si tratta semplicemente di un database relazionale in cui tutti i dati vengono archiviati in un singolo file. Sebbene non sia il migliore per le applicazioni su larga scala, funziona per le piccole demo. In seguito, parleremo di come passare a un motore di database effettivo.

Quando il database è costituito da un singolo file, se è possibile rendere permanente il file nell'host e renderlo disponibile per il contenitore successivo, dovrebbe essere in grado di riprenderlo dall'ultima volta che è stato interrotto. Tramite la creazione di un volume e il collegamento (spesso denominato "montaggio") alla directory in cui sono archiviati i dati, è possibile salvare in modo permanente i dati. Quando il contenitore scrive nel `todo.db` file, viene salvato in modo permanente nell'host del volume.

Come indicato, si userà un **volume denominato**. Si pensi a un volume denominato semplicemente a un bucket di dati. Docker mantiene la posizione fisica sul disco ed è sufficiente ricordare il nome del volume. Ogni volta che si usa il volume, Docker verifica che vengano forniti i dati corretti.

1. Creare un volume tramite il `docker volume create` comando.

    ```bash
    docker volume create todo-db
    ```

1. Arrestare di nuovo il contenitore dell'app Todo nel dashboard (oppure con `docker rm -f <id>` ), perché è ancora in esecuzione senza usare il volume permanente.

1. Avviare il contenitore dell'app todo, ma aggiungere il `-v` flag per specificare un montaggio del volume. il volume denominato verrà usato e montato in, in `/etc/todos` modo da acquisire tutti i file creati nel percorso.

    ```bash
    docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
    ```

1. Quando il contenitore viene avviato, aprire l'app e aggiungere alcuni elementi all'elenco attività.

    ![Elementi aggiunti a todo list](media/items-added.png)

1. Rimuovere il contenitore per l'app todo. Usare il dashboard o `docker ps` per ottenere l'ID e quindi `docker rm -f <id>` rimuoverlo.

1. Avviare un nuovo contenitore usando lo stesso comando riportato sopra.

1. Aprire l'app. Gli elementi dovrebbero ancora essere visualizzati nell'elenco.

1. Procedere e rimuovere il contenitore al termine dell'estrazione dell'elenco.

Evviva! A questo punto si è appreso come salvare in modo permanente i dati.

> [!TIP]
> Anche se i volumi denominati e i montaggi di binding (che parleremo in un minuto) sono i due tipi principali di volumi supportati da un'installazione predefinita del motore Docker, sono disponibili molti plug-in di driver di volume per supportare NFS, SFTP, NetApp e altro ancora. Questa operazione è particolarmente importante quando si avvia l'esecuzione di contenitori su più host in un ambiente cluster con Swarm, Kubernetes e così via.

## <a name="dive-into-your-volume"></a>Approfondimenti sul volume

Spesso una grande quantità di persone chiede "dove si trova Docker per archiviare *effettivamente* i dati quando si usa un volume denominato?" Se si vuole saperlo, è possibile usare il `docker volume inspect` comando.

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

`Mountpoint`È il percorso effettivo sul disco in cui sono archiviati i dati. Si noti che nella maggior parte dei computer è necessario disporre dell'accesso radice per accedere a questa directory dall'host. Ma ecco dove si trova!

> [!NOTE]
> **Accesso ai dati del volume direttamente sul desktop Docker** Durante l'esecuzione in Docker desktop, i comandi di Docker sono in esecuzione in una macchina virtuale di piccole dimensioni nel computer. Se si vuole esaminare il contenuto effettivo della directory *mountpoint* , è necessario prima di tutto entrare nella macchina virtuale. In WSL 2 si trova all'interno di una distribuzione WSL 2 ed è possibile accedervi tramite Esplora file.

## <a name="recap"></a>Riepilogo

A questo punto, si dispone di un'applicazione funzionante che può rimanere riavviata. Puoi mostrarlo agli investitori e sperare che possano cogliere la tua visione!

Tuttavia, si è visto in precedenza che la ricompilazione di immagini per ogni modifica richiede molto tempo. È necessario essere un modo migliore per apportare modifiche, giusto? Con i montaggi di binding (che abbiamo accennato in precedenza), esiste una soluzione migliore. Diamo uno sguardo a questo punto.

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [Uso di montaggi di binding](use-bind-mounts.md)
