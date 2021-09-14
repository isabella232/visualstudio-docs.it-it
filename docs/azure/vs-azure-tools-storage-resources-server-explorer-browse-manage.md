---
title: Esplorare e gestire le risorse di archiviazione
description: Esplorazione e gestione delle risorse di archiviazione con Esplora server
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: 18726b1fa7f42b46cd309cfd4edef289d9469d39
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633012"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>Esplorare e gestire le risorse di archiviazione usando Esplora server

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>Panoramica

Se sono stati installati gli Strumenti di Azure per Microsoft Visual Studio, è possibile visualizzare i dati BLOB, della coda e della tabella dagli account di archiviazione per Azure. Il nodo **azure Archiviazione** in Esplora server mostra i dati presenti nell'account dell'emulatore di archiviazione locale e negli altri account di archiviazione di Azure.

Per visualizzare Esplora server in Visual Studio, sulla barra dei menu selezionare **Visualizza** Esplora server  >  . Il nodo **Archiviazione** mostra tutti gli account di archiviazione esistenti in ogni sottoscrizione o certificato di Azure a cui si è connessi. Se l'account di archiviazione non è visualizzato, è possibile aggiungerlo seguendo le istruzioni riportate [più avanti in questo articolo](#add-storage-accounts-by-using-server-explorer).

A partire da Azure SDK 2.7, è anche possibile usare Cloud Explorer per visualizzare e gestire le risorse di Azure. Per altre informazioni, vedere [Gestione delle risorse di Azure con Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md).

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Visualizzare e gestire le risorse di archiviazione in Visual Studio

Esplora server mostra automaticamente un elenco di BLOB, code e tabelle nell'account dell'emulatore di archiviazione. L'account dell'emulatore di archiviazione Esplora server sotto il nodo **Archiviazione** come **nodo** Sviluppo.

Per visualizzare le risorse dell'account dell'emulatore di archiviazione, espandere il nodo **Sviluppo** . Se l'emulatore di archiviazione non è stato avviato, verrà avviato automaticamente quando si espande il nodo **Sviluppo**. Questo processo può richiedere alcuni secondi. Durante l'avvio dell'emulatore di archiviazione è possibile continuare a lavorare in altre aree di Visual Studio.

Per visualizzare le risorse in un account di archiviazione, espandere il nodo dell'account di archiviazione in Esplora server, in corrispondenza dei nodi **Blob**, **Code** e **Tabelle**.

## <a name="work-with-blob-resources"></a>Usare le risorse BLOB

Il nodo **BLOB** visualizza un elenco di contenitori per l'account di archiviazione selezionato. I contenitori BLOB contengono file BLOB che possono essere organizzati in cartelle e sottocartelle. Per altre informazioni, vedere [Come usare l'archivio BLOB da .NET](/azure/storage/blobs/storage-dotnet-how-to-use-blobs).

### <a name="to-create-a-blob-container"></a>Per creare un contenitore BLOB

1. Aprire il menu di scelta rapida per il nodo **BLOB** e quindi scegliere **Crea contenitore BLOB**.
1. Immettere il nome del nuovo contenitore nella finestra di dialogo **Crea contenitore BLOB**.
1. Premere INVIO sulla tastiera, oppure fare clic o toccare all'esterno del campo del nome per salvare il contenitore BLOB.

   > [!NOTE]
   > Il nome del contenitore BLOB deve iniziare con un numero (0-9) o una lettera minuscola (a-z).

### <a name="to-delete-a-blob-container"></a>Per eliminare un contenitore BLOB

Aprire il menu di scelta rapida per il contenitore BLOB da rimuovere e quindi selezionare **Elimina**.

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>Per visualizzare un elenco degli elementi contenuti in un contenitore BLOB

Aprire il menu di scelta rapida per un nome di contenitore BLOB nell'elenco, quindi selezionare **Apri**.

Il contenuto di un contenitore BLOB viene visualizzato in una scheda nota come visualizzazione del contenitore BLOB.

![Visualizzazione del contenitore BLOB](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

È possibile eseguire le operazioni seguenti sui BLOB usando i pulsanti nell'angolo superiore destro della visualizzazione del contenitore BLOB:

* Immettere un valore di filtro e applicarlo.
* Aggiornare l'elenco di BLOB nel contenitore.
* Caricare un file.
* Eliminare un BLOB. L'eliminazione di un file da un contenitore BLOB non comporta l'eliminazione del file sottostante. Viene solo rimosso dal contenitore BLOB.
* Aprire un BLOB.
* Salvare un BLOB nel computer locale.

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>Per creare una cartella o una sottocartella in un contenitore BLOB

1. Scegliere il contenitore BLOB in **Cloud Explorer**. Nella finestra del contenitore selezionare il pulsante **Carica BLOB**.

1. Nella finestra di dialogo **Carica nuovo file** selezionare il pulsante **Sfoglia** per specificare il file da caricare e quindi immettere un nome di cartella nella casella **Cartella (facoltativa)**.

   ![Caricamento di un file in una cartella BLOB](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   Per aggiungere sottocartelle nelle cartelle del contenitore, seguire la stessa procedura. Se non si specifica un nome di cartella, il file viene caricato nel livello superiore del contenitore BLOB. Il file verrà visualizzato nella cartella specificata nel contenitore.

   ![Cartella aggiunta a un contenitore BLOB](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. Fare doppio clic sulla cartella o premere INVIO per visualizzare il contenuto della cartella. Dalla cartella del contenitore è possibile tornare alla radice del contenitore selezionando il pulsante **Apri directory padre** (freccia).

### <a name="to-delete-a-container-folder"></a>Per eliminare un cartella del contenitore

Eliminare tutti i file nella cartella.

Poiché le cartelle nei contenitori BLOB sono cartelle virtuali, non è possibile creare una cartella vuota, né eliminare una cartella per eliminare i file al suo interno. Per eliminare la cartella, è necessario eliminarne l'intero contenuto.

### <a name="to-filter-blobs-in-a-container"></a>Per filtrare i BLOB in un contenitore

È possibile filtrare i BLOB visualizzati specificando un prefisso comune.

Se, ad esempio, si immette il prefisso **hello** nella casella di testo del filtro e quindi si seleziona il pulsante **Esegui** (**!**), vengono visualizzati solo i BLOB che iniziano con "hello".

![Campo Filtro](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

Il campo del filtro rileva la differenza tra maiuscole e minuscole e non supporta l'applicazione di filtri con caratteri jolly. I BLOB possono essere filtrati solo in base al prefisso. Il prefisso può includere un delimitatore se ne viene usato uno per organizzare i BLOB in una gerarchia virtuale. Se, ad esempio, si imposta come filtro il prefisso "HelloFabric/" vengono restituiti tutti i BLOB che iniziano con tale stringa.

### <a name="to-download-blob-data"></a>Per scaricare i dati BLOB

In **Cloud Explorer** usare uno dei metodi seguenti:

* Aprire il menu di scelta rapida per uno o più BLOB e quindi selezionare **Apri**.
* Selezionare il nome del BLOB e quindi scegliere il pulsante **Apri**.
* Fare doppio clic sul nome del BLOB.

Lo stato di un download del BLOB viene visualizzato nella finestra **Log attività di Azure**.

Il BLOB viene aperto nell'editor predefinito per il tipo di file. Se il sistema operativo riconosce il tipo di file, il file viene aperto in un'applicazione installata in locale. In caso contrario, viene richiesto di scegliere un'applicazione appropriata per il tipo di file del BLOB. Il file locale creato durante il download di un BLOB è contrassegnato come di sola lettura.

I dati BLOB vengono memorizzati nella cache in locale e vengono confrontati con l'ora dell'ultima modifica del BLOB in Archiviazione BLOB di Azure. Se il BLOB è stato aggiornato dopo l'ultima volta che è stato scaricato, viene scaricato nuovamente. In caso contrario, il BLOB viene caricato dal disco locale.

Per impostazione predefinita, un BLOB viene scaricato in una directory temporanea. Per scaricare i BLOB in una directory specifica, aprire il menu di scelta rapida per i nomi di BLOB selezionati e scegliere **Salva con nome**. Quando si salva un BLOB in questo modo, il file del BLOB non viene aperto e viene creato il file locale con gli attributi di lettura/scrittura.

### <a name="to-upload-blobs"></a>Per caricare i BLOB

Per caricare i BLOB, selezionare il pulsante **Carica BLOB** quando il contenitore è aperto nella relativa visualizzazione.

È possibile scegliere di caricare uno o più file ed è possibile caricare file di qualsiasi tipo. La finestra **Log attività di Azure** mostra lo stato del caricamento. Per altre informazioni su come usare i dati BLOB, vedere [Come usare il servizio Archiviazione BLOB di Azure in .NET](/azure/storage/blobs/storage-quickstart-blobs-dotnet).

### <a name="to-view-logs-transferred-to-blobs"></a>Per visualizzare i log trasferiti nei BLOB

Se si usa Diagnostica di Azure per registrare dati dall'applicazione di Azure e i log sono stati trasferiti nell'account di archiviazione, vengono visualizzati i contenitori che Azure ha creato per questi log. Visualizzare questi log in Esplora server è un modo semplice per identificare i problemi relativi all'applicazione, soprattutto se è stata distribuita in Azure.

Per altre informazioni su Diagnostica di Azure, vedere [Raccogliere dati di registrazione usando Diagnostica di Azure](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="to-get-the-url-for-a-blob"></a>Per ottenere l'URL per un BLOB

Aprire il menu di scelta rapida del BLOB e quindi selezionare **Copia URL**.

### <a name="to-edit-a-blob"></a>Per modificare un BLOB

Scegliere il BLOB e quindi selezionare il **pulsante Apri BLOB.**

Il file viene scaricato in un percorso temporaneo e aperto nel computer locale. Caricare nuovamente il BLOB dopo aver apportato le modifiche.

## <a name="work-with-queue-resources"></a>Usare le risorse di accodamento

Le code dei servizi di archiviazione sono ospitate in un account di archiviazione di Azure. È possibile usarle per consentire ai ruoli del servizio cloud di comunicare reciprocamente e con altri servizi attraverso un meccanismo di trasferimento dei messaggi. È possibile accedere alla coda a livello di programmazione con un servizio cloud e con un servizio Web per i client esterni. È anche possibile accedere alla coda direttamente usando Esplora server in Visual Studio.

Quando si sviluppa un servizio cloud che usa le code, è possibile usare Visual Studio per creare le code e usarle in modo interattivo durante lo sviluppo e il test del codice.

In Esplora server è possibile visualizzare le code in un account di archiviazione, creare ed eliminare code, aprire una coda per visualizzarne i messaggi e aggiungere messaggi a una coda. Quando si apre una coda per visualizzarne il contenuto, è possibile visualizzare i singoli messaggi ed eseguire le azioni seguenti sulla coda usando i pulsanti disponibili nell'angolo superiore sinistro:

* Aggiornare la visualizzazione della coda.
* Aggiungere un messaggio alla coda.
* Rimuovere dalla coda il messaggio di livello superiore.
* Cancellare l'intera coda.

La figura seguente mostra una coda contenente due messaggi:

![Visualizzazione di una coda](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

Per altre informazioni sulle code dei servizi di archiviazione, vedere [Introduzione all'archiviazione code di Azure con .NET](/azure/storage/queues/storage-dotnet-how-to-use-queues). Per informazioni sul servizio Web per le code dei servizi di archiviazione, vedere [Concetti relativi al servizio di accodamento](/rest/api/storageservices/Queue-Service-Concepts). Per informazioni su come inviare messaggi a una coda dei servizi di archiviazione usando Visual Studio, vedere [Invio di messaggi a una coda di servizi di archiviazione](/azure/visual-studio/vs-storage-cloud-services-getting-started-queues).

> [!NOTE]
> Le code dei servizi di archiviazione sono diverse dalle code del bus di servizio di Azure. Per altre informazioni sulle code bus di servizio, vedere bus di servizio [code, argomenti e sottoscrizioni.](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions)

## <a name="work-with-table-resources"></a>Usare le risorse di una tabella

Il servizio Archiviazione tabelle di Azure consente di archiviare grandi quantità di dati strutturati. Il servizio è un datastore NoSQL che accetta chiamate autenticate dall'interno e dall'esterno del cloud di Azure. Le tabelle di Azure sono ideali per l'archiviazione di dati strutturati non relazionali.

### <a name="to-create-a-table"></a>Per creare una tabella

1. In **Cloud Explorer** selezionare il **nodo Tabelle** dell'account di archiviazione e quindi selezionare **Crea tabella**.
1. Nella finestra di dialogo **Crea tabella** immettere un nome per la tabella.

### <a name="to-view-table-data"></a>Per visualizzare i dati in una tabella

1. In **Cloud Explorer** aprire il nodo **di Azure** e quindi aprire il Archiviazione nodo. 
1. Aprire il nodo dell'account di archiviazione che interessa e quindi aprire il nodo **Tabelle** per visualizzare un elenco di tabelle per l'account di archiviazione.
1. Aprire il menu di scelta rapida per una tabella e quindi scegliere **Visualizza tabella**.

    ![Tabella di Azure in Esplora soluzioni](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

La tabella è organizzata in entità (mostrate nelle righe) e proprietà (mostrate nelle colonne). Ad esempio, la figura seguente mostra le entità elencate in Progettazione tabelle.

### <a name="to-edit-table-data"></a>Per modificare i dati della tabella

In **Progettazione tabelle** aprire il menu di scelta rapida per un'entità (una singola riga) o una proprietà (una singola cella) e quindi selezionare **Modifica**.

![Aggiungere o modificare un'entità di tabella](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

Le entità di una tabella non devono avere lo stesso set di proprietà (colonne). Tenere presenti le limitazioni seguenti relative alla visualizzazione e alla modifica dei dati della tabella:

* Non è possibile visualizzare o modificare i dati binari (`type byte[]`), ma è possibile archiviarli in una tabella.
* Non è possibile modificare i valori **PartitionKey** o **RowKey** perché Archiviazione tabelle di Azure non supporta tale operazione.
* Non è possibile creare una proprietà denominata **Timestamp**. I servizi di archiviazione di Azure usano una proprietà con quel nome.
* Se si immette un valore **DateTime,** è necessario seguire un formato appropriato per le impostazioni di area e lingua del computer, ad esempio MM/GG/AAAA HH:MM:SS [AM| PM] per l'inglese degli Stati Uniti).

### <a name="to-add-entities"></a>Per aggiungere le entità

1. In **Progettazione tabelle** selezionare il **pulsante Aggiungi** entità.

    ![Pulsante Aggiungi entità](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. Nella finestra di dialogo **Aggiungi entità** immettere i valori per le proprietà **PartitionKey** e **RowKey**.

    ![Finestra di dialogo Aggiungi entità](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    Immettere i valori con attenzione. Non è possibile modificarli dopo avere chiuso la finestra di dialogo, a meno che l'entità non venga eliminata e aggiunta di nuovo.

### <a name="to-filter-entities"></a>Per filtrare le entità

Se si usa il generatore di query, è possibile personalizzare il set di entità visualizzato in una tabella.

1. Per aprire il generatore di query, visualizzare prima una tabella.
1. Scegliere il pulsante **Generatore di query** nella barra degli strumenti della visualizzazione tabella.

    Verrà visualizzata la finestra di dialogo **Generatore di query**. La figura seguente mostra una query compilata nel generatore di query.

    ![Generatore di query](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. Una volta compilata la query, chiudere la finestra di dialogo. La query risultante in formato testo viene visualizzata in una casella di testo come filtro di WCF Data Services.
1. Per eseguire la query, scegliere l'icona a forma di triangolo verde.

È anche possibile filtrare i dati delle entità visualizzati in Progettazione tabelle se si immette una stringa di filtro di WCF Data Services direttamente nel campo del filtro. Una stringa di questo tipo è simile a una clausola SQL WHERE, ma viene inviata al server come richiesta HTTP. Per informazioni su come costruire stringhe di filtro, vedere [Costruzione di stringhe di filtro per Progettazione tabelle](vs-azure-tools-table-designer-construct-filter-strings.md).

La figura seguente mostra un esempio di una stringa di filtro valida:

![Stringa di filtro](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>Aggiornare i dati di archiviazione

Quando Esplora server si connette o riceve dati da un account di archiviazione, il completamento dell'operazione potrebbe richiedere fino a un minuto. Se Esplora server possibile connettersi, potrebbe verificarsi il timeout dell'operazione. Durante il recupero dei dati, è possibile continuare a lavorare in altre parti Visual Studio. Per annullare l'operazione se sta richiedendo troppo tempo, selezionare il pulsante **Interrompi aggiornamento** sulla barra degli strumenti di Esplora server.

### <a name="to-refresh-blob-container-data"></a>Per aggiornare i dati del contenitore BLOB

* Selezionare il nodo **BLOB** sotto **Archiviazione** e scegliere il pulsante **Aggiorna** sulla barra degli strumenti di Esplora server.
* Per aggiornare l'elenco di BLOB visualizzato, selezionare il pulsante **Esegui**.

### <a name="to-refresh-table-data"></a>Per aggiornare i dati della tabella

* Selezionare il nodo **Tabelle** sotto il nodo **Archiviazione** e quindi selezionare il pulsante **Aggiorna** sulla barra degli strumenti di Esplora server.
* Per aggiornare l'elenco di entità visualizzato **in** Progettazione tabelle , selezionare il **pulsante** Esegui in Progettazione tabelle.

### <a name="to-refresh-queue-data"></a>Per aggiornare i dati della coda

Selezionare il nodo **Code** sotto il nodo **Archiviazione** e quindi selezionare il pulsante **Aggiorna** sulla barra degli strumenti di Esplora server.

### <a name="to-refresh-all-items-in-a-storage-account"></a>Per aggiornare tutti gli elementi in un account di archiviazione

Scegliere il nome dell'account e quindi selezionare il pulsante **Aggiorna** sulla barra degli strumenti di Esplora server.

## <a name="add-storage-accounts-by-using-server-explorer"></a>Aggiungere account di archiviazione usando Esplora server

Sono disponibili due modi per aggiungere gli account di archiviazione usando Esplora server. È possibile creare un account di archiviazione nella sottoscrizione di Azure o è possibile collegarne uno esistente.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>Per creare un account di archiviazione usando Esplora server

1. In Esplora server aprire il menu di scelta rapida per il nodo **Archiviazione**, quindi scegliere **Crea account di archiviazione**.

1. Nella finestra di dialogo **Crea account di archiviazione** selezionare o immettere le informazioni seguenti:

   * Sottoscrizione di Azure a cui aggiungere l'account di archiviazione.
   * Nome da usare per il nuovo account di archiviazione.
   * Area o set di affinità (ad esempio Stati Uniti occidentali o Asia orientale).
   * Tipo di replica da usare per l'account di archiviazione, ad esempio con ridondanza locale.

   ![Creare un account di archiviazione di Azure](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. Selezionare **Crea**.

Il nuovo account di archiviazione viene visualizzato nell'elenco **Archiviazione** di Esplora soluzioni.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>Per collegare un account di archiviazione esistente usando Esplora server

1. In Esplora server aprire il menu di scelta rapida per il nodo **Archiviazione** di Azure, quindi selezionare **Associa archiviazione esterna**.

    ![Aggiunta di un account di archiviazione esistente](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. Nella finestra di dialogo **Crea account di archiviazione** selezionare o immettere le informazioni seguenti:

   * Nome dell'account di archiviazione esistente da collegare.
   * Chiave per l'account di archiviazione selezionato. Questo valore viene in genere immesso automaticamente quando si seleziona un account di archiviazione. Per memorizzare la chiave dell'account di archiviazione in Visual Studio, selezionare la casella di controllo **Memorizza chiave dell'account**.
   * Protocollo da usare per connettersi all'account di archiviazione, ad esempio HTTP, HTTPS o un endpoint personalizzato. Per altre informazioni sugli endpoint personalizzati, vedere [Come configurare le stringhe di connessione](/azure/storage/common/storage-configure-connection-string).

### <a name="to-view-the-secondary-endpoints"></a>Per visualizzare gli endpoint secondari

Se è stato creato un account di archiviazione con l'opzione di replica **Archiviazione con ridondanza geografica e accesso in lettura**, è possibile visualizzare gli endpoint secondari aprendo il menu di scelta rapida relativo al nome dell'account e quindi selezionando **Proprietà**.

![Endpoint secondari di archiviazione](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>Per rimuovere un account di archiviazione da Esplora server

In Esplora server aprire il menu di scelta rapida per il nome dell'account e quindi selezionare **Elimina**.

Se si elimina un account di archiviazione, anche le informazioni sulla chiave salvate per tale account verranno rimosse.

Se si elimina un account di archiviazione da Esplora server, tale operazione non influisce sull'account di archiviazione né sui dati che contiene. Rimuove semplicemente il riferimento da Esplora server. Per eliminare definitivamente un account di archiviazione, usare il [portale di Azure](https://portal.azure.com/).

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su come usare i servizi di archiviazione di Azure, vedere [Accesso ai servizi di Archiviazione di Azure](/azure/storage/common/storage-introduction).
