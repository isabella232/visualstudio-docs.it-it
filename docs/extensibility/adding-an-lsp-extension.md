---
title: Aggiunta di un'estensione per il protocollo di Server di linguaggio | Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad112d34c8f23a7738137f148f00a38a27335424
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53966560"
---
# <a name="add-a-language-server-protocol-extension"></a>Aggiungere un'estensione del protocollo di Server di linguaggio

Il protocollo Server Language (LSP) è un protocollo comune, nel formato v2.0 RPC JSON, usato per fornire funzioni di servizio per vari editor di codice di linguaggio. Usa il protocollo, gli sviluppatori possono scrivere un server singolo linguaggio per fornire funzionalità come IntelliSense, finestra di diagnostica degli errori del servizio linguaggio, trovare tutti i riferimenti, e così via per vari editor di codice che supportano il rappresentante LSP memorizzato. Tradizionalmente, i servizi di linguaggio in Visual Studio possono essere aggiunti in uno dei modi usando file di grammatica TextMate per offrire funzionalità di base, ad esempio l'evidenziazione della sintassi, o mediante la scrittura di servizi di linguaggio personalizzato con il set completo di API di estendibilità di Visual Studio per fornire dati più complessi. A questo punto, il supporto per il rappresentante LSP memorizzato offre una terza opzione.

![servizio del protocollo di server di linguaggio in Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Protocollo di server di linguaggio

![implementazione del protocollo della lingua server](media/lsp-implementation.png)

Questo articolo descrive come creare un'estensione di Visual Studio che usa un server di linguaggio basato su provider LSP. Si presuppone che si hanno già sviluppato un server di linguaggio basato su provider LSP e si vuole semplicemente integrarla in Visual Studio.

Per il supporto all'interno di Visual Studio, i server di linguaggio possono comunicare con il client (Visual Studio) tramite qualsiasi meccanismo di trasmissione di flusso di base, ad esempio:

* Flussi di input/output standard
* Named pipe
* Socket (solo TCP)

Lo scopo di LSP e il relativo supporto in Visual Studio è ai servizi di eseguire l'onboarding del linguaggio che non fanno parte del prodotto Visual Studio. Non si intende estendere i servizi di linguaggio esistenti (ad esempio, c#) in Visual Studio. Per estendere i linguaggi esistenti, fare riferimento alla Guida di estendibilità del servizio di linguaggio (ad esempio, il [piattaforma del compilatore .NET "Roslyn"](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)).

Per altre informazioni sul protocollo stesso, vedere la documentazione [qui](https://github.com/Microsoft/language-server-protocol).

Per altre informazioni su come creare un server di linguaggio di esempio o come integrare un server Java esistente in Visual Studio Code, vedere la documentazione [qui](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-features-supported"></a>Funzionalità del protocollo Server linguaggio supportate

Le funzionalità LSP seguenti sono supportate in Visual Studio finora:

Messaggio | Include il supporto in Visual Studio
--- | ---
inizializzare | sì
inizializzato | sì
chiusura della sessione | sì
uscita | sì
$/ cancelRequest | sì
finestra/showMessage | sì
window/showMessageRequest | sì
window/logMessage | sì
i dati di telemetria/evento |
client/registerCapability |
client/unregisterCapability |
workspace/didChangeConfiguration | sì
area di lavoro/didChangeWatchedFiles | sì
area di lavoro/simbolo | sì
area di lavoro/executeCommand | sì
area di lavoro/applyEdit | sì
textDocument/publishDiagnostics | sì
textDocument/didOpen | sì
textDocument/didChange | sì
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | sì
textDocument/didClose | sì
textDocument/completamento | sì
completamento/risolvere | sì
textDocument/passaggio del mouse | sì
textDocument/signatureHelp | sì
textDocument/i riferimenti | sì
textDocument/documentHighlight | sì
textDocument/documentSymbol | sì
textDocument/formattazione | sì
textDocument/rangeFormatting | sì
textDocument/onTypeFormatting |
textDocument/definizione | sì
textDocument/codeAction | sì
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/risolvere |
textDocument, ridenominazione | sì

## <a name="getting-started"></a>Per iniziare

> [!NOTE]
> A partire da Visual Studio 15.8 Preview 3, il supporto del protocollo di Server di linguaggio comune è incorporato in Visual Studio.  Se è stata creata usando l'anteprima delle estensioni LSP [linguaggio Server Client VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) versione, essi smetterà di funzionare dopo a è stato eseguito l'aggiornamento a 15,8 Preview 3 o versione successiva.  È necessario eseguire il comando seguente per ottenere le estensioni LSP funziona di nuovo:
>
> 1. Disinstallare l'anteprima protocollo Server alla lingua di Microsoft Visual Studio VSIX.  A partire da Preview 15,8 4, ogni volta che si esegue un aggiornamento in Visual Studio, viene automaticamente rileverà e rimuovere l'anteprima VSIX per l'utente durante il processo di aggiornamento.
>
> 2. Aggiornare il riferimento a Nuget per la versione non di anteprima più recente per [pacchetti LSP](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client).
>
> 3. Rimuovere la dipendenza da VSIX di anteprima del Server lingua di Microsoft Visual Studio protocollo nel manifesto VSIX.
>
> 4. Assicurarsi che VSIX specifica di Visual Studio 15.8 Preview 3 come limite inferiore per la destinazione dell'installazione.
>
> 5. Ricompilare e ridistribuire.

### <a name="create-a-vsix-project"></a>Creare un progetto VSIX

Per creare un'estensione del servizio di linguaggio Usa un server di linguaggio basato su provider LSP, prima di tutto assicurarsi di avere il **sviluppo di estensioni di Visual Studio** carico di lavoro per l'istanza di Visual Studio installato.

Successivamente, creare un nuovo VSIXProject vuoto, passare a **File** > **nuovo progetto** > **Visual c#**  >   **Estendibilità** > **progetto VSIX**:

![creare il progetto vsix](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Installazione di server e il runtime di linguaggio

Per impostazione predefinita, le estensioni create per supportare i server di linguaggio basato su provider LSP in Visual Studio non conterrà i server di linguaggio autonomamente o i runtime necessari per eseguirle. Gli sviluppatori di estensione sono responsabili della distribuzione i server di linguaggio e i runtime necessiti. Esistono diversi modi per eseguire questa operazione:

* I server di linguaggio possono essere incorporati in VSIX come file di contenuto.
* Creare un file MSI per installare il server di linguaggio e/o necessarie di runtime.
* Vengono fornite istruzioni su che avvisa che gli utenti del Marketplace come ottenere i server di runtime e linguaggio.

### <a name="textmate-grammar-files"></a>File di grammatica TextMate

Il rappresentante LSP memorizzato non è incluse specifiche su come fornire la colorazione del testo per lingue. Per garantire la colorazione personalizzata per le lingue in Visual Studio, gli sviluppatori di estensioni possono utilizzare un file di grammatica TextMate. Per aggiungere file di grammatica o del tema TextMate personalizzati, seguire questa procedura:

1. Creare una cartella denominata "Grammatiche" all'interno dell'estensione (o può essere qualsiasi nome scelto).

2. All'interno di *grammatiche* cartella, includere eventuali  *\*.tmlanguage*,  *\*con estensione plist*,  *\*tmtheme*, oppure  *\*JSON* file desiderato che fornisce la colorazione di personalizzati.

3. Fare doppio clic sul file e scegliere **proprietà**. Modifica il **compilare** azione **contenuto** e il **Includi in VSIX** proprietà su true.

4. Creare un *pkgdef* file e aggiungere una riga simile alla seguente:

   ```xml
   [$RootKey$\TextMate\Repositories]
   "MyLang"="$PackageFolder$\Grammars"
   ```

5. Fare doppio clic sul file e scegliere **proprietà**. Modifica il **compilare** azione **contenuto** e il **Includi in VSIX** proprietà su true.

Dopo aver completato i passaggi precedenti, un *grammatiche* cartella viene aggiunta all'installazione del pacchetto directory come origine del repository denominato 'MyLang' ('MyLang' è solo un nome per la risoluzione dell'ambiguità e può essere qualsiasi stringa univoca). Tutte le grammatiche (*.tmlanguage* file) e i file di tema (*tmtheme* file) in questa directory vengono prelevate come potenziali e sostituiscono le grammatiche predefinite fornite con TextMate. Se estensioni dichiarato del file di grammatica corrispondono all'estensione del file in fase di apertura, TextMate passerà.

## <a name="create-a-simple-language-client"></a>Creare un client di linguaggio semplice

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>Interfaccia principale - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Dopo aver creato il progetto VSIX, aggiungere i pacchetti NuGet seguenti al progetto:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Quando si utilizza una dipendenza del pacchetto NuGet, dopo aver completato i passaggi precedenti, i pacchetti di newtonsoft. JSON e StreamJsonRpc vengono aggiunti anche al progetto. **Questi pacchetti non vengono aggiornati a meno che non si è certi che le nuove versioni verranno installati nella versione di Visual Studio che le destinazioni di estensione**. Gli assembly non verranno inclusi in VSIX, invece, verrà prelevati dalla directory di installazione di Visual Studio. Se si fa riferimento a una versione più recente degli assembly rispetto a quella installata nel computer dell'utente, l'estensione *non funzionerà*.

È quindi possibile creare una nuova classe che implementa il [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) interfaccia, l'interfaccia principale necessario per la connessione a un server di linguaggio basato su provider LSP ai client di linguaggio.

Di seguito è riportato un esempio:

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync.InvokeAsync(this, EventArgs.Empty);
        }

        public Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

Sono i metodi principali che devono essere implementati [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) e [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) viene chiamato quando l'estensione è caricata in Visual Studio e il server di linguaggio è pronto per essere avviato. In questo metodo, è possibile richiamare il [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) delegato immediatamente per segnalare che il server di linguaggio deve essere avviato o è possibile eseguire una logica aggiuntiva e richiamare [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) in un secondo momento. **Per attivare il server di linguaggio, è necessario chiamare StartAsync a un certo punto.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) è il metodo di richiamata alla fine, chiamare il [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) delegare; contiene la logica per avviare il server di linguaggio e stabilire la connessione. Deve essere restituito un oggetto di connessione che contiene i flussi per la scrittura nel server e la lettura dal server. Tutte le eccezioni generate in questo caso vengono intercettate e visualizzate all'utente tramite un messaggio nella barra informazioni in Visual Studio.

### <a name="activation"></a>Attivazione

Dopo aver implementata la classe di client di linguaggio, è necessario definire due attributi per poter definire come verrà caricato in Visual Studio e attivato:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio Usa [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) per gestire i relativi punti di estendibilità. Il [esportare](/dotnet/api/system.componentmodel.composition.exportattribute) attributo indica a Visual Studio che questa classe deve essere selezionata come un punto di estensione e caricata al momento opportuno.

Per utilizzare MEF, è necessario anche definire MEF come Asset nel manifesto VSIX.

Aprire la finestra di progettazione del manifesto VSIX e passare al **asset** scheda:

![Aggiungi asset MEF](media/lsp-add-asset.png)

Fare clic su Nuovo per creare un nuovo Asset:

![definire asset MEF](media/lsp-define-asset.png)

* **Tipo**: Microsoft.VisualStudio.MefComponent
* **Origine**: Un progetto nella soluzione corrente
* **Progetto**: [progetto]

### <a name="content-type-definition"></a>Definizione del tipo di contenuto

Attualmente l'unico modo per caricare l'estensione di server di linguaggio basato su provider LSP sia dal tipo di contenuto di file. Vale a dire, quando si definisce una classe di client di linguaggio (che implementa [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), sarà necessario definire i tipi di file che, quando aperto, farà sì che il caricamento dell'estensione. Se non sono aperto alcun file che soddisfano il tipo di contenuto definito, quindi l'estensione non verrà caricata.

Questa operazione viene eseguita tramite la definizione di uno o più classi ContentTypeDefinition:

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;


        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

Nell'esempio precedente, viene creata una definizione di tipo di contenuto per i file che terminano *.bar* estensione di file. La definizione di tipo di contenuto è fornita la barra"nome" e **devono** derivativo [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Dopo l'aggiunta di una definizione di tipo di contenuto, è possibile definire casi in cui caricare l'estensione client di linguaggio nella classe della lingua client:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Aggiunta del supporto per i server di linguaggio LSP non richiede di implementare il proprio sistema di progetto in Visual Studio. I clienti possono aprire un singolo file o una cartella in Visual Studio per iniziare a usare il servizio di linguaggio. In effetti, il supporto per i server di linguaggio LSP è progettato per funzionare solo in scenari di Apri cartella/file. Se viene implementato un sistema di progetto personalizzati, alcune funzionalità (ad esempio le impostazioni) non funzionerà.

## <a name="advanced-features"></a>Funzionalità avanzate

### <a name="settings"></a>Impostazioni

Supporto per le impostazioni specifiche della lingua server personalizzati è disponibile, ma è ancora in corso continui miglioramenti. Le impostazioni sono specifiche di ciò che il server di linguaggio supporta e in genere come server di linguaggio emette i dati di controllo. Ad esempio, un server di linguaggio può avere un'impostazione per il numero massimo di errori segnalati. Gli autori delle estensioni definisce un valore predefinito, che può essere modificato dagli utenti per progetti specifici.

Eseguire la procedura seguente per aggiungere supporto per le impostazioni per l'estensione del servizio di linguaggio LSP:

1. Aggiungere un file JSON (ad esempio, *MockLanguageExtensionSettings.json*) nel progetto che contiene le impostazioni e i relativi valori predefiniti. Ad esempio:

   ```json
   {
    "foo.maxNumberOfProblems": -1
   }
   ```
2. Fare doppio clic sul file JSON e selezionare **proprietà**. Modifica il **compilare** azione a "Content" e "Includi in VSIX' su true.

3. Implementare ConfigurationSections e restituire l'elenco dei prefissi per le impostazioni definite nel file JSON (In Visual Studio Code, questo potrebbe eseguire il mapping al nome di sezione di configurazione nel file package. JSON):

   ```csharp
   public IEnumerable<string> ConfigurationSections
   {
      get
      {
          yield return "foo";
      }
   }
   ```

4. Aggiungere un file con estensione pkgdef per il progetto (Aggiungi nuovo file di testo e modificare l'estensione di file in pkgdef). Il file pkgdef dovrebbe contenere queste info:

   ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
   ```

    Esempio:
    ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Fare clic con il pulsante destro sul file con estensione pkgdef e selezionare **proprietà**. Modifica il **compilare** azione **contenuto** e il **Includi in VSIX** proprietà su true.

6. Aprire il *vsixmanifest* file e aggiungere un asset nel **Asset** scheda:

   ![Modifica risorsa vspackage](media/lsp-add-vspackage-asset.png)

   * **Tipo**: Microsoft.VisualStudio.VsPackage
   * **Origine**: File in filesystem
   * **Percorso**: [percorso per il *pkgdef* file]

### <a name="user-editing-of-settings-for-a-workspace"></a>Utente di modifica delle impostazioni dell'area di lavoro

1. Utente apre un'area di lavoro che contiene i file che del server proprietaria.
2. Utente aggiunge un file nei *VS* cartella denominata *vsworkspacesettings. JSON*.
3. Utente aggiunge una riga per il *vsworkspacesettings. JSON* file per un'impostazione forniti dal server. Ad esempio:

   ```json
   {
    "foo.maxNumberOfProblems": 10
   }
   ```
   ### <a name="enabling-diagnostics-tracing"></a>Abilitazione della traccia di diagnostica
   Tracce di diagnostica può essere abilitata per l'output di tutti i messaggi tra client e server, che può essere utile durante il debug di problemi.  Per abilitare la traccia diagnostica, eseguire le operazioni seguenti:

4. Aprire o creare il file di impostazioni dell'area di lavoro *vsworkspacesettings. JSON* (vedere "Utente di modifica delle impostazioni dell'area di lavoro").
5. Aggiungere la riga seguente nel file di impostazioni json:

```json
{
    "foo.trace.server": "Off"
}
```

Esistono tre possibili valori per il livello di dettaglio di traccia:
* "Off": traccia viene completamente disattivato
* "I messaggi": traccia attivata, ma solo metodo per nome e la risposta ID vengono tracciati.
* "Verbose": traccia attivata viene tracciato il messaggio intero rpc.

Quando la tracciatura è attivata il contenuto è scritto in un file nei *%temp%\VisualStudio\LSP* directory.  Il log viene indicato il formato di denominazione *[LanguageClientName]-[indicatore data/ora]. log*.  Attualmente, la traccia può essere abilitata solo per gli scenari di Apri cartella.  Apertura di un singolo file per attivare un server di linguaggio non dispone di supporto di analisi diagnostica.

### <a name="custom-messages"></a>Messaggi personalizzati

Esistono API unica posizione per facilitare il passaggio di messaggi a e ricezione di messaggi dal server di linguaggio che non fanno parte del protocollo Server linguaggio standard. Per gestire i messaggi personalizzati, implementare [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) interfaccia nella classe del client di linguaggio. [Visual Studio-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) libreria viene usata per la trasmissione dei messaggi personalizzati tra il client di linguaggio e il server di linguaggio. Poiché l'estensione del client linguaggio LSP è proprio come qualsiasi altra estensione di Visual Studio, è possibile decidere di aggiungere le funzionalità aggiuntive (che non sono supportate per il rappresentante LSP memorizzato) a Visual Studio (usando altre API di Visual Studio) nella propria estensione tramite messaggi personalizzati.

#### <a name="receiving-custom-messages"></a>Ricezione di messaggi personalizzati

Per ricevere messaggi personalizzati dal server di linguaggio, implementare il [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) proprietà sul [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) e restituire un oggetto che sa come gestire i messaggi personalizzati . Esempio riportato di seguito:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="sending-custom-messages"></a>L'invio di messaggi personalizzato

Per inviare messaggi personalizzati per il server di linguaggio, implementare il [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) metodo sul [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Questo metodo viene richiamato quando il server di linguaggio è avviato e pronto per ricevere messaggi. Oggetto [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) oggetto viene passato come parametro, che è quindi possibile mantenere per inviare messaggi al server di linguaggio mediante [VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) API. Esempio riportato di seguito:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {    
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
    }
}
```

### <a name="middle-layer"></a>Livello intermedio

In alcuni casi uno sviluppatore di estensione possibile intercettare i messaggi LSP inviati e ricevuti dal server di linguaggio. Uno sviluppatore di estensione potrà ad esempio, si decida di modificare il parametro del messaggio inviato per un particolare messaggio LSP o modificare i risultati restituiti dal server di linguaggio per una funzionalità LSP (ad esempio i completamenti). Quando ciò è necessario, gli sviluppatori di estensioni possono utilizzare l'API MiddleLayer per intercettare i messaggi LSP.

Ogni messaggio LSP ha la propria interfaccia di livello intermedio per l'intercettazione. Per intercettare un messaggio specifico, creare una classe che implementa l'interfaccia di livello intermedio per quel messaggio. Implementare poi il [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) interfaccia nella classe del client di linguaggio e restituire un'istanza dell'oggetto nel [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) proprietà. Esempio riportato di seguito:

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{
    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
    }
}
```

La funzionalità di livello intermedio è ancora in fase di sviluppo e non ancora completo.

## <a name="sample-lsp-language-server-extension"></a>Estensione di esempio LSP lingua server

Per visualizzare il codice sorgente di un'estensione di esempio usando l'API del client di LSP in Visual Studio, vedere esempi di estendibilità VSSDK [esempio LSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>Domande frequenti

**Vorrebbe compilare un sistema di progetto personalizzati per integrare un server di linguaggio LSP per fornire supporto delle funzionalità più completo in Visual Studio, come posso farlo?**

Supporto per i server di linguaggio basato su provider LSP in Visual Studio si basa sul [funzionalità Apri cartella](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/) ed è progettato appositamente per non richiedere un sistema di progetto personalizzato. È possibile compilare il proprio sistema di progetto personalizzati attenendosi alle istruzioni [qui](https://github.com/Microsoft/VSProjectSystem), ma alcune funzionalità, ad esempio le impostazioni, potrebbe non funzionare. La logica di inizializzazione predefinito per i server di linguaggio LSP consiste nel passare il percorso della cartella radice della cartella attualmente aperta, pertanto se si usa un sistema di progetto personalizzati, potrebbe essere necessario fornire la logica personalizzata durante l'inizializzazione per garantire possibile lingua server avviato correttamente.

**Come si aggiunge il supporto del debugger?**

Verrà fornito supporto per la [comune debug protocollo](https://code.visualstudio.com/docs/extensionAPI/api-debugging) in una versione futura.

**Se esiste già un servizio di linguaggio supportati VS installato (ad esempio, JavaScript), posso comunque installare un'estensione di server di linguaggio LSP che offre funzionalità aggiuntive (ad esempio, il termine Lint indica)?**

Sì, ma non tutte le funzionalità funzioneranno correttamente. L'obiettivo finale per le estensioni del server LSP linguaggio consiste nell'abilitare Servizi di linguaggio non supportati da Visual Studio. È possibile creare estensioni per offrono supporto aggiuntivo usando LSP lingua server, ma alcune funzionalità (ad esempio IntelliSense) non sarà un'esperienza senza problemi. In generale, è consigliabile che le estensioni del server di linguaggio LSP utilizzabile per fornire nuove esperienze di lingua, non per estendere quelli esistenti.

**Dove posso pubblicare il server di linguaggio LSP VSIX completato?**

Vedere le istruzioni del Marketplace [qui](walkthrough-publishing-a-visual-studio-extension.md).
