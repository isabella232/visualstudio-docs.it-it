---
title: Ottimizzazione del codice di Azure in Visual Studio | Microsoft Docs
description: Informazioni sul codice di Azure come strumento di ottimizzazione in Visual Studio consentono di rendere il codice più affidabile e migliorare le prestazioni.
author: ghogen
manager: douge
ms.assetid: ed48ee06-e2d2-4322-af22-07200fb16987
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: d1d0f5a69015a6c6596e1a2b7ee85b12f4116d6b
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002520"
---
# <a name="optimizing-your-azure-code"></a>Ottimizzazione del codice di Azure
Quando si programmano App che usano Microsoft Azure, esistono alcune procedure consigliate da seguire per evitare problemi con la scalabilità di app, il comportamento e le prestazioni in un ambiente cloud. Microsoft fornisce uno strumento di analisi del codice di Azure che riconosce molti di questi problemi comunemente riscontrati e aiuta a risolverli. È possibile scaricare lo strumento in Visual Studio tramite NuGet.

## <a name="azure-code-analysis-rules"></a>Regole di analisi del codice di Azure
Lo strumento di analisi del codice di Azure Usa le regole seguenti per contrassegnare automaticamente il codice di Azure quando vengono rilevati problemi noti di influire sulle prestazioni. Rilevati problemi vengono visualizzati come avvisi o errori del compilatore. Le correzioni del codice o suggerimenti per risolvere l'avviso o errore vengono spesso forniti tramite un'icona lampadina.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Evitare di usare la modalità stato sessione (in-process) predefinita
### <a name="id"></a>Id
AP0000

### <a name="description"></a>Descrizione
Se si usa la modalità di stato sessione (in-process) predefinita per le applicazioni cloud, è possibile perdere lo stato della sessione.

Per condividere le idee, commenti e suggerimenti [commenti e suggerimenti dell'analisi del codice di Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
Per impostazione predefinita, la modalità stato sessione specificata nel file Web. config viene in-process. Inoltre, se nessuna voce specificata nel file di configurazione, la modalità di stato della sessione predefinita per in-process. La modalità in-process memorizza lo stato della sessione in memoria nel server web. Quando un'istanza viene riavviata o una nuova istanza viene utilizzata per il bilanciamento del carico o un supporto per il failover, non viene salvato lo stato della sessione archiviato in memoria nel server web. Questa situazione impedisce che l'applicazione sia scalabile nel cloud.

Stato della sessione ASP.NET supporta diverse opzioni di archiviazione per i dati dello stato della sessione: InProc, StateServer, SQLServer, personalizzato e Off. È consigliabile usare la modalità Custom per ospitare i dati in un archivio esterno dello stato della sessione, ad esempio [provider di stato della sessione di Azure per Redis](http://go.microsoft.com/fwlink/?LinkId=401521).

### <a name="solution"></a>Soluzione
Una soluzione consigliata consiste nell'archiviare lo stato della sessione in un servizio cache gestita. Informazioni su come usare [provider di stato della sessione di Azure per Redis](http://go.microsoft.com/fwlink/?LinkId=401521) per archiviare lo stato della sessione. È anche possibile archiviare lo stato della sessione in altre posizioni per assicurarsi che l'applicazione sia scalabile nel cloud. Per altre informazioni sulle soluzioni alternative, leggere [modalità stato sessione](https://msdn.microsoft.com/library/ms178586).

## <a name="run-method-should-not-be-async"></a>Metodo di esecuzione non deve essere asincrona
### <a name="id"></a>Id
AP1000

### <a name="description"></a>Descrizione
Creare metodi asincroni (ad esempio [await](https://msdn.microsoft.com/library/hh156528.aspx)) all'esterno del [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metodo e quindi chiamare i metodi asincroni da [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx). Dichiarare la [ [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metodo come asincrona fa sì che il ruolo di lavoro immetta un ciclo di riavvio.

Per condividere le idee, commenti e suggerimenti [commenti e suggerimenti dell'analisi del codice di Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
Chiamata di metodi asincroni all'interno di [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metodo fa in modo che il runtime del servizio cloud riciclare il ruolo di lavoro. Quando viene avviato un ruolo di lavoro, l'esecuzione del programma avviene all'interno di [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) (metodo). Chiusura di [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metodo fa sì che il ruolo di lavoro da riavviare. Quando il runtime di ruolo di lavoro raggiunge il metodo asincrono, invia tutte le operazioni dopo il metodo asincrono e restituisce. In questo modo il ruolo di lavoro da cui uscire il [ [ [ [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) (metodo) e riavviare. Nell'iterazione successiva dell'esecuzione, il ruolo di lavoro raggiunge nuovamente il metodo asincrono e viene riavviato, causando il riciclo anche in questo caso anche il ruolo di lavoro.

### <a name="solution"></a>Soluzione
Posizionare tutte le operazioni asincrone fuori il [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) (metodo). Quindi, chiamare il metodo asincrono refactoring dall'interno di [ [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metodo, ad esempio RunAsync () Wait. Lo strumento di analisi del codice di Azure può aiutare a risolvere il problema.

Il frammento di codice seguente dimostra la correzione del codice per risolvere questo problema:

```
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

    Task<string> urlString = client.GetStringAsync("http://msdn.microsoft.com");

    while (true)
    {
        Thread.Sleep(10000);
        Trace.TraceInformation("Working");

        string stream = await urlString;
    }

}
```

## <a name="use-service-bus-shared-access-signature-authentication"></a>Usare l'autenticazione di firma di accesso condiviso di Service Bus
### <a name="id"></a>Id
AP2000

### <a name="description"></a>Descrizione
Usare il file system distribuito (SAS, Shared Access Signature) per l'autenticazione. Il servizio di controllo di accesso (ACS) è deprecato per l'autenticazione del bus di servizio.

Per condividere le idee, commenti e suggerimenti [commenti e suggerimenti dell'analisi del codice di Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
Per una maggiore sicurezza, Azure Active Directory sostituisce l'autenticazione ACS con l'autenticazione di firma di accesso condiviso. Visualizzare [Azure Active Directory è il futuro di ACS](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) per informazioni sul piano di transizione.

### <a name="solution"></a>Soluzione
Usare l'autenticazione SAS nelle app. Nell'esempio seguente viene illustrato come utilizzare un token di firma di accesso condiviso esistente per accedere a un spazio dei nomi del bus di servizio o un'entità.

```
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Vedere gli argomenti seguenti per altre informazioni.

* Per una panoramica, vedere [autenticazione della firma di accesso condiviso con il Bus di servizio](https://msdn.microsoft.com/library/dn170477.aspx)
* [Come usare l'autenticazione della firma di accesso condiviso con il Bus di servizio](https://msdn.microsoft.com/library/dn205161.aspx)
* Per un progetto di esempio, vedere [l'autenticazione con firma di accesso condiviso (SAS) con le sottoscrizioni del Bus di servizio](http://code.msdn.microsoft.com/windowsazure/Using-Shared-Access-e605b37c)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>È consigliabile usare il metodo OnMessage per evitare "ciclo di ricezione"
### <a name="id"></a>Id
AP2002

### <a name="description"></a>Descrizione
Per evitare che si verifichi un "ciclo di ricezione," chiama il **OnMessage** metodo è una soluzione migliore per la ricezione di messaggi rispetto a chiamare il **ricezione** (metodo). Tuttavia, se è necessario usare il **ricezione** (metodo) e si specifica un tempo di attesa non predefinito, assicurarsi che il tempo di attesa sia superiore a un minuto.

Per condividere le idee, commenti e suggerimenti [commenti e suggerimenti dell'analisi del codice di Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
Quando si chiama **OnMessage**, il client avvia un message pump interno che esegue costantemente il polling di coda o sottoscrizione. Questo pump del messaggio contiene un ciclo infinito che emette una chiamata a ricevere messaggi. Se la chiamata scade, genera una nuova chiamata. L'intervallo di timeout è determinato dal valore della [OperationTimeout](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactorysettings.operationtimeout.aspx) proprietà delle [MessagingFactory](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactory.aspx)che viene utilizzato.

Il vantaggio dell'utilizzo **OnMessage** rispetto alle **ricezione** è che gli utenti non dovranno manualmente il polling dei messaggi, gestire le eccezioni, elaborare più messaggi in parallelo e completare i messaggi.

Se si chiama **Receive** senza utilizzare il valore predefinito, assicurarsi di *ServerWaitTime* valore è superiore a un minuto. L'impostazione *ServerWaitTime* per più di un minuto impedisce al server scada prima che il messaggio venga ricevuto completamente.

### <a name="solution"></a>Soluzione
Vedere gli esempi di codice seguente per gli utilizzi consigliati. Per altre informazioni, vedere [metodo queueclient. Onmessage (Microsoft. ServiceBus.)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.onmessage.aspx)e [metodo queueclient. Receive (Microsoft. ServiceBus.)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.receive.aspx).

Per migliorare le prestazioni dell'infrastruttura di messaggistica di Azure, vedere lo schema progettuale [Introduzione alla messaggistica asincrona](https://msdn.microsoft.com/library/dn589781.aspx).

Di seguito è riportato un esempio d'uso **OnMessage** per ricevere i messaggi.

```
void ReceiveMessages()
{
    // Initialize message pump options.
    OnMessageOptions options = new OnMessageOptions();
    options.AutoComplete = true; // Indicates if the message-pump should call complete on messages after the callback has completed processing.
    options.MaxConcurrentCalls = 1; // Indicates the maximum number of concurrent calls to the callback the pump should initiate.
    options.ExceptionReceived += LogErrors; // Enables you to get notified of any errors encountered by the message pump.

    // Start receiving messages.
    QueueClient client = QueueClient.Create("myQueue");
    client.OnMessage((receivedMessage) => // Initiates the message pump and callback is invoked for each message that is recieved, calling close on the client will stop the pump.
    {
        // Process the message.
    }, options);
    Console.WriteLine("Press any key to exit.");
    Console.ReadKey();
```

Di seguito è riportato un esempio d'uso **ricezione** tempo di attesa con il server predefinito.

```
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

Di seguito è riportato un esempio d'uso **ricezione** con un server diverso tempo di attesa.

```
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
## <a name="consider-using-asynchronous-service-bus-methods"></a>È consigliabile usare i metodi asincroni del Bus di servizio
### <a name="id"></a>Id
AP2003

### <a name="description"></a>Descrizione
Usare i metodi asincroni del Bus di servizio per migliorare le prestazioni con la messaggistica negoziata.

Per condividere le idee, commenti e suggerimenti [commenti e suggerimenti dell'analisi del codice di Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
Uso di metodi asincroni consente la concorrenza di programma dell'applicazione perché l'esecuzione di ogni chiamata non blocca il thread principale. Quando si usano i metodi di messaggistica, l'esecuzione di un'operazione del Bus di servizio (inviare, ricevere, eliminare e così via) richiede tempo. Questo tempo include l'elaborazione dell'operazione dal servizio del Bus di servizio oltre alla latenza della richiesta e risposta. Per aumentare il numero di operazioni per volta, è necessario eseguire operazioni contemporaneamente. Per altre informazioni, vedere [procedure consigliate per prestazioni miglioramenti tramite servizio di messaggistica negoziata del Bus](https://msdn.microsoft.com/library/azure/hh528527.aspx).

### <a name="solution"></a>Soluzione
Visualizzare [QueueClient Class (Microsoft. ServiceBus.)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.aspx) per informazioni su come usare il metodo asincrono consigliato.

Per migliorare le prestazioni dell'infrastruttura di messaggistica di Azure, vedere lo schema progettuale [Introduzione alla messaggistica asincrona](https://msdn.microsoft.com/library/dn589781.aspx).

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Si consideri di partizionamento di code del Bus di servizio e gli argomenti
### <a name="id"></a>Id
AP2004

### <a name="description"></a>Descrizione
Partizione di code del Bus di servizio e gli argomenti per ottenere prestazioni migliori con la messaggistica del Bus di servizio.

Per condividere le idee, commenti e suggerimenti [commenti e suggerimenti dell'analisi del codice di Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
Il partizionamento di code e argomenti Service Bus aumenta la disponibilità dei servizi e velocità effettiva delle prestazioni perché la velocità effettiva complessiva di una coda o argomento partizionato non è più limitata dalle prestazioni di un singolo broker messaggi o archivio di messaggistica. Inoltre, un'interruzione temporanea di un archivio di messaggistica non effettua una coda o argomento partizionato non disponibile. Per altre informazioni, vedere [partizionamento delle entità di messaggistica](https://msdn.microsoft.com/library/azure/dn520246.aspx).

### <a name="solution"></a>Soluzione
Il frammento di codice seguente viene illustrato come partizionare le entità di messaggistica.

```
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Per altre informazioni, vedere [Service Bus code e argomenti partizionati | Blog di Microsoft Azure](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) consultare le [coda partizionata del Bus di Microsoft Azure Service](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f) esempio.

## <a name="do-not-set-sharedaccessstarttime"></a>Non impostare SharedAccessStartTime
### <a name="id"></a>Id
AP3001

### <a name="description"></a>Descrizione
È consigliabile evitare l'utilizzo di SharedAccessStartTimeset all'ora corrente per avviare subito il criterio di accesso condiviso. È sufficiente impostare questa proprietà se si desidera avviare il criterio di accesso condiviso in un secondo momento.

Per condividere le idee, commenti e suggerimenti [commenti e suggerimenti dell'analisi del codice di Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
Sincronizzazione dell'orologio comporta una differenza oraria lieve tra i Data Center. Ad esempio, si potrebbe pensare che impostando l'ora di inizio di un archivio criteri SAS come l'ora corrente utilizzando Now o un metodo simile causerà il criterio di firma di accesso condiviso abbia effetto immediato. Tuttavia, le differenze lievi di tempo tra i Data Center possono causare problemi con questo poiché alcuni tempi del datacenter potrebbero essere leggermente oltre l'ora di inizio, mentre altri la precedono. Di conseguenza, i criteri di firma di accesso condiviso possono scadere rapidamente (o persino immediatamente) se la durata di criteri impostata è troppo breve.

Per altre informazioni sull'uso di firma di accesso condiviso in archiviazione di Azure, vedere [introduzione della tabella SAS (Shared Access Signature) della coda SAS e all'aggiornamento per Blob SAS - Blog del Team di Microsoft Azure Storage - home page - sito blog MSDN](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas.aspx).

### <a name="solution"></a>Soluzione
Rimuovere l'istruzione che imposta l'ora di inizio dei criteri di accesso condiviso. Lo strumento di analisi del codice di Azure fornisce una correzione per risolvere questo problema. Per altre informazioni sulla gestione della sicurezza, vedere lo schema progettuale [Valet Key Pattern](https://msdn.microsoft.com/library/dn568102.aspx).

Il frammento di codice seguente dimostra la correzione del codice per risolvere questo problema.

```
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

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>Data di scadenza deve essere più di cinque minuti di criteri di accesso condiviso
### <a name="id"></a>Id
AP3002

### <a name="description"></a>Descrizione
Può esistere come differenza relativa a cinque minuti negli orologi tra i Data Center in posizioni diverse a causa di una condizione nota come "sfasamento." Per impedire la firma di accesso condiviso token dei criteri scada prima del previsto, impostare l'ora di scadenza per essere più di cinque minuti.

Per condividere le idee, commenti e suggerimenti [commenti e suggerimenti dell'analisi del codice di Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
I Dataenter in diverse località del mondo Sincronizza da un segnale di clock. Poiché occorre tempo per segnale dell'orologio viaggi in località diverse, può esistere una varianza di tempo tra i Data Center in località geografiche diverse anche se apparentemente tutto ciò che viene sincronizzato. Questa differenza di tempo può influire sull'accesso condiviso iniziale tempo e scadenza intervallo di criteri. Pertanto, per assicurarsi che i criteri di accesso condiviso diventano effettiva immediatamente, non specificare l'ora di inizio. Inoltre, assicurarsi che l'ora di scadenza sia più di 5 minuti per evitare una scadenza anticipata.

Per altre informazioni sull'uso della firma di accesso condiviso in archiviazione di Azure, vedere [introduzione della tabella SAS (Shared Access Signature) della coda SAS e all'aggiornamento per Blob SAS - Blog del Team di Microsoft Azure Storage - home page - sito blog MSDN](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas.aspx).

### <a name="solution"></a>Soluzione
Per altre informazioni sulla gestione della sicurezza, vedere lo schema progettuale [Valet Key Pattern](https://msdn.microsoft.com/library/dn568102.aspx).

Di seguito è riportato un esempio di non specificare un'ora di inizio dei criteri di accesso condiviso.

```
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

Di seguito è riportato un esempio di come specificare un'ora di inizio dei criteri di accesso condiviso con una durata di scadenza dei criteri maggiore di cinque minuti.

```
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

Per altre informazioni, vedere [creare e usare una firma di accesso condiviso](https://msdn.microsoft.com/library/azure/jj721951.aspx).

## <a name="use-cloudconfigurationmanager"></a>Utilizzare CloudConfigurationManager
### <a name="id"></a>Id
AP4000

### <a name="description"></a>Descrizione
Usando il [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) classe per i progetti, ad esempio sito Web di Azure e servizi mobili di Azure non introducono problemi di runtime. Come procedura consigliata, tuttavia, è consigliabile usare il Cloud[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) come modo unificato di gestione delle configurazioni per tutte le applicazioni Cloud di Azure.

Per condividere le idee, commenti e suggerimenti [commenti e suggerimenti dell'analisi del codice di Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
CloudConfigurationManager legge il file di configurazione appropriato per l'ambiente dell'applicazione.

[CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)

### <a name="solution"></a>Soluzione
Il refactoring del codice per usare la [CloudConfigurationManager classe](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx). Una correzione del codice per risolvere questo problema viene fornita dallo strumento di analisi del codice di Azure.

Il frammento di codice seguente dimostra la correzione del codice per risolvere questo problema. Sostituisci

`var settings = ConfigurationManager.AppSettings["mySettings"];`

con

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

Ecco un esempio di come archiviare l'impostazione di configurazione in un file app. config o Web. config. Aggiungere le impostazioni per la sezione appSettings del file di configurazione. Di seguito è riportato il file Web. config per l'esempio di codice precedente.

```
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>  
```

## <a name="avoid-using-hard-coded-connection-strings"></a>Evitare di usare le stringhe di connessione hardcoded
### <a name="id"></a>Id
AP4001

### <a name="description"></a>Descrizione
Se si utilizzano stringhe di connessione hardcoded ed è necessario aggiornarle in un secondo momento, è possibile apportare modifiche al codice sorgente e ricompilare l'applicazione. Tuttavia, se si archiviano le stringhe di connessione in un file di configurazione, è possibile cambiarle successivamente semplicemente aggiornando il file di configurazione.

Per condividere le idee, commenti e suggerimenti [commenti e suggerimenti dell'analisi del codice di Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
Impostare come hardcoded le stringhe di connessione è sconsigliato perché presenta problemi quando le stringhe di connessione devono essere modificate rapidamente. Inoltre, se il progetto deve essere archiviato nel controllo del codice sorgente, le stringhe di connessione hardcoded introducono vulnerabilità di sicurezza poiché le stringhe possono essere visualizzate nel codice sorgente.

### <a name="solution"></a>Soluzione
Store le stringhe di connessione nel file di configurazione o gli ambienti di Azure.

* Per le applicazioni autonome, usare l'app. config per archiviare le impostazioni della stringa di connessione.
* Per le applicazioni web ospitate in IIS, usare file Web. config per archiviare le stringhe di connessione.
* Per le applicazioni ASP.NET vNext utilizzare Configuration per archiviare le stringhe di connessione.

Per informazioni sull'utilizzo dei file di configurazioni, ad esempio Web. config o App. config, vedere [linee guida di configurazione di ASP.NET Web](https://msdn.microsoft.com/library/vstudio/ff400235\(v=vs.100\).aspx). Per informazioni su come Azure funzionano le variabili di ambiente, vedere [siti Web di Azure: How Application Strings and Connection Strings Work](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/). Per informazioni sulla memorizzazione di stringa di connessione nel controllo del codice sorgente, vedere [evitare di inserire informazioni sensibili, ad esempio le stringhe di connessione nei file archiviati nel repository del codice sorgente](http://www.asp.net/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control).

## <a name="use-diagnostics-configuration-file"></a>Usare file di configurazione di diagnostica
### <a name="id"></a>Id
AP5000

### <a name="description"></a>Descrizione
Anziché configurare le impostazioni di diagnostica nel codice, ad esempio usando l'API di programmazione di windowsazure, è necessario configurare le impostazioni di diagnostica nel file Diagnostics. wadcfg. (O, Diagnostics. wadcfgx se si usa Azure SDK 2.5). In questo modo, è possibile modificare le impostazioni di diagnostica senza dover ricompilare il codice.

Per condividere le idee, commenti e suggerimenti [commenti e suggerimenti dell'analisi del codice di Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
Prima che Azure SDK 2.5 (che usa diagnostica di Azure 1.3), diagnostica di Azure (WAD) può essere configurato usando diversi metodi: aggiungendola al blob di configurazione nell'archiviazione, usando codice imperativo, una configurazione dichiarativa o il valore predefinito configurazione. Tuttavia, il modo migliore per configurare la diagnostica è usare un file di configurazione XML (Diagnostics. wadcfg o diagnositcs per SDK 2.5 e versioni successive) nel progetto di applicazione. Questo approccio, il file Diagnostics. wadcfg completamente definisce la configurazione e può essere aggiornato e ridistribuito a suo piacimento. Combinare l'uso del file di configurazione Diagnostics. wadcfg con metodi programmatici di impostazione delle configurazioni tramite le [DiagnosticMonitor](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.diagnosticmonitor.aspx)oppure [RoleInstanceDiagnosticManager](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.management.roleinstancediagnosticmanager.aspx)le classi possono generare confusione. Visualizzare [inizializzare o modificare la configurazione di diagnostica Azure](https://msdn.microsoft.com/library/azure/hh411537.aspx) per altre informazioni.

A partire da 1.3 WAD (incluso in Azure SDK 2.5), non è più possibile usare codice per configurare la diagnostica. Di conseguenza, è possibile specificare solo la configurazione quando si applica o l'aggiornamento dell'estensione di diagnostica.

### <a name="solution"></a>Soluzione
Utilizzare la finestra di progettazione di configurazione di diagnostica per spostare le impostazioni di diagnostica per il file di configurazione di diagnostica (diagnositcs. wadcfg o diagnositcs per SDK 2.5 e versioni successive). È inoltre consigliabile installare [Azure SDK 2.5](http://go.microsoft.com/fwlink/?LinkId=513188) e usare la funzionalità di diagnostica più recente.

1. Menu di scelta rapida per il ruolo che si desidera configurare, scegliere Proprietà e quindi scegliere la scheda di configurazione.
2. Nel **Diagnostics** sezione, verificare che il **Abilita diagnostica** casella di controllo è selezionata.
3. Scegliere il **configura** pulsante.

   ![L'accesso all'opzione Abilita diagnostica](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   Visualizzare [configurazione della diagnostica per servizi Cloud di Azure e macchine virtuali](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) per altre informazioni.

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>Evitare di dichiarare gli oggetti DbContext come static
### <a name="id"></a>Id
AP6000

### <a name="description"></a>Descrizione
Per risparmiare memoria, evitare di dichiarare gli oggetti DBContext come static.

Per condividere le idee, commenti e suggerimenti [commenti e suggerimenti dell'analisi del codice di Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Motivo
Gli oggetti DBContext contengono i risultati della query da ogni chiamata. Gli oggetti DBContext statici non vengono eliminati fino a quando non viene scaricato il dominio dell'applicazione. Pertanto, un oggetto DBContext statico può utilizzare grandi quantità di memoria.

### <a name="solution"></a>Soluzione
Dichiarare DBContext come una variabile locale o un campo di istanza non statico, usarlo per un'attività e consentire che venga eliminato dopo l'uso.

Il classe controller MVC di esempio seguente viene illustrato come utilizzare l'oggetto DBContext.

```
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
Per altre informazioni sull'ottimizzazione e risoluzione dei problemi delle app di Azure, vedere [risolvere i problemi di un'app web nel servizio App di Azure con Visual Studio](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio).
