---
title: 'Esercitazione su Docker - Parte 5: Usare bind mount'
description: Descrive come usare i montamenti di associazione per controllare il punto di montaggio nell'host.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: ad3737ccfa4b0dae8ad427bd79e4adeb2756795b
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222760"
---
# <a name="use-bind-mounts"></a>Usare bind mounts

Nel capitolo precedente sono stati appresi e usati volumi **denominati per** rendere persistenti i dati nel database. I volumi denominati sono molto importanti se si vogliono semplicemente archiviare i dati, in quanto non è necessario preoccuparsi della posizione in cui vengono archiviati i dati. 

Con **i montanti di binding** è possibile controllare il punto di montaggio esatto nell'host. È possibile usarlo per rendere persistenti i dati, ma viene spesso usato per fornire dati aggiuntivi nei contenitori. Quando si lavora a un'applicazione, è possibile usare un bind mount per montare il codice sorgente nel contenitore per consentire all'applicazione di visualizzare le modifiche al codice, rispondere e visualizzare immediatamente le modifiche.

Per le applicazioni basate su Node, [nodemon](https://npmjs.com/package/nodemon) è un ottimo strumento per controllare le modifiche ai file e quindi riavviare l'applicazione. Nella maggior parte degli altri linguaggi e framework sono disponibili strumenti equivalenti.

## <a name="quick-volume-type-comparisons"></a>Confronti rapidi dei tipi di volume

I montamenti di binding e i volumi denominati sono i due tipi principali di volumi disponibili con il motore Docker. Tuttavia, sono disponibili driver di volume aggiuntivi per supportare altri casi d'uso ([SFTP,](https://github.com/vieux/docker-volume-sshfs) [Ceph,](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/) [NetApp,](https://netappdvp.readthedocs.io/en/stable/) [S3](https://github.com/elementar/docker-s3-volume)e altro ancora).

| Proprietà | Volumi denominati | Bind mount |
| -------- | ------------- | ----------- |
| Posizione host | Docker sceglie | È possibile controllare |
| Esempio di montaggio (con `-v` ) | my-volume:/usr/local/data | /path/to/data:/usr/local/data |
| Popola il nuovo volume con il contenuto del contenitore | Sì | No |
| Supporta i driver di volume | Sì | No |

## <a name="start-a-dev-mode-container"></a>Avviare un contenitore in modalità sviluppo

Per eseguire il contenitore per supportare un flusso di lavoro di sviluppo, eseguire le operazioni seguenti:

- Montare il codice sorgente nel contenitore
- Installare tutte le dipendenze, incluse le dipendenze "dev"
- Avviare nodemon per controllare le modifiche al file system

1. Assicurarsi che non siano in esecuzione `getting-started` contenitori precedenti.

1. Eseguire il comando seguente (sostituire i ` \ ` caratteri con `` ` `` in Windows PowerShell). Si apprenderà cosa succede in seguito:

    ```bash
    docker run -dp 3000:3000 \
        -w /app \
        -v "%cd%:/app" \
        node:12-alpine \
        sh -c "yarn install && yarn run dev"
    ```

    - `-dp 3000:3000` : come in precedenza. Eseguire in modalità scollegata (in background) e creare un mapping delle porte
    - `-w /app` : imposta la "directory di lavoro" o la directory corrente da cui verrà eseguito il comando
    - `-v "%cd%:/app"` - Bind montare la directory corrente dall'host nel contenitore nella `/app` directory
    - `node:12-alpine` : immagine da usare. Si noti che questa è l'immagine di base per l'app dal Dockerfile
    - `sh -c "yarn install && yarn run dev"` : il comando . Si avvia una shell usando (alpine non ha ) ed è in esecuzione per `sh` `bash` installare tutte `yarn install` *le* dipendenze e quindi eseguire `yarn run dev` . Se si osserva in `package.json` , si noti che lo script sta `dev` avviando `nodemon` .

1. È possibile controllare i log usando `docker logs -f <container-id>` . Si saprà che si è pronti per iniziare quando viene visualizzato quanto seguente:

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

    Al termine del controllo dei log, uscire premendo `Ctrl` + `C` .

1. A questo punto, apportare una modifica all'app. Nel `src/static/js/app.js` file modificare il pulsante Aggiungi  **elemento** in modo da aggiungere semplicemente . Questa modifica sarà alla riga 109.

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. È sufficiente aggiornare la pagina (o aprirla) per visualizzare la modifica nel browser quasi immediatamente. Il riavvio del server Node potrebbe richiedere alcuni secondi, quindi se si verifica un errore, provare ad eseguire l'aggiornamento dopo alcuni secondi.

    ![Screenshot dell'etichetta aggiornata per il pulsante Aggiungi](media/updated-add-button.png)

1. È possibile apportare qualsiasi altra modifica che si desidera apportare. Al termine, arrestare il contenitore e compilare la nuova immagine usando `docker build -t getting-started .` .

L'uso di bind mounts *è molto* comune per le configurazioni di sviluppo locali. Il vantaggio è che non è necessario che nel computer di sviluppo siano installati tutti gli strumenti e gli ambienti di compilazione. Con un singolo `docker run` comando, l'ambiente di sviluppo viene estratto e pronto per l'uso. Verranno fornite informazioni sulle Docker Compose in un passaggio futuro, perché ciò consente di semplificare i comandi (si stanno già ricevendo molti flag).

## <a name="recap"></a>Riepilogo

A questo punto, è possibile rendere persistente il database e rispondere rapidamente alle esigenze e alle esigenze dei propri clienti e dei propri membri. Evviva! Ma, come si può immaginare? Hai ricevuto ottime notizie.

**Il progetto è stato selezionato per lo sviluppo futuro.**

Per prepararsi per la produzione, è necessario eseguire la migrazione del database dall'uso di SQLite a un elemento che può essere ridimensionato leggermente meglio. Per semplicità, è possibile usare un database relazionale e passare all'applicazione per usare MySQL. Ma come è consigliabile eseguire MySQL? Come si consente ai contenitori di parlare tra loro? Si apprenderà a questo proposito in un passaggio successivo.

## <a name="next-steps"></a>Passaggi successivi

Continuare con l'esercitazione.

> [!div class="nextstepaction"]
> [App con più contenitori](multi-container-apps.md)