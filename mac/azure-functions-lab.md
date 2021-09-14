---
title: 'Esercitazione: Funzioni di Azure'
description: Procedura dettagliata sull'uso di Funzioni di Azure in Visual Studio per Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/06/2020
ms.technology: vs-ide-install
ms.assetid: 38FD2070-5151-482E-B0A9-993715128736
ms.topic: tutorial
ms.openlocfilehash: 3fa653a1acaae0f9b58d17f86d6e2e0feeb027a6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710493"
---
# <a name="tutorial-getting-started-with-azure-functions"></a>Esercitazione: Introduzione alle funzioni di Azure

In questa esercitazione si apprenderà come iniziare a creare le funzioni di Azure tramite Visual Studio per Mac. Si eseguirà anche l'integrazione con le tabelle di archiviazione di Azure, uno dei vari tipi di binding e trigger disponibili per gli sviluppatori di funzioni di Azure.

## <a name="objectives"></a>Obiettivi

> [!div class="checklist"]
> * Creare ed eseguire il debug di funzioni di Azure locali
> * Integrare risorse di archiviazione Web e di Azure
> * Gestire un flusso di lavoro che interessa più funzioni di Azure

## <a name="requirements"></a>Requisiti

- Visual Studio per Mac 7.5 o versione successiva.
- Una sottoscrizione di Azure (disponibile gratuitamente da [https://azure.com/free](https://azure.com/free?ref=visualstudio) ).

## <a name="exercise-1-creating-an-azure-functions-project"></a>Esercizio 1: Creazione di un progetto di Funzioni di Azure

1. Avviare **Visual Studio per Mac**.

2. Selezionare **File > Nuova soluzione**.

3. Nella categoria **Cloud > Generale** selezionare il modello **Funzioni di Azure**. Si userà C# per creare una libreria di classi .NET che ospita le funzioni di Azure. Fare clic su **Avanti**.

    ![Selezione del modello Funzioni di Azure](media/azure-functions-lab-image1.png)

4. Impostare **Nome progetto** su **"AzureFunctionsLab"** e fare clic su **Crea**.

    ![Denominazione e creazione del progetto di funzione di Azure](media/azure-functions-lab-image2.png)

5. Espandere i nodi nella **finestra della soluzione**. Il modello di progetto predefinito include riferimenti NuGet a vari pacchetti di Processi Web di Azure e al pacchetto Newtonsoft.Json.

     Sono anche disponibili tre file: **host.json** per la descrizione delle opzioni di configurazione globale per l'host, **local.settings.json** per la configurazione delle impostazioni del servizio.
        - Il modello di progetto crea anche un HttpTrigger predefinito. Ai fini di questa esercitazione, eliminare il file **HttpTrigger.cs** dal progetto.

    Aprire **local.settings.json**. Per impostazione predefinita il file include due impostazioni stringa di connessione vuote.

    ![finestra della soluzione che visualizza il file local.settings.json](media/azure-functions-lab-image3.png)

## <a name="exercise-2-creating-an-azure-storage-account"></a>Esercizio 2: Creazione di un account di archiviazione di Azure

1. Accedere all'account Azure all'indirizzo [https://portal.azure.com](https://portal.azure.com) .

1. Nella sezione **Preferiti** sul lato sinistro dello schermo, selezionare **Account di archiviazione**:

    ![Sezione Preferiti del portale di Azure con l'elemento Account di archiviazione](media/azure-functions-lab-image4.png)

1. Selezionare **Aggiungi** per creare un nuovo account di archiviazione:

    ![Pulsante per l'aggiunta di un nuovo account di archiviazione](media/azure-functions-lab-image5.png)

1. Immettere un nome univoco a livello globale in **Nome** e riusarlo per **Gruppo di risorse**. Mantenere i valori predefiniti per tutti gli altri elementi.

    ![Dettagli del nuovo account di archiviazione](media/azure-functions-lab-image6.png)

1. Fare clic su **Crea**. La creazione dell'account di archiviazione può richiedere alcuni minuti. Al completamento si riceve una notifica.

    ![Notifica di distribuzione riuscita](media/azure-functions-lab-image7.png)

1. Selezionare il pulsante **Vai alla risorsa** nella notifica.

1. Selezionare la scheda **Chiavi di accesso**.

    ![Impostazione della chiave di accesso](media/azure-functions-lab-image8.png)

1. Copiare la prima **stringa di connessione**. Questa stringa viene usata in seguito per integrare l'archiviazione di Azure con Funzioni di Azure.

    ![Informazioni per la chiave 1](media/azure-functions-lab-image9.png)

1. Tornare a **Visual Studio per Mac** e incollare la stringa di connessione completa nell'impostazione **AzureWebJobsStorage** in **local.settings.json**. Ora è possibile fare riferimento al nome dell'impostazione negli attributi per le funzioni che richiedono l'accesso alle risorse dell'impostazione.

    ![File di impostazioni locali con chiave di connessione immessa](media/azure-functions-lab-image10.png)

## <a name="example-3-creating-and-debugging-an-azure-function"></a>Esempio 3: Creazione e debug di una funzione di Azure

1. Ora è possibile iniziare ad aggiungere codice. Quando si usa una libreria di classi .NET le funzioni di Azure vengono aggiunte come metodi statici. Nella finestra **della soluzione fare** clic con il pulsante destro del mouse sul nodo del progetto **AzureFunctions** **e scegliere Aggiungi**> Aggiungi funzione :

    ![Opzione Aggiungi funzione](media/azure-functions-lab-image11.png)

1. Nella finestra di dialogo Nuova funzione di Azure selezionare il modello webhook generico. Impostare **Nome** su **Add** e fare clic su **Ok** per creare una funzione:

    ![Finestra di dialogo Nuova funzione di Azure](media/azure-functions-lab-image12.png)

1. Nella parte superiore del nuovo file aggiungere le direttive **using** seguenti:

    ```csharp
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using System.Web;
    using Microsoft.WindowsAzure.Storage.Table;
    ```

1. Rimuovere il metodo `Run` esistente e aggiungere il metodo seguente alla classe come funzione di Azure:

    ```csharp
    [FunctionName("Add")]
    public static int Run(
    [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
    HttpRequestMessage req,
    TraceWriter log)
    {
        int x = 1;
        int y = 2;

        return x + y;
    }
    ```

1. Di seguito si analizzano in dettaglio le varie sezioni della definizione del metodo.

    Inizialmente viene visualizzato l'attributo **FunctionName**, che contrassegna questo metodo come funzione di Azure. L'attributo specifica il nome pubblico della funzione. Il nome dell'attributo non deve necessariamente corrispondere al nome del metodo.

    ![Nuovo metodo run con l'attributo FunctionName evidenziato](media/azure-functions-lab-image13.png)

1. Successivamente, il metodo è contrassegnato come metodo **public static**, impostazione necessaria. Si noterà anche che il valore restituito è **int**. Se non diversamente specificato usando gli attributi del metodo, qualsiasi valore restituito non void di una funzione di Azure viene restituito al client come testo. Per impostazione predefinita viene restituito come **XML**, ma può essere modificato in **JSON**. Si eseguirà questa operazione più avanti nell'esercitazione.

    ![Nuovo metodo run con l'inizializzazione del metodo evidenziata](media/azure-functions-lab-image14.png)

1. Il primo parametro è contrassegnato con l'attributo **HttpTrigger**, che indica che il metodo viene chiamato da una richiesta HTTP. L'attributo specifica anche il livello di autorizzazione del metodo, nonché i verbi supportati (in questo caso solo **"GET"**). È anche possibile definire una **Route** che sostituisce il percorso del metodo e consente di estrarre automaticamente variabili dal percorso. Dato che in questo caso l'impostazione **Route** è null, il percorso di questo metodo assume l'impostazione predefinita **/api/Add**.

    ![Nuovo metodo run con il parametro evidenziato](media/azure-functions-lab-image15.png)

1. Il parametro finale del metodo è un **TraceWriter** che può essere usato per registrare messaggi per errori e di diagnostica.

    ![Nuovo metodo run con TraceWriter evidenziato](media/azure-functions-lab-image16.png)

1. Impostare un punto di interruzione sulla riga **return** del metodo facendo clic sul margine della riga:

    ![Punto di interruzione impostato sulla riga return](media/azure-functions-lab-image17.png)

1. Compilare ed eseguire il progetto in una sessione di debug premendo **F5** o selezionando **Esegui > Avvia debug**. In alternativa è possibile scegliere pulsante **Esegui**. Tutte queste opzioni eseguono la stessa attività. Nel resto di questa esercitazione viene citato **F5**, ma è possibile usare il metodo che si preferisce.

    ![Compilare ed eseguire il progetto](media/azure-functions-lab-image18.png)

1. Quando si esegue il progetto, viene aperta automaticamente l'applicazione Terminale.

1. Il progetto esegue un processo di rilevamento delle funzioni di Azure in base agli attributi del metodo e a una convenzione di file illustrata più avanti in questo articolo. In questo caso rileva una sola funzione di Azure e "genera" una funzione del processo.

    ![Output della funzione di Azure nel Terminale](media/azure-functions-lab-image19.png)

1. Nella parte inferiore dei messaggi di avvio, l'host Funzioni di Azure visualizza gli URL delle eventuali API trigger HTTP. Dovrebbe essere presente un solo trigger. Copiare l'URL e incollarlo in una nuova scheda del browser.

    ![URL di API della funzione di Azure](media/azure-functions-lab-image20.png)

1. Il punto di interruzione viene attivato immediatamente. La richiesta Web è stata inoltrata alla funzione e ora può essere sottoposta a debug. Portare il mouse sulla variabile **x** per visualizzarne il valore.

    ![Punto di interruzione attivato](media/azure-functions-lab-image21.png)

1. Rimuovere il punto di interruzione con lo stesso metodo usato in precedenza per aggiungerlo (fare clic sul margine o selezionare la riga e premere **F9**).

1. Premere **F5 per** continuare l'esecuzione.

1. Nel browser viene visualizzato il risultato XML del metodo. Come previsto, l'operazione di addizione hardcoded produce una somma plausibile. Se in Safari viene visualizzato solo "3" selezionare **Safari > Preferenze > Avanzate** e selezionare la casella di controllo "**Mostra menu Sviluppo nella barra dei menu**", quindi ricaricare la pagina.

1. In **Visual Studio per Mac** fare clic sul pulsante **Arresta** per terminare la sessione di debug. Per garantire che le nuove modifiche vengano implementate, ricordare di riavviare (arrestare e quindi eseguire) la sessione di debug.

    ![Opzione di arresto del debug](media/azure-functions-lab-image22.png)

1. Nel metodo **Run** sostituire le definizioni **x** e **y** con il codice seguente. Questo codice estrae valori dalla stringa di query dell'URL, per far sì che l'operazione di addizione sia eseguibile in modo dinamico in base ai parametri specificati.

    ```csharp
    var query = HttpUtility.ParseQueryString(req.RequestUri.Query);

    int x = int.Parse(query["x"]);

    int y = int.Parse(query["y"]);

    return x + y;
    ```

1. Eseguire l'applicazione.

1. Tornare alla finestra del browser e aggiungere la stringa `/?x=2&y=3` all'URL. L'URL intero ora sarà `http://localhost:7071/api/Add?x=2&y=3`. Passare al nuovo URL.

1. Ora il risultato rifletterà i nuovi parametri. Eseguire il progetto con valori diversi. Non è disponibile nessun controllo degli errori, pertanto in caso di parametri non validi o mancanti viene generato un errore.

1. Arrestare la sessione di debug.

## <a name="exercise-4-working-with-functionjson"></a>Esercizio 4: Uso di function.json

1. In un esercizio precedente, si indicava che Visual Studio per Mac "generava" una funzione di processo per la funzione di Azure definita nella libreria. Questo accade perché Funzioni di Azure non usa gli attributi del metodo in fase di runtime, ma usa una convenzione di file system in fase di compilazione per configurare la posizione e la modalità con cui le funzioni di Azure vengono rese disponibili. Nella finestra **della soluzione fare** clic con il pulsante destro del mouse sul nodo del progetto e scegliere Reveal in **Finder**.

     ![Opzione di menu Visualizza in Finder](media/azure-functions-lab-image23.png)

1. Spostarsi verso il basso nel file system fino a raggiungere **bin/Debug/netstandard2.0**. Trovare la cartella **Add**. La cartella è stata creata per la corrispondenza con l'attributo del nome di funzione nel codice C#. Espandere la cartella Add per visualizzare un singolo file **function.json**. Questo file viene usato dal runtime per ospitare e gestire la funzione di Azure. Per altri modelli di linguaggio senza supporto in fase di compilazione (ad esempio script C# o JavaScript), queste cartelle devono essere create e gestite manualmente. Per gli sviluppatori C# vengono generate automaticamente dai metadati degli attributi in fase di compilazione. Fare clic con il pulsante destro del mouse su **function.json** e selezionare l'opzione che lo apre in Visual Studio.

    ![function.json nella directory di file](media/azure-functions-lab-image24.png)

1. Tenendo in considerazione le fasi precedenti dell'esercitazione, ora si avrà un'idea di base degli attributi C#. Di conseguenza questo codice JSON dovrebbe risultare familiare. Tuttavia alcuni elementi non sono stati illustrati negli esercizi precedenti. Ad esempio, per ogni **binding** deve essere impostato l'elemento **direction** corrispondente. Come si può dedurre, **"in"** indica che il parametro è di input, mentre **"out"** indica che il parametro è un valore restituito (tramite **$return**) o un parametro **out** per il metodo. È anche necessario specificare l'elemento **scriptFile** (relativo a questo percorso finale) e il metodo **entryPoint** (public e static) all'interno dell'assembly. Nei passaggi seguenti si aggiungerà un percorso di funzione personalizzato usando questo modello. Copiare il contenuto di questo file negli Appunti.

    ![File function.json aperto in Visual Studio per Mac](media/azure-functions-lab-image25.png)

1. Nella finestra **della soluzione fare** clic con il pulsante destro del mouse sul nodo del progetto **AzureFunctionsLab** e scegliere Aggiungi > **nuova cartella**. Assegnare il nome **Adder** alla nuova cartella. Per convenzione predefinita, il nome di questa cartella definisce il percorso dell'API, ad esempio **api/Adder**.

    ![Opzione Nuova cartella](media/azure-functions-lab-image26.png)

1. Fare clic con il pulsante destro del mouse sulla cartella **Adder** e selezionare **Aggiungi > Nuovo file**.

    ![Opzione Nuovo file](media/azure-functions-lab-image27.png)

1. Selezionare la categoria **Web** e il modello **File JSON vuoto**. Impostare **Nome** su **function** e fare clic su **Nuovo**.

    ![Opzione File JSON vuoto](media/azure-functions-lab-image28.png)

1. Incollare il contenuto dell'altro file **function.json** (ottenuto nel passaggio 3) per sostituire il contenuto predefinito del file appena creato.

1. Rimuovere le righe seguenti dalla parte iniziale del file con estensione json:

    ```json
    "configurationSource":"attributes",
    "generatedBy":"Microsoft.NET.Sdk.Functions-1.0.13",
    ```

1. Alla fine del primo binding (dopo la riga **"name": "req"**) aggiungere le proprietà seguenti. Non dimenticare di includere una virgola nella riga precedente. Questa proprietà sostituisce la radice predefinita e ora estrae i parametri **int** dal percorso e li inserisce nei parametri del metodo denominati **x** e **y**.

    ```json
    "direction": "in",
    "route": "Adder/{x:int?}/{y:int?}"
    ```

1. Aggiungere un altro binding sotto il primo. Questo binding gestisce il valore restituito della funzione. Non dimenticare di includere una virgola nella riga precedente:

    ```json
    {
    "name": "$return",
    "type": "http",
    "direction": "out"
    }
    ```

1. Aggiornare anche la proprietà **entryPoint** nella parte inferiore del file in modo che usi un metodo chiamato **"Add2"**, come indicato di seguito. Lo scopo è dimostrare che il percorso **api/Adder...** può eseguire il mapping a un metodo appropriato con qualsiasi nome (in questo caso **Add2**).

    ```json
    "entryPoint": "<project-name>.<function-class-name>.Add2"
    ```

1. Il file **function.json** finale avrà un aspetto simile al seguente:

    ```json
    {
    "bindings": [
        {
        "type": "httpTrigger",
        "methods": [
            "get"
        ],
        "authLevel": "function",
        "direction": "in",
        "name": "req",
        "route": "Adder/{x:int?}/{y:int?}"
        },
        {
        "name": "$return",
        "type": "http",
        "direction": "out"
        }
    ],
    "disabled": false,
    "scriptFile": "../bin/AzureFunctionsProject.dll",
    "entryPoint": "AzureFunctionsProject.Add.Add2"
    }
    ```

1. Il passaggio finale necessario per attivare il funzionamento del progetto è un'istruzione che richiede a Visual Studio per Mac di copiare il file nello stesso percorso relativo della directory di output ogni volta che viene modificato. Con il file selezionato, scegliere la scheda delle proprietà sulla barra a destra, quindi in **Copia nella directory di output** selezionare **Copia se più recente**:

    ![Opzioni delle proprietà per il file con estensione json](media/azure-functions-lab-image30.png)

1. In **Add.cs** sostituire il metodo `Run` (incluso l'attributo) con il metodo seguente per completare la funzione prevista. Il metodo è molto simile a `Run`, ma non usa attributi e dispone di parametri espliciti per **x** e **y**.

    ```csharp
    public static int Add2(
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        return x + y;
    }
    ```

1. Premere **F5** per compilare ed eseguire il progetto.

1. Dopo il completamento della compilazione e l'avvio della piattaforma, questa indica che è disponibile una seconda route per le richieste, mappata sul metodo appena aggiunto:

    ![URL per le funzioni Http](media/azure-functions-lab-image31.png)

1. Tornare alla finestra del browser e passare a **http://localhost:7071/api/Adder/3/5** .

1. Ora il metodo funziona di nuovo ed estrae parametri dal percorso, quindi produce una somma.

1. Tornare a **Visual Studio per Mac** e terminare la sessione di debug.

## <a name="exercise-5-working-with-azure-storage-tables"></a>Esercizio 5: Uso delle tabelle di archiviazione di Azure

Spesso il servizio compilato è molto più complesso di quello creato fino a questo punto e la sua esecuzione può richiedere un'infrastruttura e tempi molto maggiori. In questi casi può risultare utile accettare le richieste che vengono messe in coda per l'elaborazione quando le risorse diventano disponibili. Le funzioni di Azure supportano questo approccio. In altri casi risulta più utile archiviare i dati in modo centralizzato. Le tabelle di Archiviazione di Azure consentono di eseguire questa operazione rapidamente.

1. Aggiungere la classe seguente a **Add.cs**. La classe deve essere inserita all'interno dello spazio dei nomi, ma all'esterno della classe esistente.

    ```csharp
    public class TableRow : TableEntity
    {
        public int X { get; set; }
        public int Y { get; set; }
        public int Sum { get; set; }
    }
    ```

1. Nella classe **Add** aggiungere il codice seguente per introdurre un'altra funzione. Si noti che fino a questo punto il codice è univoco, in quanto non prevede una risposta HTTP. La riga finale restituisce un nuovo elemento **TableRow** completo di alcuni dati chiave che ne faciliteranno il recupero in una fase successiva (**PartitionKey** e **RowKey**), nonché dei relativi parametri e della somma. Anche il codice all'interno del metodo usa **TraceWriter** per facilitare il rilevamento dell'esecuzione della funzione.

    ```csharp
    [FunctionName("Process")]
    [return: Table("Results")]
    public static TableRow Process(
        [HttpTrigger(AuthorizationLevel.Function, "get",
            Route = "Process/{x:int}/{y:int}")]
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        log.Info($"Processing {x} + {y}");

        return new TableRow()
        {
            PartitionKey = "sums",
            RowKey = $"{x}_{y}",
            X = x,
            Y = y,
            Sum = x + y
        };
    }
    ```

1. Premere **F5** per compilare ed eseguire il progetto.

1. Nella scheda del browser passare a **http://localhost:7071/api/Process/4/6** . Questa operazione inserisce un altro messaggio nella coda, che a sua volta aggiungerà un'altra riga alla tabella in un secondo momento.

1. Tornare a **Terminal** e verificare la richiesta in ingresso per **4 + 6**.

    ![Output di Terminal con richiesta di addizione](media/azure-functions-lab-image32.png)

1. Tornare al browser per aggiornare la richiesta con lo stesso URL. Questa volta verrà visualizzato un errore dopo il metodo **Process**. Questo avviene perché il codice prova ad aggiungere una riga alla tabella di Archiviazione tabelle di Azure tramite una combinazione di partizione e chiave riga che esiste già.

    ```
    System.Private.CoreLib: Exception while executing function: Process. Microsoft.Azure.WebJobs.Host: Error while handling parameter $return after function returned:. Microsoft.Azure.WebJobs.Host: The specified entity already exists.
    ```

1. Arrestare la sessione di debug.

1. Per correggere l'errore, aggiungere il parametro seguente alla definizione del metodo, immediatamente prima del parametro **TraceWriter**. Questo parametro richiede alla piattaforma Funzioni di Azure di provare il recupero di una **TableRow** dalla tabella **Results** per la **PartitionKey** usata per l'archiviazione dei risultati. Tuttavia sarà sorprendente notare che **RowKey** viene generata dinamicamente in base agli altri parametri **x** e **y** per lo stesso metodo. Se tale riga esiste già, **tableRow** la includerà quando inizia l'esecuzione del metodo, senza richiedere lavoro aggiuntivo allo sviluppatore. Se la riga non esiste, il valore sarà null. Questo tipo di efficienza consente agli sviluppatori di concentrarsi sulla logica di business importante anziché sull'infrastruttura.

    ```csharp
    [Table("Results", "sums", "{x}_{y}")]
    TableRow tableRow,
    ```

1. Aggiungere il codice seguente all'inizio del metodo. Se **tableRow** non è null, i risultati per l'operazione richiesta sono già disponibili e possono essere restituiti immediatamente. In caso contrario, l'esecuzione della funzione continua come in precedenza. Questo potrebbe non essere il modo più efficiente per restituire i dati, ma dimostra che è possibile organizzare operazioni molto sofisticate su più livelli scalabili con un volume di codice molto ridotto.

    ```csharp
    if (tableRow != null)
    {
        log.Info($"{x} + {y} already exists");
        return null;
    }
    ```

1. Premere **F5** per compilare ed eseguire il progetto.

1. Nella scheda del browser aggiornare l'URL in **http://localhost:7071/api/Process/4/6** . Dato che la riga della tabella per questo record esiste, viene restituita immediatamente e senza errori. Poiché non esiste alcun output HTTP, è possibile visualizzare l'output nel Terminale.

    ![Output nel Terminale indicante che la riga della tabella esiste già](media/azure-functions-lab-image33.png)

1. Aggiornare l'URL in modo che rifletta una combinazione non ancora testata, ad esempio **http://localhost:7071/api/Process/5/7** . Si noti il messaggio nel Terminale, indicante che la riga della tabella non è stata trovata (come previsto).

    ![Output nel Terminale che visualizza il nuovo processo](media/azure-functions-lab-image34.png)

1. Tornare a **Visual Studio per Mac** e terminare la sessione di debug.

<!--
1. Finally, let's take a look at what it's like to work with multiple input records. Rather than specify a specific **TableRow**, you can request an **IQueryable<TableRow>** using the same attributes, and the runtime will fill it with the appropriate resource you need. Add the code below to create a **List** function that lists all items that currently exist in the Azure table we've been working with. Also note that we're specifying that the MIME type of the response is **application/json**, so the runtime will automatically render as JSON.

    ```csharp
    [FunctionName("List")]
    public static HttpResponseMessage List(
        [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
        HttpRequestMessage req,
        [Table("Results", "sums")]
        IQueryable<TableRow> table,
        TraceWriter log)
    {
        return req.CreateResponse(HttpStatusCode.OK, table, "application/json");
    }
    ```
1. Press **F5** to build and run the project.

1. In the browser tab, navigate to **http://localhost:7071/api/List**. This should pull down the list of all items in the Azure table and render it as JSON.

    ![](https://user-images.githubusercontent.com/3944468/29033725-be9d5a5e-7b4a-11e7-8b55-df0a200b6320.png)
-->

## <a name="summary"></a>Riepilogo

In questa esercitazione si è appreso come iniziare a creare le funzioni di Azure tramite Visual Studio per Mac.
