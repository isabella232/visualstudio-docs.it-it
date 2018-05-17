---
title: Introduzione alle funzioni di Azure
description: Uso delle funzioni di Azure in Visual Studio per Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.openlocfilehash: 5d787efbd09ad7f2d4a1f5f72b8f1493d8c6c587
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="introduction-to-azure-functions"></a>Introduzione alle funzioni di Azure

Le funzioni di Azure sono un metodo per la creazione e l'esecuzione di frammenti di codice gestiti dagli eventi (funzioni) nel cloud, senza richiedere l'aggiunta o la gestione esplicita di elementi di infrastruttura. Per altre informazioni sulle funzioni di Azure, vedere la [documentazione di Funzioni di Azure](https://docs.microsoft.com/azure/azure-functions/).

## <a name="requirements"></a>Requisiti

Gli strumenti Funzioni di Azure sono inclusi in **Visual Studio per Mac 7.5**.

Per creare e distribuire le funzioni è necessaria anche una sottoscrizione di Azure, disponibile gratuitamente in [https://azure.com/free](https://azure.com/free).

## <a name="creating-your-first-azure-functions-project"></a>Creazione del primo progetto di Funzioni di Azure

1. In Visual Studio per Mac selezionare **File > Nuova soluzione**. 
2. Nella finestra di dialogo Nuovo progetto, selezionare il modello Funzioni di Azure in **Cloud > Generale** e fare clic su **Avanti**:

    ![Finestra Nuovo progetto con l'opzione Funzioni di Azure](media/azure-functions-image1.png)

3. Immettere un nome in **Nome progetto** e selezionare **Crea**.

Visual Studio per Mac crea un progetto .NET Standard che include una funzione HttpTrigger predefinita. Il progetto include anche riferimenti NuGet a vari pacchetti **AzureWebJobs**, nonché al pacchetto **Newtonsoft.Json**.

![Editor di Visual Studio per Mac con una nuova funzione di Azure creata da un modello](media/azure-functions-newproj.png)

Il nuovo progetto contiene i file seguenti:

* **HttpTrigger.cs**: questa classe contiene codice boilerplate per una funzione attivata tramite HTTP. Contiene un attributo **FunctionName** con il nome della funzione e un attributo trigger **HttpTrigger**, che specifica che la funzione viene attivata da una richiesta HTTP. Per altre informazioni sul metodo della funzione, vedere l'articolo [Azure Functions C# developer reference](https://docs.microsoft.com/azure/azure-functions/functions-dotnet-class-library) (Riferimento di Funzioni di Azure per gli sviluppatori C#).
* **host.json**: questo file descrive le opzioni di configurazione globali per l'host delle funzioni. Per visualizzare un file di esempio e informazioni sulle impostazioni disponibili per tale file, vedere [Riferimento host.json per Funzioni di Azure](https://docs.microsoft.com/azure/azure-functions/functions-host-json).
* **local.settings.json**: questo file contiene tutte le impostazioni per l'esecuzione locale delle funzioni. Le impostazioni vengono usate dagli strumenti di base di Funzioni di Azure. Per altre informazioni, vedere [File di impostazioni locali](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local#local-settings-file) nell'articolo relativo agli strumenti di base di Funzioni di Azure.

Ora che è stato creato un nuovo progetto di Funzioni di Azure in Visual Studio per Mac, è possibile sottoporre a test la funzione attivata da HTTP predefinita nel computer locale.

<!--
## Create an Azure storage account

[Describe why this step is necessary and what it does]

1. Log on to your account at [https://portal.azure.com](https://portal.azure.com).
2. Under the **Favorites** section, located on the left of the screen, select **Storage Accounts**:
    ![]()
3. Select **Add** to create a new storage account:
    ![]()
4. Enter a globally unique name for the **Name** and reuse it for the **Resource group**. You can keep all the other items as their default.
    ![]()
5. Click **Create**. It might take a few minutes to create the storage account. You'll get a notification once it has been successfully created.
6. Select the **Go to resource** button from the notification:
    ![]()
-->

## <a name="testing-the-function-locally"></a>Test della funzione in locale

Grazie al supporto di Funzioni di Azure in Visual Studio per Mac è possibile sottoporre a test e debug la funzione nel computer di sviluppo locale.

1. Per eseguire il test della funzione in locale, fare clic sul pulsante **Esegui** in Visual Studio per Mac:

    ![Pulsante per l'avvio del debug in Visual Studio per Mac](media/azure-functions-run.png)

1. L'esecuzione del progetto inizia con il debug locale della funzione di Azure e apre una nuova finestra Terminale, come illustrato nell'immagine seguente: 

    ![Finestra Terminale con l'output della funzione](media/azure-functions-terminal.png) 

    Copiare l'URL dall'output.

3. Incollare l'URL della richiesta HTTP nella barra degli indirizzi del browser. Aggiungere la stringa di query `?name=<yourname>` alla fine dell'URL ed eseguire la richiesta. L'immagine seguente visualizza la risposta restituita dalla funzione nel browser alla richiesta GET locale:

    ![Richiesta HTTP nel browser](media/azure-functions-httpreq.png)

## <a name="creating-a-new-function"></a>Creazione di una nuova funzione

I modelli di funzione consentono di creare rapidamente nuove funzioni usando i trigger e i modelli più comuni. Quando viene creato un nuovo progetto Funzioni di Azure, questo include automaticamente una funzione HttpTrigger. Per creare un altro tipo di funzione, seguire questa procedura:

1. Rimuovere il file **HttpTrigger.cs** facendo clic con il pulsante destro del mouse su di esso e selezionando **Rimuovi**. Nell'avviso successivo, selezionare **Elimina** per rimuovere il file dal progetto:

    ![Finestra di dialogo per rimuovere il file dal progetto](media/azure-functions-remove.png)

2. Per aggiungere una nuova funzione, fare clic con il pulsante destro del mouse sul nome del progetto e selezionare **Aggiungi > Aggiungi funzione**:

    ![Azione di contesto per l'aggiunta della nuova funzione](media/azure-functions-addnew.png)

3. Nella finestra di dialogo **Nuova funzione di Azure** selezionare la funzione necessaria:

    ![Finestra di dialogo Nuova funzione di Azure](media/azure-functions-newfunction.png)

    Nella sezione seguente viene specificato un elenco dei modelli di funzioni di Azure.

## <a name="available-function-templates"></a>Modelli di funzioni disponibili

- **HTTP**: attivare l'esecuzione del codice usando una richiesta HTTP. Sono disponibili modelli espliciti per i seguenti trigger HTTP:
    - Http GET CRUD
    - Http POST CRUD
    - Trigger HTTP con parametri
    - Trigger HTTP
- **Timer**: consente di eseguire attività di pulizia o altre attività batch in una pianificazione predefinita. Questo modello supporta due campi: un nome e una pianificazione, ovvero un'espressione CRON a sei campi. Per altre informazioni, vedere [l'articolo di Funzioni di Azure con timer](https://docs.microsoft.com/azure/azure-functions/functions-create-scheduled-function)
- **Trigger GitHub**: risponde a eventi che si verificano nei repository GitHub. Per altre informazioni, vedere l'[articolo di Funzioni di Azure su GitHub](https://docs.microsoft.com/azure/azure-functions/functions-create-github-webhook-triggered-function)
    - Commenter GitHub: funzione che viene eseguita e aggiunge un commento ogni volta che viene ricevuto un webhook GitHub per un problema o una richiesta pull.
    - WebHook GitHub: Funzione che viene eseguita ogni volta che viene ricevuto un webhook GitHub
- **Trigger BLOB**: elabora i BLOB di Archiviazione di Azure quando vengono aggiunti a un contenitore. Oltre al nome della funzione, questo modello accetta proprietà Path e Connection. La proprietà Path è il percorso dell'account di archiviazione che verrà monitorato dal trigger. L'account di connessione è il nome dell'impostazione dell'app contenente la stringa di connessione dell'account di archiviazione. Per altre informazioni, vedere l'[articolo di Funzioni di Azure sull'archiviazione BLOB](https://docs.microsoft.com/azure/azure-functions/functions-create-storage-blob-triggered-function).
- **Trigger Queue**: funzione che risponde ai messaggi quando raggiungono la coda di Archiviazione di Azure. Oltre al nome della funzione, questo modello accetta una proprietà **Path** (nome della coda dalla quale verrà letto il messaggio) e una proprietà **Connection** dell'account di archiviazione (nome dell'impostazione dell'app che contiene la stringa di connessione dell'account di archiviazione). Per altre informazioni, vedere l'[articolo di Funzioni di Azure sull'archiviazione code](https://docs.microsoft.com/azure/azure-functions/functions-create-storage-queue-triggered-function).
- **WebHook generico**: funzione semplice che viene eseguita ogni volta che riceve una richiesta da un servizio che supporta i webhook. Per altre informazioni, vedere l'[articolo di Funzioni di Azure sui webhook generici](https://docs.microsoft.com/azure/azure-functions/functions-create-generic-webhook-triggered-function).
- **Image Resizer**: questa funzione crea immagini ridimensionate ogni volta che un BLOB viene aggiunto a un contenitore. Il modello accetta un percorso e una stringa di connessione per il trigger, un output immagine di piccole dimensioni e un output immagine di medie dimensioni.
- **Token SAS**: funzione che genera un token di firma di accesso condiviso per un nome BLOB e un contenitore di archiviazione di Azure specificato. Oltre al nome della funzione, questo modello accetta proprietà Path e Connection. La proprietà Path è il percorso dell'account di archiviazione che verrà monitorato dal trigger. L'account di connessione è il nome dell'impostazione dell'app contenente la stringa di connessione dell'account di archiviazione. È necessario impostare anche i **diritti di accesso**. Il livello di autorizzazione controlla se la funzione richiede una chiave API e quale chiave usare: Function usa una chiave di funzione, mentre Admin usa la chiave master. Per altre informazioni, vedere l'esempio [C# Azure Function for generating SAS tokens](https://azure.microsoft.com/resources/samples/functions-dotnet-sas-token/) (Funzione di Azure C# per generare token SAS).
- **Gestione di Funzioni durevoli**: Funzioni durevoli consente di creare funzioni con stato in un ambiente senza server. L'estensione gestisce lo stato, i checkpoint e i riavvii per conto dell'utente. Per altre informazioni, vedere le sezioni relative alle funzioni di Azure in [Funzioni durevoli](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview).