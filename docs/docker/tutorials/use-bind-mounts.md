---
title: 'Esercitazione su Docker-parte 5: usare i montaggi di binding'
description: Viene descritto come utilizzare i montaggi di binding per controllare il punto di montaggio nell'host.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 6474179a0714f2407ac37e724b997139206a91fb
ms.sourcegitcommit: f4d734329c82f2c8005b36af4b2b5516d90e6c63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "89039155"
---
# <a name="use-bind-mounts"></a>Usare i montaggi di binding

Nel capitolo precedente è stato descritto e utilizzato un **volume denominato** per salvare in modo permanente i dati nel database. I volumi denominati sono eccezionali se si vuole semplicemente archiviare i dati, perché non è necessario preoccuparsi della *posizione in cui* sono archiviati i dati.

Con i **montaggi di binding**è possibile controllare l'esatto mountpoint nell'host. Questa operazione può essere utilizzata per rendere permanente i dati, ma viene spesso utilizzata per fornire dati aggiuntivi nei contenitori. Quando si lavora in un'applicazione, è possibile usare un montaggio di binding per montare il codice sorgente nel contenitore per visualizzare le modifiche al codice, rispondere e consentire di visualizzare immediatamente le modifiche.

Per le applicazioni basate su nodi, [nodemon](https://npmjs.com/package/nodemon) è un ottimo strumento che consente di controllare le modifiche ai file e quindi di riavviare l'applicazione. Sono disponibili strumenti equivalenti nella maggior parte degli altri linguaggi e Framework.

## <a name="quick-volume-type-comparisons"></a>Confronti di tipo volume rapido

I montaggi di binding e i volumi denominati sono i due tipi principali di volumi disponibili con il motore docker. Sono tuttavia disponibili driver di volume aggiuntivi per supportare altri casi di utilizzo ([SFTP](https://github.com/vieux/docker-volume-sshfs), [Ceph](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/), [NetApp](https://netappdvp.readthedocs.io/en/stable/), [S3](https://github.com/elementar/docker-s3-volume)e altro ancora).

| Proprietà | Volumi denominati | Bind mount |
| -------- | ------------- | ----------- |
| Percorso host | Docker sceglie | Controllo |
| Esempio di montaggio (using `-v` ) | My-volume:/usr/local/data | /path/to/data:/usr/local/data |
| Popola il nuovo volume con contenuto del contenitore | Sì | No |
| Supporta i driver di volume | Sì | No |

## <a name="start-a-dev-mode-container"></a>Avviare un contenitore in modalità dev

Per eseguire il contenitore per supportare un flusso di lavoro di sviluppo, procedere come segue:

- Montare il codice sorgente nel contenitore
- Installare tutte le dipendenze, incluse le dipendenze "dev"
- Avviare nodemon per controllare le modifiche del file System

1. Assicurarsi che non siano presenti contenitori precedenti `getting-started` in esecuzione.

1. Eseguire il comando seguente (sostituire i ` \ ` caratteri con `` ` `` in Windows PowerShell). Si apprenderà come procedere in seguito:

    ```bash
    docker run -dp 3000:3000 \
        -w /app -v ${PWD}:/app \
        node:12-alpine \
        sh -c "yarn install && yarn run dev"
    ```

    - `-dp 3000:3000` -uguale a quello precedente. Esegui in modalità scollegata (in background) e crea un mapping delle porte
    - `-w /app` -imposta la "directory di lavoro" o la directory corrente da cui viene eseguito il comando
    - `-v ${PWD}:/app` -Binding montare la directory corrente dall'host nel contenitore alla `/app` Directory
    - `node:12-alpine` : immagine da usare. Si noti che questa è l'immagine di base per l'app da Dockerfile
    - `sh -c "yarn install && yarn run dev"` : comando. Stiamo iniziando una shell usando `sh` (Alpine non ha `bash` ) e l'esecuzione `yarn install` di per installare *tutte le* dipendenze e quindi l'esecuzione `yarn run dev` . Se si osserva la, si noterà `package.json` che lo `dev` script viene avviato `nodemon` .

1. È possibile controllare i log usando `docker logs -f <container-id>` . Si saprà che si è pronti a procedere quando viene visualizzato quanto segue:

    ```bash
    docker logs -f <container-id>
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Using sqlite database at /etc/todos/todo.db
    Listening on port 3000
    ```

    Al termine del controllo dei log, uscire da `Ctrl` + `C` .

1. A questo punto, apportare una modifica all'app. Nel `src/static/js/app.js` file modificare il pulsante **Aggiungi elemento** per **aggiungere**semplicemente. Questa modifica sarà alla riga 109.

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. È sufficiente aggiornare la pagina (o aprirla). la modifica verrà visualizzata quasi immediatamente nel browser. Potrebbero essere necessari alcuni secondi per il riavvio del server del nodo, quindi, se si riceve un errore, provare a eseguire l'aggiornamento dopo alcuni secondi.

    ![Screenshot dell'etichetta aggiornata per il pulsante Aggiungi](media/updated-add-button.png)

1. È possibile apportare tutte le altre modifiche desiderate. Al termine, arrestare il contenitore e compilare la nuova immagine usando `docker build -t getting-started .` .

Usare i montaggi di binding è *molto* comune per le configurazioni di sviluppo locali. Il vantaggio è che non è necessario che nel computer di sviluppo siano installati tutti gli strumenti e gli ambienti di compilazione. Con un unico `docker run` comando, l'ambiente di sviluppo viene tirato e pronto per l'uso. Si apprenderà come Docker Compose in un passaggio successivo, in quanto ciò consentirà di semplificare i comandi (si stanno già ottenendo moltissimi flag).

## <a name="recap"></a>Riepilogo

A questo punto, è possibile salvare in modo permanente il database e rispondere rapidamente alle esigenze e alle esigenze degli investitori e dei fondatori. Evviva! Ma indovinate? Hai ricevuto ottime notizie!

**Il progetto è stato selezionato per lo sviluppo futuro.**

Per preparare l'ambiente di produzione, è necessario eseguire la migrazione del database dall'uso di SQLite a un elemento che può essere ridimensionato in modo più efficace. Per semplicità, si manterrà un database relazionale e si commuterà l'applicazione per l'uso di MySQL. Ma come si deve eseguire MySQL? Come è possibile consentire ai contenitori di comunicare tra loro? Questa esercitazione verrà illustrata di seguito.

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [App con più contenitori](multi-container-apps.md)