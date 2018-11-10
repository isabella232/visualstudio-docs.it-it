---
title: Esplorare e gestire le risorse di archiviazione usando Esplora Server | Microsoft Docs
description: Esplorazione e gestione delle risorse di archiviazione usando Esplora Server
author: ghogen
manager: douge
assetId: 658dc064-4a4e-414b-ae5a-a977a34c930d
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: 00229cd88ddcab4d2d59ae40202620c374415e4b
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003050"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>Esplorare e gestire le risorse di archiviazione usando Esplora server

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>Panoramica

Se è stato installato Strumenti di Azure per Microsoft Visual Studio, è possibile visualizzare blob, coda e i dati della tabella dagli account di archiviazione di Azure. Azure **archiviazione** nodo in Esplora Server Mostra i dati presenti nell'account dell'emulatore di archiviazione locale e negli altri account di archiviazione di Azure.

Per visualizzare Esplora Server in Visual Studio, sulla barra dei menu, selezionare **View** > **Esplora Server**. Il **archiviazione** nodo Mostra tutti gli account di archiviazione esistenti in ogni sottoscrizione di Azure o un certificato che si è connessi. Se non viene visualizzato l'account di archiviazione, è possibile aggiungerlo seguendo le istruzioni riportate [più avanti in questo articolo](#add-storage-accounts-by-using-server-explorer).

A partire da Azure SDK 2.7, è anche possibile usare Cloud Explorer per visualizzare e gestire le risorse di Azure. Per altre informazioni, vedere [risorse di gestione di Azure con Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md).

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Visualizzare e gestire le risorse di archiviazione in Visual Studio

Esplora server Mostra automaticamente un elenco di BLOB, code e tabelle nell'account dell'emulatore di archiviazione. Account dell'emulatore di archiviazione è elencato in Esplora Server sotto il **archiviazione** nodo sotto il **sviluppo** nodo.

Per visualizzare le risorse dell'account dell'emulatore di archiviazione, espandere la **sviluppo** nodo. Se non è stato avviato l'emulatore di archiviazione quando si espande il **sviluppo** nodo, verrà avviato automaticamente. Questo processo può richiedere alcuni secondi. È possibile continuare a lavorare in altre aree di Visual Studio mentre viene avviato l'emulatore di archiviazione.

Per visualizzare le risorse in un account di archiviazione, espandere il nodo dell'account di archiviazione in Esplora Server in cui sono visualizzate **BLOB**, **code**, e **tabelle** nodi.

## <a name="work-with-blob-resources"></a>Usare le risorse blob

Il **BLOB** nodo viene visualizzato un elenco di contenitori per l'account di archiviazione selezionato. I contenitori BLOB contengono file blob, ed è possibile organizzare i BLOB in cartelle e sottocartelle. Per altre informazioni, vedere [come usare archiviazione Blob da .NET](/azure/storage/blobs/storage-dotnet-how-to-use-blobs).

### <a name="to-create-a-blob-container"></a>Per creare un contenitore blob

1. Aprire il menu di scelta rapida per il **BLOB** nodo e quindi selezionare **crea contenitore Blob**.
1. Nel **crea contenitore Blob** finestra di dialogo immettere il nome del nuovo contenitore.  
1. Premere INVIO sulla tastiera, oppure è possibile fare clic o toccare all'esterno del campo nome per salvare il contenitore blob.

   > [!NOTE]
   > Il nome del contenitore blob deve iniziare con una lettera minuscola (a-z) o un numero (0-9).

### <a name="to-delete-a-blob-container"></a>Per eliminare un contenitore blob

Aprire il menu di scelta rapida per il contenitore blob che si desidera rimuovere e quindi selezionare **Elimina**.

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>Per visualizzare un elenco degli elementi in un contenitore blob

Aprire il menu di scelta rapida per un nome del contenitore blob nell'elenco e quindi selezionare **aperto**.

Quando si visualizza il contenuto di un contenitore blob, viene visualizzato in una scheda nota come visualizzazione del contenitore blob.

![Visualizzazione del contenitore BLOB](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

È possibile eseguire le operazioni seguenti sui blob usando i pulsanti nell'angolo superiore destro della visualizzazione del contenitore blob:

* Immettere un valore di filtro e applicarlo.
* Aggiornare l'elenco dei BLOB nel contenitore.
* Caricare un file.
* Eliminare un blob. (L'eliminazione di un file da un contenitore blob non viene eliminato il file sottostante. Viene solo rimosso dal contenitore blob.)
* Aprire un blob.
* Salvare un blob nel computer locale.

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>Per creare una cartella o una sottocartella in un contenitore blob

1. Scegliere il contenitore blob in Cloud Explorer. Nella finestra del contenitore, selezionare la **carica Blob** pulsante.

1. Nel **Carica nuovo File** finestra di dialogo, seleziona la **Sfoglia** pulsante per specificare il file che si vuole caricare e quindi immettere un nome di cartella nel **cartella (facoltativo)** casella.

   ![Caricare un file in una cartella blob](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   È possibile aggiungere sottocartelle nelle cartelle del contenitore seguendo lo stesso passaggio. Se non si specifica un nome di cartella, il file viene caricato nel livello superiore del contenitore blob. Il file viene visualizzato nella cartella specificata nel contenitore.

   ![Cartella aggiunta a un contenitore blob](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. Fare doppio clic sulla cartella o premere INVIO per visualizzare il contenuto della cartella. Quando si è nella cartella del contenitore, è possibile tornare alla radice del contenitore selezionando il **Apri Directory padre** (freccia).

### <a name="to-delete-a-container-folder"></a>Per eliminare una cartella del contenitore

Eliminare tutti i file nella cartella.

Poiché le cartelle nei contenitori blob sono cartelle virtuali, è possibile creare una cartella vuota. È inoltre non è possibile eliminare una cartella per eliminare i file, ma invece necessario eliminare l'intero contenuto di una cartella per eliminare la cartella stessa.

### <a name="to-filter-blobs-in-a-container"></a>Per filtrare i BLOB in un contenitore

È possibile filtrare i BLOB visualizzati specificando un prefisso comune.

Ad esempio, se si immette il prefisso **hello** nella casella del filtro testo e quindi selezionare la **Execute** (**!**) vengono visualizzati solo i blob che iniziano con "hello" pulsante.

![Casella di testo filtro](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

Casella di testo filtro distinzione maiuscole/minuscole e non supporta il filtro con caratteri jolly. I BLOB possono essere filtrati solo dal prefisso. Il prefisso può includere un delimitatore se si usa un delimitatore per organizzare i BLOB in una gerarchia virtuale. Ad esempio, filtro il prefisso "HelloFabric /" restituisce tutti i blob che iniziano con tale stringa.

### <a name="to-download-blob-data"></a>Per scaricare i dati blob

In Cloud Explorer, usare uno qualsiasi dei metodi seguenti:

* Aprire il menu di scelta rapida per uno o più BLOB e quindi selezionare **aperto**.
* Scegliere il nome del blob e quindi selezionare il **aperto** pulsante.
* Fare doppio clic sul nome del blob.

Lo stato di avanzamento di un download di blob viene visualizzato nei **Log attività di Azure** finestra.

Il blob viene aperto nell'editor predefinito per tale tipo di file. Se il sistema operativo riconosce il tipo di file, il file viene aperto in un'applicazione installata in locale. In caso contrario, viene chiesto di scegliere un'applicazione appropriata per il tipo di file del blob. Il file locale che viene creato quando si scarica un blob viene contrassegnato come di sola lettura.

Dati BLOB vengono memorizzati nella cache locale e confrontati con l'ora dell'ultima modifica del blob nell'archivio Blob di Azure. Se il blob è stato aggiornato dopo l'ultimo download, viene scaricato nuovamente. In caso contrario, il blob viene caricato dal disco locale.

Per impostazione predefinita, un blob viene scaricato in una directory temporanea. Per scaricare i BLOB in una directory specifica, aprire il menu di scelta rapida per i nomi blob selezionati e scegliere **Salva con nome**. Quando si salva un blob in questo modo, non è possibile aprire il file di blob e viene creato il file locale con gli attributi di lettura/scrittura.

### <a name="to-upload-blobs"></a>Per caricare i BLOB

Per caricare i BLOB, selezionare la **carica Blob** dopo che il contenitore è aperto per la visualizzazione nella visualizzazione del contenitore blob.

È possibile scegliere uno o più file da caricare, ed è possibile caricare file di qualsiasi tipo. Il **Log attività di Azure** finestra Mostra lo stato di avanzamento del caricamento. Per altre informazioni su come usare i dati blob, vedere [come usare archiviazione Blob di Azure in .NET](http://go.microsoft.com/fwlink/p/?LinkId=267911).

### <a name="to-view-logs-transferred-to-blobs"></a>Per visualizzare i log trasferiti ai BLOB

Se si usa diagnostica di Azure per registrare dati dall'applicazione Azure e sono stati trasferiti log all'account di archiviazione, si noterà i contenitori di Azure creato per tali log. Visualizzare questi log in Esplora Server è un modo semplice per identificare i problemi relativi all'applicazione, soprattutto se è stata distribuita in Azure.

Per altre informazioni sulla diagnostica di Azure, vedere [raccogliere dati di registrazione utilizzando diagnostica Azure](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="to-get-the-url-for-a-blob"></a>Per ottenere l'URL per un blob

Aprire il menu di scelta rapida del blob e quindi selezionare **Copia URL**.

### <a name="to-edit-a-blob"></a>Per modificare un blob

Selezionare il blob e quindi selezionare il **Apri Blob** pulsante.

Il file viene scaricato in un percorso temporaneo e aperto nel computer locale. Caricare nuovamente il blob dopo aver apportato le modifiche.

## <a name="work-with-queue-resources"></a>Usare le risorse di coda

Le code di servizi di archiviazione sono ospitate in un account di archiviazione di Azure. È possibile utilizzare tali per consentire ai ruoli di servizio comunicare tra loro e con altri servizi tramite un meccanismo di passaggio dei messaggi del cloud. È possibile accedere alla coda a livello di codice tramite un servizio cloud e in un servizio web per i client esterni. È anche possibile accedere alla coda direttamente usando Esplora Server in Visual Studio.

Quando si sviluppa un servizio cloud che usa le code, è possibile usare Visual Studio per creare le code e lavorare con loro in modo interattivo durante lo sviluppo e test del codice.

In Esplora Server, è possibile visualizzare le code in un account di archiviazione, creare ed eliminare le code, apre una coda per visualizzarne i messaggi e aggiungere messaggi a una coda. Quando si apre una coda per la visualizzazione, è possibile visualizzare i singoli messaggi e si possono eseguire le azioni seguenti sulla coda usando i pulsanti nell'angolo superiore sinistro:

* Aggiornare la visualizzazione della coda.
* Aggiungere un messaggio alla coda.
* Rimozione dalla coda il messaggio di livello superiore.
* Cancellare l'intera coda.

L'immagine seguente mostra una coda contenente due messaggi:

![Visualizzazione di una coda](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

Per altre informazioni sull'archiviazione code dei servizi, vedere [Introduzione all'archiviazione code di Azure con .NET](http://go.microsoft.com/fwlink/?LinkID=264702). Per informazioni sul servizio web per le code dei servizi di archiviazione, vedere [concetti relativi al servizio di Accodamento](http://go.microsoft.com/fwlink/?LinkId=264788). Per informazioni su come inviare messaggi a una coda di servizi di archiviazione usando Visual Studio, vedere [invio di messaggi a una coda di servizi di archiviazione](https://docs.microsoft.com/azure/visual-studio/vs-storage-cloud-services-getting-started-queues).

> [!NOTE]
> Le code di servizi di archiviazione sono diverse dalle code del Bus di servizio di Azure. Per altre informazioni sulle code del Bus di servizio, vedere [code del Bus di servizio, argomenti e sottoscrizioni](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-queues-topics-subscriptions).

## <a name="work-with-table-resources"></a>Usare le risorse di tabella

Archiviazione tabelle di Azure archivia grandi quantità di dati strutturati. Il servizio è un datastore NoSQL che accetta chiamate autenticate dall'interno e all'esterno del cloud di Azure. Le tabelle di Azure sono ideali per l'archiviazione dei dati strutturati non relazionali.

### <a name="to-create-a-table"></a>Per creare una tabella

1. In Cloud Explorer selezionare il **tabelle** nodo dell'account di archiviazione e quindi selezionare **Create Table**.
1. Nel **Create Table** finestra di dialogo immettere un nome per la tabella.

### <a name="to-view-table-data"></a>Per visualizzare i dati della tabella

1. In Cloud Explorer aprire il **Azure** nodo e quindi aprire il **archiviazione** nodo.
1. Aprire il nodo di account di archiviazione che si è interessati e quindi aprire il **tabelle** nodo per visualizzare un elenco di tabelle per l'account di archiviazione.
1. Aprire il menu di scelta rapida per una tabella e quindi selezionare **vista tabella**.

    ![Una tabella di Azure in Esplora soluzioni](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

La tabella è organizzata in entità (mostrate nelle righe) e delle proprietà (mostrate nelle colonne). Ad esempio, la figura seguente mostra le entità elencate in Progettazione tabelle.

### <a name="to-edit-table-data"></a>Per modificare i dati della tabella

In Progettazione tabelle, aprire il menu di scelta rapida per un'entità (una singola riga) o una proprietà (una singola cella) e quindi selezionare **modifica**.

    ![Add or edit a table entity](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

Le entità in una singola tabella non deve avere lo stesso set di proprietà (colonne). Tenere presente le restrizioni seguenti sulla visualizzazione e modifica dei dati della tabella:

* Non è possibile visualizzare o modificare i dati binari (`type byte[]`), ma è possibile archiviarlo in una tabella.
* Non è possibile modificare il **PartitionKey** oppure **RowKey** valori, perché l'archiviazione tabelle di Azure non supporta tale operazione.
* Non è possibile creare una proprietà denominata **Timestamp**. Servizi di archiviazione di Azure usano una proprietà con lo stesso nome.
* Se si immette una **DateTime** valore, è necessario seguire un formato appropriato alle impostazioni di paese e lingua del computer in uso (ad esempio, MM/GG/AAAA hh.mm.ss [AM | PM] per l'inglese degli Stati Uniti).

### <a name="to-add-entities"></a>Per aggiungere entità

1. In Progettazione tabelle, selezionare la **Aggiungi entità** pulsante.

    ![Pulsante Aggiungi entità](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. Nel **Aggiungi entità** finestra di dialogo immettere i valori delle **PartitionKey** e **RowKey** proprietà.

    ![Dialogo Aggiungi entità](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    Immettere i valori con attenzione. È possibile modificare tali dopo aver chiuso la finestra di dialogo, a meno che non si elimina l'entità e aggiungerlo di nuovo.

### <a name="to-filter-entities"></a>Per filtrare le entità

È possibile personalizzare il set di entità visualizzato in una tabella se si usa il generatore delle query.

1. Per aprire il generatore delle query, aprire una tabella per la visualizzazione.
1. Selezionare il **generatore Query** sulla barra degli strumenti della visualizzazione tabella.

    Il **generatore Query** verrà visualizzata la finestra di dialogo. Nella figura seguente viene illustrata una query che viene compilata nel generatore di query.

    ![Generatore di query](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. Dopo aver completato la creazione della query, chiudere la finestra di dialogo. Risultante in formato testo della query viene visualizzato in una casella di testo come filtro di WCF Data Services.
1. Per eseguire la query, selezionare l'icona triangolo verde.

È anche possibile filtrare i dati entità visualizzati in Progettazione tabelle se si immette una stringa di filtro di WCF Data Services direttamente nella casella di testo filtro. Stringa di questo tipo è simile a una clausola SQL WHERE ma viene inviato al server come una richiesta HTTP. Per informazioni su come costruire stringhe di filtro, vedere [Constructing le stringhe di filtro per Progettazione tabelle](https://docs.microsoft.com/azure/vs-azure-tools-table-designer-construct-filter-strings).

La figura seguente mostra un esempio di una stringa di filtro valide:

![Stringa di filtro](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>Aggiornare i dati di archiviazione

Quando Esplora Server si connette o riceve dati da un account di archiviazione, l'operazione potrebbe richiedere fino a un minuto alla fine. Se non è possibile connettere Esplora Server, l'operazione potrebbe scadere. Mentre vengono recuperati i dati, è possibile continuare a lavorare in altre parti di Visual Studio. Per annullare l'operazione se sta richiedendo troppo tempo, selezionare la **Arresta aggiornamento** pulsante sulla barra degli strumenti di Esplora Server.

### <a name="to-refresh-blob-container-data"></a>Per aggiornare i dati del contenitore blob

* Selezionare il **BLOB** nodo sottostante **archiviazione**e quindi selezionare il **Aggiorna** pulsante sulla barra degli strumenti di Esplora Server.
* Per aggiornare l'elenco di BLOB visualizzato, selezionare la **Execute** pulsante.

### <a name="to-refresh-table-data"></a>Per aggiornare i dati della tabella

* Selezionare il **tabelle** nodo sottostante **archiviazione**e quindi selezionare il **Aggiorna** pulsante sulla barra degli strumenti di Esplora Server.
* Per aggiornare l'elenco delle entità che viene visualizzato in Progettazione tabelle, selezionare la **Execute** pulsante in Progettazione tabelle.

### <a name="to-refresh-queue-data"></a>Per aggiornare i dati della coda

Selezionare il **code** nodo sottostante **archiviazione**e quindi selezionare il **Aggiorna** pulsante sulla barra degli strumenti di Esplora Server.

### <a name="to-refresh-all-items-in-a-storage-account"></a>Per aggiornare tutti gli elementi in un account di archiviazione

Scegliere il nome dell'account e quindi selezionare il **Aggiorna** pulsante sulla barra degli strumenti di Esplora Server.

## <a name="add-storage-accounts-by-using-server-explorer"></a>Aggiungere gli account di archiviazione usando Esplora Server

Esistono due modi per aggiungere gli account di archiviazione usando Esplora Server. È possibile creare un account di archiviazione nella sottoscrizione di Azure oppure è possibile collegare un account di archiviazione.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>Per creare un account di archiviazione usando Esplora Server

1. In Esplora Server aprire il menu di scelta rapida per il **memorizzazione** nodo e quindi selezionare **crea Account di archiviazione**.

1. Nel **crea Account di archiviazione** finestra di dialogo, selezionare o immettere le informazioni seguenti:

   * Sottoscrizione di Azure a cui si desidera aggiungere l'account di archiviazione.
   * Il nome che si desidera utilizzare per il nuovo account di archiviazione.
   * Area o gruppo di affinità (ad esempio Stati Uniti occidentali o Asia orientale).
   * Il tipo di replica da usare, ad esempio per l'account di archiviazione con ridondanza locale.

   ![Creare un account di archiviazione di Azure](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. Scegliere **Crea**.

Il nuovo account di archiviazione viene visualizzato nei **archiviazione** elenco in Esplora soluzioni.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>Per collegare un account di archiviazione usando Esplora Server

1. In Esplora Server aprire il menu di scelta rapida per Azure **memorizzazione** nodo e quindi selezionare **associa archiviazione esterna**.

    ![Aggiunta di un account di archiviazione](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. Nel **crea Account di archiviazione** finestra di dialogo, selezionare o immettere le informazioni seguenti:

   * Il nome dell'account di archiviazione esistente che si desidera collegare.
   * La chiave dell'account di archiviazione selezionato. Questo valore viene in genere immesso automaticamente quando si seleziona un account di archiviazione. Se si vuole che Visual Studio di memorizzare la chiave di account di archiviazione, selezionare la **memorizza chiave dell'account** casella di controllo.
   * Il protocollo da usare per connettersi all'account di archiviazione, ad esempio HTTP, HTTPS o un endpoint personalizzato. Per altre informazioni sugli endpoint personalizzati, vedere [come configurare le stringhe di connessione](https://msdn.microsoft.com/library/azure/ee758697.aspx).

### <a name="to-view-the-secondary-endpoints"></a>Per visualizzare gli endpoint secondari

Se è stato creato un account di archiviazione usando il **Read-Access Geo Redundant** opzione di replica, è possibile visualizzare gli endpoint secondari aprendo il menu di scelta rapida per il nome dell'account e quindi selezionare **proprietà**.

![Endpoint secondari di archiviazione](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>Per rimuovere un account di archiviazione da Esplora Server

In Esplora Server aprire il menu di scelta rapida per il nome dell'account e quindi selezionare **Elimina**. 

Se si elimina un account di archiviazione, viene rimossa anche eventuali informazioni sulla chiave salvate per quell'account.

Se si elimina un account di archiviazione da Esplora Server, tale operazione non influisce sull'account di archiviazione né sui dati che contiene. Rimuove semplicemente il riferimento da Esplora Server. Per eliminare definitivamente un account di archiviazione, usare il [portale di Azure](https://portal.azure.com/).

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su come usare servizi di archiviazione di Azure, vedere [l'accesso a servizi di archiviazione di Azure](https://msdn.microsoft.com/library/azure/ee405490.aspx).
