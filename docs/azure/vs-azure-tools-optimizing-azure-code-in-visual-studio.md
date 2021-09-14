---
title: Ottimizzazione del codice di Azure
description: Informazioni su come il codice di Azure come strumento di ottimizzazione in Visual Studio consente di rendere il codice più affidabile e migliorare le prestazioni.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 9836f13ac97641876746e0c514f11efc297d2975
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633092"
---
# <a name="optimizing-your-azure-code"></a>Ottimizzare il codice Azure
Quando si programmano app che utilizzano Microsoft Azure, esistono alcune procedure consigliate da seguire per evitare problemi con la scalabilità di app, il comportamento e le prestazioni in un ambiente cloud. Microsoft fornisce uno strumento di analisi del codice di Azure che riconosce molti di questi problemi comunemente riscontrati e aiuta a risolverli. È possibile scaricare lo strumento in Visual Studio tramite NuGet.

## <a name="azure-code-analysis-rules"></a>Regole di analisi codice di Azure
Lo strumento di analisi del codice di Azure utilizza le regole seguenti per contrassegnare automaticamente il codice di Azure quando rileva i problemi noti che influiscono sulle prestazioni. I problemi rilevati vengono visualizzati come avvisi o errori del compilatore. Correzioni del codice o suggerimenti per risolvere l'avviso o l’errore vengono spesso forniti tramite un'icona a forma di lampadina.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Evitare di utilizzare la modalità stato sessione (in-process) predefinita
### <a name="id"></a>ID
AP0000

### <a name="description"></a>Descrizione
Se si utilizza la modalità di stato sessione (in-process) predefinita per le applicazioni cloud, è possibile perdere lo stato della sessione.

Condividere le idee e i suggerimenti nei [Commenti e suggerimenti dell'analisi del codice di Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
Per impostazione predefinita, la modalità stato sessione specificata nel file Web. config è in corso. Inoltre, se nessuna voce è specificata nel file di configurazione, la modalità di stato della sessione è predefinita per in-process. La modalità in-process memorizza lo stato della sessione sul server web. Quando un'istanza viene riavviata o una nuova istanza viene utilizzata per il bilanciamento del carico o il supporto di failover, non viene salvato lo stato della sessione archiviato in memoria sul server web. Questa situazione impedisce che l'applicazione sia scalabile nel cloud.

Lo stato della sessione ASP.NET supporta diverse opzioni di archiviazione per i dati dello stato sessione: InProc, StateServer, SQLServer, personalizzato e Off. È consigliabile utilizzare la modalità personalizzata per ospitare i dati in un archivio esterno dello stato della sessione, ad esempio [Provider di stato della sessione di Azure per Redis](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/).

### <a name="solution"></a>Soluzione
Una soluzione consigliata consiste nell'archiviare lo stato della sessione in un servizio cache gestito. Informazioni su come utilizzare [il provider di stato della sessione di Azure per Redis](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/) per archiviare lo stato della sessione. È anche possibile archiviare lo stato della sessione in altre posizioni per garantire che l'applicazione sia scalabile nel cloud. Per ulteriori informazioni sulle soluzioni alternative, leggere [Modalità dello stato di sessione](/previous-versions/ms178586(v=vs.140)).

## <a name="run-method-should-not-be-async"></a>L’esecuzione del metodo non deve essere asincrona
### <a name="id"></a>ID
AP1000

### <a name="description"></a>Descrizione
Creare metodi asincroni, ad esempio [await](/dotnet/csharp/language-reference/operators/await), fuori dal metodo [Run ()](/previous-versions/azure/reference/ee772746(v=azure.100)) e quindi chiamare i metodi asincroni da [Run ()](/previous-versions/azure/reference/ee772746(v=azure.100)). La dichiarazione del metodo [[Run ()](/previous-versions/azure/reference/ee772746(v=azure.100))](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) come asincrona fa sì che il ruolo di lavoro immetta un ciclo di riavvio.

Condividere le idee e i suggerimenti nei [Commenti e suggerimenti dell'analisi del codice di Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
La chiamata di metodi asincroni all'interno del metodo [Run()](/previous-versions/azure/reference/ee772746(v=azure.100)) fa sì che il runtime del servizio cloud ricicli il ruolo di lavoro. Quando viene avviato un ruolo di lavoro, l'esecuzione del programma ha luogo all'interno del metodo [Run()](/previous-versions/azure/reference/ee772746(v=azure.100)). Se si esce dal metodo Run, il ruolo di lavoro viene riavviato. Quando il runtime di ruolo di lavoro raggiunge il metodo asincrono, invia tutte le operazioni dopo il metodo asincrono e poi ritorna  In questo modo il ruolo di lavoro viene chiuso dal metodo Run e riavviato. Nell'iterazione successiva dell'esecuzione, il ruolo di lavoro raggiunge nuovamente il metodo asincrono e viene riavviato, causando nuovamente il riciclo anche del ruolo di lavoro.

### <a name="solution"></a>Soluzione
Posizionare tutte le operazioni asincrone fuori dal metodo [Run](/previous-versions/azure/reference/ee772746(v=azure.100)) . Chiamare quindi il metodo asincrono di cui è stato eseguito il refactoring dall'interno del metodo Run, ad esempio RunAsync().wait. Lo strumento di analisi del codice di Azure può aiutare a risolvere il problema.

Il seguente frammento di codice dimostra la correzione del codice per questo problema:

```csharp
public override void Run()
{
    RunAsync().Wait();
}

public async Task RunAsync()
{
    //Asynchronous operations code logic
    // This is a sample worker implementation. Replace with your logic.

    Trace.TraceInformation("WorkerRole1 entry point called");

    HttpClient client = new HttpClient();

    Task<string> urlString = client.GetStringAsync("https://msdn.microsoft.com");

    while (true)
    {
        Thread.Sleep(10000);
        Trace.TraceInformation("Working");

        string stream = await urlString;
    }

}
```

## <a name="use-service-bus-shared-access-signature-authentication"></a>Autenticazione della firma di accesso condiviso con il bus di servizio
### <a name="id"></a>ID
AP2000

### <a name="description"></a>Descrizione
Uso della firma di accesso condiviso per l’autenticazione. Il servizio di controllo di accesso (ACS) è deprecato per l'autenticazione di bus di servizio.

Condividere le idee e i suggerimenti nei [Commenti e suggerimenti dell'analisi del codice di Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
Per una sicurezza ottimale, Azure Active Directory consiste nella sostituzione dell’autenticazione ACS con l'autenticazione SAS. Vedere [Azure Active Directory è il futuro di ACS](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) per informazioni sul piano di transizione.

### <a name="solution"></a>Soluzione
Utilizzare l'autenticazione SAS nelle app. Nell'esempio seguente viene illustrato come utilizzare un token SAS esistente per accedere a uno spazio dei nomi o a un’entità del bus di servizio.

```csharp
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Per altre informazioni, vedere gli argomenti seguenti.

* Per una panoramica, vedere [autenticazione della firma di accesso condiviso con il bus di servizio](/azure/service-bus-messaging/service-bus-sas)
* [Come usare l'autenticazione della firma di accesso condiviso con il bus di servizio](/azure/service-bus-messaging/service-bus-sas)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>È consigliabile utilizzare il metodo OnMessage per evitare il "ciclo di ricezione"
### <a name="id"></a>ID
AP2002

### <a name="description"></a>Descrizione
Per evitare di entrare in un "ciclo di ricezione" la chiamata al metodo **OnMessage** è una soluzione ottimale, poi chiamare il metodo **Receive**. Tuttavia, se è necessario utilizzare il metodo **Ricezione** e si specifica un tempo di attesa del server non predefinito, assicurarsi che il tempo di attesa del server sia più di un minuto.

Condividere le idee e i suggerimenti nei [Commenti e suggerimenti dell'analisi del codice di Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
Quando si chiama **OnMessage**, il client avvia un message pump interno che esegue costantemente il polling della coda o della sottoscrizione. Questo pump del messaggio contiene un ciclo infinito che emette una chiamata per ricevere messaggi. Se la chiamata scade, genera una nuova chiamata. L'intervallo di timeout è determinato dal valore della proprietà [OperationTimeout](/dotnet/api/microsoft.servicebus.messaging.messagingfactorysettings) del [MessagingFactory](/dotnet/api/microsoft.servicebus.messaging.messagingfactory) che viene usato.

Il vantaggio dell'uso di **OnMessage** rispetto a **Receive** è che gli utenti non devono eseguire manualmente il polling dei messaggi, gestire le eccezioni, elaborare più messaggi in parallelo e completare i messaggi.

Se si chiama la **Ricezione** senza utilizzare il valore predefinito, assicurarsi che il valore *ServerWaitTime* sia superiore a un minuto. L'impostazione di *ServerWaitTime* a più di un minuto impedisce al server di scadere prima che il messaggio venga ricevuto completamente.

### <a name="solution"></a>Soluzione
Vedere gli esempi di codice seguenti per gli utilizzi consigliati. Per altre informazioni, vedere [Metodo QueueClient.OnMessage (Microsoft.ServiceBus.Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient) e [Metodo QueueClient.Receive (Microsoft.ServiceBus.Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient).

Per migliorare le prestazioni dell'infrastruttura di messaggistica di Azure, vedere il modello di progettazione [Nozioni di base di messaggistica asincrona](/previous-versions/msp-n-p/dn589781(v=pandp.10)).

Il seguente è un esempio dell'utilizzo di **OnMessage** per ricevere i messaggi.

```csharp
void ReceiveMessages()
{
    // Initialize message pump options.
    OnMessageOptions options = new OnMessageOptions();
    options.AutoComplete = true; // Indicates if the message-pump should call complete on messages after the callback has completed processing.
    options.MaxConcurrentCalls = 1; // Indicates the maximum number of concurrent calls to the callback the pump should initiate.
    options.ExceptionReceived += LogErrors; // Enables you to get notified of any errors encountered by the message pump.

    // Start receiving messages.
    QueueClient client = QueueClient.Create("myQueue");
    client.OnMessage((receivedMessage) => // Initiates the message pump and callback is invoked for each message that is received, calling close on the client will stop the pump.
    {
        // Process the message.
    }, options);
    Console.WriteLine("Press any key to exit.");
    Console.ReadKey();
```

Il seguente è un esempio dell'utilizzo di **Ricezione** con il tempo di attesa predefinito del server.

```csharp
string connectionString =
CloudConfigurationManager.GetSetting("Microsoft.ServiceBus.ConnectionString");

QueueClient Client =
    QueueClient.CreateFromConnectionString(connectionString, "TestQueue");

while (true)
{
   BrokeredMessage message = Client.Receive();
   if (message != null)
   {
      try
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
```

Il seguente è un esempio dell'utilizzo di **Ricezione** con il tempo di attesa non predefinito del server.

```csharp
while (true)
{
   BrokeredMessage message = Client.Receive(new TimeSpan(0,1,0));

   if (message != null)
   {
      try
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
}
```

## <a name="consider-using-asynchronous-service-bus-methods"></a>Si consideri l'utilizzo di metodi asincroni del Bus di servizio
### <a name="id"></a>ID
AP2003

### <a name="description"></a>Descrizione
Utilizzare i metodi asincroni del Bus di servizio per migliorare le prestazioni con la messaggistica negoziata.

Condividere le idee e i suggerimenti nei [Commenti e suggerimenti dell'analisi del codice di Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
L’utilizzo di metodi asincroni consente la concorrenza del programma di applicazione perché l'esecuzione di ogni chiamata non blocca il thread principale. Quando si utilizzano i metodi di messaggistica del Bus di servizio, l’esecuzione di un'operazione (inviare, ricevere, eliminare, ecc) richiede tempo. Questa volta include l'elaborazione dell'operazione dal servizio Bus di servizio oltre alla latenza della richiesta e risposta. Per aumentare il numero di operazioni per volta, è necessario eseguire le operazioni contemporaneamente. Per altre informazioni, consultare le [Procedure consigliate per il miglioramento delle prestazioni tramite la messaggistica negoziata del bus di servizio](/previous-versions/azure/hh528527(v=azure.100)).

### <a name="solution"></a>Soluzione
Vedere [QueueClient class (Microsoft.ServiceBus.Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient) per ricevere informazioni su come utilizzare il metodo asincrono consigliato.

Per migliorare le prestazioni dell'infrastruttura di messaggistica di Azure, vedere il modello di progettazione [Nozioni di base di messaggistica asincrona](/previous-versions/msp-n-p/dn589781(v=pandp.10)).

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Prendere in considerazione il partizionamento delle code e degli argomenti del bus di servizio.
### <a name="id"></a>ID
AP2004

### <a name="description"></a>Descrizione
Esegue il partizionamento delle code e degli argomenti del bus di servizio per ottenere prestazioni migliori con la messaggistica del bus di servizio.

Condividere le idee e i suggerimenti nei [Commenti e suggerimenti dell'analisi del codice di Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
Il partizionamento delle code e degli argomenti del bus di servizio permette di aumentare la disponibilità dei servizi e la velocità effettiva delle prestazioni, perché la velocità effettiva complessiva di una coda o di un argomento partizionato non è più limitata dalle prestazioni di un singolo broker messaggi o archivio di messaggistica. Una interruzione temporanea di un archivio di messaggistica non influisce sulla disponibilità di code e argomenti partizionati. Per ulteriori informazioni, vedere [Partizionamento delle entità di messaggistica](/previous-versions/azure/dn520246(v=azure.100)).

### <a name="solution"></a>Soluzione
Il seguente frammento di codice mostra come suddividere le entità di messaggistica.

```csharp
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Per altre informazioni, vedere il blog di Microsoft Azure [Partitioned Service Bus Queues and Topics](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) (Code e argomenti partizionati del bus di servizio) e l'esempio [Microsoft Azure Service Bus Partitioned Queue](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f) (Coda partizionata del bus di servizio di Microsoft Azure).

## <a name="do-not-set-sharedaccessstarttime"></a>Non impostare SharedAccessStartTime
### <a name="id"></a>ID
AP3001

### <a name="description"></a>Descrizione
È consigliabile evitare l'utilizzo di SharedAccessStartTimeset all'ora corrente per avviare immediatamente il criterio di accesso condiviso. È sufficiente impostare questa proprietà se si desidera avviare i criteri di accesso condivisi in un secondo momento.

Condividere le idee e i suggerimenti nei [Commenti e suggerimenti dell'analisi del codice di Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
La sincronizzazione dell'orologio comporta una differenza oraria lieve tra i Data Center. Ad esempio, si pensa logicamente che impostando l'ora di inizio di un archivio criteri SAS come l'ora corrente utilizzando Now o un metodo simile si farà sì che i criteri SAS abbiano effetto immediato. Tuttavia, le differenze lievi di tempo tra i Data Center possono provocare problemi con questo poiché alcuni tempi del datacenter potrebbero essere leggermente oltre l'ora di inizio, mentre altri la precedono. Di conseguenza, i criteri di firma di accesso condiviso possono scadere rapidamente (o persino immediatamente) se la durata di criteri è troppo breve.

Per ulteriori informazioni sull'utilizzo di firma di accesso condiviso sull'archiviazione di Azure, vedere [Introduzione della tabella SAS (Shared Access Signature) della coda SAS coda del BLOB SAS - Blog del Team Microsoft Azure Storage - Home page - sito blog di MSDN](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/).

### <a name="solution"></a>Soluzione
Rimuovere l'istruzione che imposta l'ora di inizio del criterio di accesso condiviso. Lo strumento di analisi del codice di Azure fornisce una correzione per questo problema. Per ulteriori informazioni sulla gestione della protezione, vedere il modello di progettazione [Modello passepartout](/previous-versions/msp-n-p/dn568102(v=pandp.10)).

Il seguente frammento di codice dimostra la correzione del codice per questo problema.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>L’ora di scadenza del criterio di accesso condiviso deve essere più di cinque minuti 
### <a name="id"></a>ID
AP3002

### <a name="description"></a>Descrizione
Può esistere una differenza di circa cinque minuti negli orologi tra i Data Center in posizioni diverse a causa di una condizione nota come "sfasamento." Per evitare che il token del criterio SAS scada prima del previsto, impostare l'ora di scadenza a più di cinque minuti.

Condividere le idee e i suggerimenti nei [Commenti e suggerimenti dell'analisi del codice di Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
I dataenter in diverse località del mondo sono sincronizzati da un segnale di orologio. Poiché occorre tempo affinché il segnale dell’orologio viaggi in località diverse, può esistere una varianza di tempo tra i datacenter in località geografiche diverse anche se apparentemente tutto ciò viene sincronizzato. Questa differenza di tempo può influenzare l’inizio del tempo dell'accesso condiviso e dell’intervallo di scadenza dei criteri. Per verificare che il criterio di accesso condiviso diventi effettivo immediatamente, pertanto, non specificare l'ora di inizio. Inoltre, assicurarsi che l'ora di scadenza sia maggiore di 5 minuti per evitare una scadenza anticipata.

Per ulteriori informazioni sull'utilizzo di firma di accesso condiviso sull'archiviazione di Azure, vedere [Introduzione della tabella SAS (Shared Access Signature) della coda SAS coda del BLOB SAS - Blog del Team Microsoft Azure Storage - Home page - sito blog di MSDN](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/).

### <a name="solution"></a>Soluzione
Per ulteriori informazioni sulla gestione della protezione, vedere il modello di progettazione [Modello passepartout](/previous-versions/msp-n-p/dn568102(v=pandp.10)).

Di seguito è riportato un esempio di ora di inizio dei criteri di accesso condiviso non specificata.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

Di seguito è riportato un esempio di un'ora di inizio dei criteri di accesso condiviso specificata, con un periodo di scadenza dei criteri maggiore di cinque minuti.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
  SharedAccessStartTime = new DateTime(2014,1,20),
 SharedAccessExpiryTime = new DateTime(2014, 1, 21),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

Per altre informazioni, vedere [Configurare l'accesso in lettura pubblico anonimo per contenitori e BLOB.](/azure/storage/blobs/anonymous-read-access-configure?tabs=portal)

## <a name="use-cloudconfigurationmanager"></a>Utilizzare CloudConfigurationManager
### <a name="id"></a>ID
AP4000

### <a name="description"></a>Descrizione
Usando la classe [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) per progetti, come il sito Web di Azure e i servizi mobili di Azure, non si verificano problemi di runtime. Come procedura consigliata, tuttavia, è consigliabile usare Cloud [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) come modo unificato di gestione delle configurazioni per tutte le applicazioni Cloud di Azure.

Condividere le idee e i suggerimenti nei [Commenti e suggerimenti dell'analisi del codice di Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
CloudConfigurationManager legge il file di configurazione appropriato per l'ambiente dell'applicazione.

[CloudConfigurationManager](/previous-versions/azure/)

### <a name="solution"></a>Soluzione
Effettuare il refactoring del codice per utilizzare il [CloudConfigurationManager classe](/previous-versions/azure/reference/mt634650(v=azure.100)). Una correzione del codice per questo problema viene fornita dallo strumento di analisi del codice di Azure.

Il seguente frammento di codice dimostra la correzione del codice per questo problema. Sostituisci

`var settings = ConfigurationManager.AppSettings["mySettings"];`

con

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

Di seguito è riportato un esempio di come archiviare l'impostazione di configurazione in un file app. config o Web. config. Aggiungere le impostazioni per la sezione appSettings del file di configurazione. Di seguito è il file Web. config per l'esempio di codice precedente.

```xml
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>
```

## <a name="avoid-using-hard-coded-connection-strings"></a>Evitare di utilizzare stringhe di connessione hardcoded
### <a name="id"></a>ID
AP4001

### <a name="description"></a>Descrizione
Se si utilizzano stringhe di connessione hardcoded ed è necessario aggiornarle in un secondo momento, sarà necessario apportare modifiche al codice sorgente e ricompilare l'applicazione. Tuttavia, se si archiviano le stringhe di connessione in un file di configurazione, è possibile cambiarle successivamente semplicemente aggiornando il file di configurazione.

Condividere le idee e i suggerimenti nei [Commenti e suggerimenti dell'analisi del codice di Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
Impostare come hardcoded le stringhe di connessione è sconsigliato perché presenta problemi quando è necessario modificare rapidamente le stringhe di connessione. Inoltre, se il progetto deve essere controllato nel codice sorgente, le stringhe di connessione hardcoded presentano una vulnerabilità di protezione poiché le stringhe possono essere visualizzate nel codice sorgente.

### <a name="solution"></a>Soluzione
Archiviare le stringhe di connessione nel file di configurazione o negli ambienti di Azure.

* Per le applicazioni autonome utilizzare la config. dell’app per archiviare le impostazioni della stringa di connessione.
* Per le applicazioni web ospitate in IIS, utilizzare config. web per archiviare le stringhe di connessione.
* Per le applicazioni ASP.NET vNext utilizzare configuration.json per archiviare le stringhe di connessione.

Per informazioni sull'uso di file di configurazione, ad esempio web.config o app. config, vedere [Linee guida configurazione di ASP.NET Web](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/web-config-transformations). Per informazioni su come funzionano le variabili di ambiente di Azure, vedere [Azure Web Sites: How Application Strings and Connection Strings Work](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/) (Siti Web di Microsoft Azure sul funzionamento delle stringhe di applicazione e di connessione). Per informazioni sull'archiviazione della stringa di connessione nel codice sorgente, vedere [evitare di inserire informazioni riservate come le stringhe di connessione nei file archiviati nel repository del codice sorgente](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control).

## <a name="use-diagnostics-configuration-file"></a>Utilizzo del file di configurazione di Diagnostica.
### <a name="id"></a>ID
AP5000

### <a name="description"></a>Descrizione
Anziché configurare le impostazioni di diagnostica nel codice, ad esempio tramite l'API di programmazione della diagnostica di Microsoft.WindowsAzure, è necessario configurare le impostazioni di diagnostica nel file diagnostics wadcfg. (O, diagnostics.wadcfgx se si utilizza Azure SDK 2.5). In questo modo è possibile modificare le impostazioni di diagnostica senza dover ricompilare il codice.

Condividere le idee e i suggerimenti nei [Commenti e suggerimenti dell'analisi del codice di Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
Prima di Azure SDK 2.5 (che utilizza diagnostica Microsoft Azure 1.3), la diagnostica di Azure (WAD) può essere configurata utilizzando diversi metodi: aggiunta del BLOB di configurazione nel servizio di archiviazione, utilizzando il codice imperativo, la configurazione dichiarativa o la configurazione predefinita. Il modo migliore per configurare la diagnostica consiste tuttavia nell'usare un file di configurazione XML (diagnostics.wadcfg o diagnostics.wadcfgx per SDK 2.5 e versioni successive)nel progetto di applicazione. In questo approccio, il file diagnostics wadcfg definisce completamente la configurazione e può essere aggiornato e ridistribuito a suo piacimento. Combinare l'uso del file di configurazione wadcfg con i metodi a livello di codice di impostazione delle configurazioni tramite le classi [Diagnosticmonitorconfiguration](/previous-versions/azure/reference/ee758597(v=azure.100)) o [RoleInstanceDiagnosticManager](/previous-versions/azure/reference/ee773157(v=azure.100)) può generare confusione. Vedere [Avviare o modificare la configurazione della diagnostica di Azure](/previous-versions/azure/hh411537(v=azure.100)) per ulteriori informazioni.

A partire da 1.3 WAD (incluso in Azure SDK 2.5), non è più possibile utilizzare il codice per configurare la diagnostica. Di conseguenza, è possibile specificare solo la configurazione quando si applica o si aggiorna l'estensione di diagnostica.

### <a name="solution"></a>Soluzione
Usare la finestra di progettazione di configurazione di diagnostica per spostare le impostazioni di diagnostica nel file di configurazione di diagnostica (diagnositcs.wadcfg o diagnostics.wadcfgx per SDK 2.5 e versioni successive). È inoltre consigliabile installare [Azure SDK 2.5](https://social.msdn.microsoft.com/Forums/en-US/home) e utilizzare la funzionalità di diagnostica più recente.

1. Dal menu di scelta rapida per il ruolo desiderato scegliere Proprietà, quindi selezionare la scheda Configurazione.
2. Nella sezione **Diagnostica** assicurarsi che la casella di controllo **Abilita diagnostica** sia selezionata.
3. Fare clic sul pulsante **Configura**.

   ![Accesso all'opzione Abilita diagnostica](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   Vedere [Configurazione della diagnostica per i servizi cloud e le macchine virtuali di Azure](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) .per ulteriori informazioni.

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>Evitare di dichiarare gli oggetti DbContext come static
### <a name="id"></a>ID
AP6000

### <a name="description"></a>Descrizione
Per conservare memoria, evitare di dichiarare gli oggetti DbContext come static

Condividere le idee e i suggerimenti nei [Commenti e suggerimenti dell'analisi del codice di Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Motivo
Gli oggetti DBContext contengono i risultati della query da ogni chiamata. Gli oggetti DBContext statici non vengono eliminati fino a quando non viene scaricato il dominio dell'applicazione. Pertanto, un oggetto DBContext statico può utilizzare grandi quantità di memoria.

### <a name="solution"></a>Soluzione
Dichiarare DBContext come una variabile locale o un campo di istanza non statico, utilizzarlo per un'attività e poi eliminarlo dopo l'uso.

Il seguente esempio di classe controller MVC illustra come utilizzare l'oggetto DBContext.

```csharp
public class BlogsController : Controller
    {
        //BloggingContext is a subclass to DbContext
        private BloggingContext db = new BloggingContext();
        // GET: Blogs
        public ActionResult Index()
        {
            //business logics…
            return View();
        }
        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                db.Dispose();
            }
            base.Dispose(disposing);
        }
    }
```

## <a name="next-steps"></a>Passaggi successivi
Per altre informazioni sull'ottimizzazione e la risoluzione dei problemi delle app Azure, vedere [Risoluzione dei problemi di un'app Web nel servizio app di Azure tramite Visual Studio](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio).
