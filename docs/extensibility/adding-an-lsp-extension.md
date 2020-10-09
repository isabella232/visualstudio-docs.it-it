---
title: Aggiunta di un'estensione del protocollo server di linguaggio | Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0c43d5a50b7a2acb536dee5fe9c6ed9ec3d36d7
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91860454"
---
# <a name="add-a-language-server-protocol-extension"></a>Aggiungere un'estensione del protocollo di server di linguaggio

Il protocollo LSP (Language Server Protocol) è un protocollo comune, sotto forma di JSON RPC v 2.0, usato per fornire funzionalità del servizio di linguaggio a diversi editor di codice. Utilizzando il protocollo, gli sviluppatori possono scrivere un solo server di linguaggio per fornire funzionalità del servizio di linguaggio come IntelliSense, diagnostica degli errori, trova tutti i riferimenti e così via, a diversi editor di codice che supportano il LSP. Tradizionalmente, i servizi di linguaggio in Visual Studio possono essere aggiunti usando i file di grammatica TextMate per fornire funzionalità di base, ad esempio l'evidenziazione della sintassi o la scrittura di servizi di linguaggio personalizzati che usano il set completo di API di estendibilità di Visual Studio per offrire dati più completi. Con il supporto di Visual Studio per LSP, esiste una terza opzione.

![servizio del protocollo server di linguaggio in Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Protocollo di server di linguaggio

![implementazione del protocollo server di linguaggio](media/lsp-implementation.png)

Questo articolo descrive come creare un'estensione di Visual Studio che usa un server di linguaggio basato su LSP. Si presuppone che sia già stato sviluppato un server di linguaggio basato su LSP e si voglia semplicemente integrarlo in Visual Studio.

Per il supporto in Visual Studio, i server di linguaggio possono comunicare con il client (Visual Studio) tramite qualsiasi meccanismo di trasmissione basato sul flusso, ad esempio:

* Flussi di input/output standard
* Named Pipes
* Socket (solo TCP)

Lo scopo di LSP e il relativo supporto in Visual Studio è quello di eseguire l'onboarding di servizi di linguaggio che non fanno parte del prodotto Visual Studio. Non è progettato per estendere i servizi di linguaggio esistenti (ad esempio C#) in Visual Studio. Per estendere le lingue esistenti, vedere la Guida all'estendibilità del servizio di linguaggio (ad esempio, ["Roslyn" .NET Compiler Platform](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)) o vedere [estendere l'editor e i servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md).

Per ulteriori informazioni sul protocollo stesso, vedere la documentazione [qui](https://github.com/Microsoft/language-server-protocol).

Per ulteriori informazioni su come creare un server di linguaggio di esempio o su come integrare un server di linguaggio esistente in Visual Studio Code, vedere la documentazione [qui](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-supported-features"></a>Funzionalità supportate del protocollo server di linguaggio

Le tabelle seguenti illustrano le funzionalità LSP supportate in Visual Studio:

Message | Con supporto in Visual Studio
--- | ---
inizializzazione | sì
inizializzato | sì
shutdown | sì
exit | sì
$/cancelRequest | sì
finestra/showMessage | sì
finestra/showMessageRequest | sì
finestra/logMessage | sì
telemetria/evento |
client/registerCapability |
client/unregisterCapability |
area di lavoro/didChangeConfiguration | sì
area di lavoro/didChangeWatchedFiles | sì
area di lavoro/simbolo | sì
area di lavoro/executeCommand | sì
area di lavoro/applyEdit | sì
textDocument/publishDiagnostics | sì
textDocument/didrogato | sì
textDocument/didChange | sì
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | sì
textDocument/didClose | sì
textDocument/completamento | sì
completamento/risoluzione | sì
textDocument/hover | sì
textDocument/signatureHelp | sì
textDocument/riferimenti | sì
textDocument/documentHighlight | sì
textDocument/documentSymbol | sì
textDocument/formattazione | sì
textDocument/rangeFormatting | sì
textDocument/onTypeFormatting |
textDocument/definizione | sì
textDocument/codeaction | sì
textDocument/CodeLens |
CodeLens/Risolvi |
textDocument/documentLink |
documentLink/Risolvi |
textDocument/Rinomina | sì

## <a name="get-started"></a>Introduzione

> [!NOTE]
> A partire da Visual Studio 2017 versione 15,8, il supporto per il protocollo Common Language Server è integrato in Visual Studio. Se sono state compilate estensioni LSP usando la versione [VSIX del client del server](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) di anteprima, l'aggiornamento alla versione 15,8 o successiva sarà interrotto. Per far funzionare nuovamente le estensioni di LSP, è necessario eseguire le operazioni seguenti:
>
> 1. Disinstallare il linguaggio VSIX di Microsoft Visual Studio Language Server Preview.
>
>    A partire dalla versione 15,8, ogni volta che si esegue un aggiornamento in Visual Studio, l'anteprima VSIX viene automaticamente rilevata e rimossa.
>
> 2. Aggiornare il riferimento a NuGet alla versione più recente non di anteprima per i [pacchetti LSP](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client).
>
> 3. Rimuovere la dipendenza dal linguaggio VSIX di Microsoft Visual Studio Language Server Preview nel manifesto VSIX.
>
> 4. Assicurarsi che VSIX specifichi Visual Studio 2017 versione 15,8 Preview 3 come limite inferiore per l'installazione di destinazione.
>
> 5. Ricompilare e ridistribuire.

### <a name="create-a-vsix-project"></a>Creare un progetto VSIX

Per creare un'estensione del servizio di linguaggio utilizzando un server di linguaggio basato su LSP, verificare prima di tutto che sia installato il carico di lavoro **sviluppo di estensioni di Visual Studio** per l'istanza di vs.

Successivamente, creare un nuovo progetto VSIX passando a **file**  >  **nuovo progetto**  >  **Visual C#**  >  **Extensibility**  >  **VSIX Project**:

![Crea progetto VSIX](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Server di linguaggio e installazione del runtime

Per impostazione predefinita, le estensioni create per supportare i server di linguaggi basati su LSP in Visual Studio non contengono i server di linguaggio o i runtime necessari per eseguirli. Gli sviluppatori di estensioni sono responsabili della distribuzione dei server di linguaggio e dei runtime necessari. Esistono diversi modi per eseguire questa operazione:

* I server di linguaggio possono essere incorporati in VSIX come file di contenuto.
* Creare un'identità del servizio gestito per installare il server di lingua e/o i runtime necessari.
* Fornire istruzioni sul Marketplace per informare gli utenti su come ottenere runtime e server di linguaggio.

### <a name="textmate-grammar-files"></a>File di grammatica TextMate

Lo LSP non include le specifiche su come fornire la colorazione del testo per le lingue. Per fornire una colorazione personalizzata per le lingue in Visual Studio, gli sviluppatori di estensioni possono usare un file di grammatica TextMate. Per aggiungere file di tema o grammatica TextMate personalizzati, seguire questa procedura:

1. Creare una cartella denominata "grammatiche" all'interno dell'estensione. in alternativa, è possibile scegliere qualsiasi nome.

2. All'interno della cartella *Grammatics* includere tutti i file con * \* estensione tmlanguage*, * \* plist*, * \* tmtheme*o * \* JSON* che forniscono la colorazione personalizzata.

   > [!TIP]
   > Un file con *estensione tmtheme* definisce la modalità di mapping degli ambiti alle classificazioni di Visual Studio (chiavi di colore denominate). Per informazioni aggiuntive, è possibile fare riferimento al file Global *. tmtheme* nella directory *% ProgramFiles (x86)% \ Microsoft Visual Studio \\ \<version> \\ \<SKU> \Common7\IDE\CommonExtensions\Microsoft\TextMate\Starterkit\Themesg* .

3. Creare un file con *estensione pkgdef* e aggiungere una riga simile alla seguente:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Fare clic con il pulsante destro del mouse sui file e scegliere **Proprietà**. Impostare l'azione di **compilazione** su **contenuto** e impostare la proprietà **Includi in VSIX** su **true**.

Dopo aver completato i passaggi precedenti, una cartella *Grammatics* viene aggiunta alla directory di installazione del pacchetto come origine del repository denominata ' ". lang ' è semplicemente un nome per la risoluzione dell'ambiguità e può essere una stringa univoca. Tutte le grammatiche (file con*estensione tmlanguage* ) e i file di tema (file con*estensione tmtheme* ) in questa directory vengono prelevate come potenziali e sostituiscono le grammatiche predefinite fornite con TextMate. Se le estensioni dichiarate del file di grammatica corrispondono all'estensione del file aperto, TextMate eseguirà l'istruzione.

## <a name="create-a-simple-language-client"></a>Creazione di un client di linguaggio semplice

### <a name="main-interface---ilanguageclient"></a>Interfaccia principale- [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)

Dopo aver creato il progetto VSIX, aggiungere i pacchetti NuGet seguenti al progetto:

* [Microsoft. VisualStudio. LanguageServer. client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Quando si prende una dipendenza dal pacchetto NuGet dopo aver completato i passaggi precedenti, anche i pacchetti Newtonsoft.Json e StreamJsonRpc vengono aggiunti al progetto. Non **aggiornare questi pacchetti a meno che non si sia certi che le nuove versioni verranno installate nella versione di Visual Studio a cui è destinata l'estensione**. Gli assembly non verranno inclusi in VSIX. verranno invece prelevati dalla directory di installazione di Visual Studio. Se si fa riferimento a una versione più recente degli assembly rispetto a quella installata nel computer di un utente, l'estensione non funzionerà.

È quindi possibile creare una nuova classe che implementa l'interfaccia [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true) , che è l'interfaccia principale necessaria per i client di linguaggio che si connettono a un server di linguaggio basato su LSP.

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

I metodi principali che devono essere implementati sono [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) e [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) viene chiamato quando Visual Studio ha caricato l'estensione e il server di linguaggio è pronto per l'avvio. In questo metodo, è possibile richiamare immediatamente il delegato [startAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) per segnalare che il server di linguaggio deve essere avviato, oppure è possibile eseguire una logica aggiuntiva e richiamare [startAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) in un secondo momento. **Per attivare il server di linguaggio, è necessario chiamare StartAsync in un determinato momento.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true) è il metodo richiamato chiamando il delegato [startAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) . Contiene la logica per avviare il server di linguaggio e stabilire una connessione. Deve essere restituito un oggetto connessione che contiene flussi per la scrittura nel server e la lettura dal server. Tutte le eccezioni generate vengono rilevate e visualizzate dall'utente tramite un messaggio della barra informazioni in Visual Studio.

### <a name="activation"></a>Activation

Una volta implementata la classe client del linguaggio, è necessario definire due attributi per definire come verrà caricato in Visual Studio e attivato:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio USA [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) per gestire i punti di estendibilità. L'attributo [Export](/dotnet/api/system.componentmodel.composition.exportattribute) indica a Visual Studio che questa classe deve essere prelevata come punto di estensione e caricata al momento appropriato.

Per usare MEF, è necessario definire anche MEF come asset nel manifesto VSIX.

Aprire la finestra di progettazione del manifesto VSIX e passare alla scheda **Asset** :

![Aggiungi asset MEF](media/lsp-add-asset.png)

Fare clic su **nuovo** per creare un nuovo asset:

![definire asset MEF](media/lsp-define-asset.png)

* **Tipo**: Microsoft. VisualStudio. MefComponent
* **Origine**: un progetto nella soluzione corrente
* **Progetto**: [progetto]

### <a name="content-type-definition"></a>Definizione del tipo di contenuto

Attualmente, l'unico modo per caricare l'estensione del server di linguaggio basato su LSP è il tipo di contenuto del file. Ovvero, quando si definisce la classe del client del linguaggio (che implementa [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)), sarà necessario definire i tipi di file che, quando aperti, provocheranno il caricamento dell'estensione. Se non vengono aperti file che corrispondono al tipo di contenuto definito, l'estensione non verrà caricata.

Questa operazione viene eseguita tramite la definizione di una o più `ContentTypeDefinition` classi:

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

Nell'esempio precedente viene creata una definizione di tipo di contenuto per i file che terminano con l'estensione di file a *barre* . Alla definizione del tipo di contenuto viene assegnato il nome "barra" e deve derivare da [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017&preserve-view=true).

Dopo aver aggiunto una definizione del tipo di contenuto, è possibile definire quando caricare l'estensione del client di linguaggio nella classe Language client:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

L'aggiunta del supporto per i server di linguaggio LSP non richiede l'implementazione di un sistema di progetto personalizzato in Visual Studio. I clienti possono aprire un singolo file o una cartella in Visual Studio per iniziare a usare il servizio di linguaggio. In realtà, il supporto per i server di linguaggio LSP è progettato per funzionare solo in scenari di cartelle/file aperti. Se viene implementato un sistema di progetto personalizzato, alcune funzionalità, ad esempio le impostazioni, non funzioneranno.

## <a name="advanced-features"></a>Funzionalità avanzate

### <a name="settings"></a>Impostazioni

Il supporto per le impostazioni specifiche del Server Language è disponibile, ma è ancora in fase di miglioramento. Le impostazioni sono specifiche delle funzionalità supportate dal server di linguaggio e in genere controllano il modo in cui il server di linguaggio emette i dati. Ad esempio, un server di linguaggio potrebbe avere un'impostazione per il numero massimo di errori segnalati. Gli autori di estensioni definiscono un valore predefinito che può essere modificato dagli utenti per progetti specifici.

Attenersi alla seguente procedura per aggiungere il supporto per le impostazioni all'estensione del servizio di linguaggio LSP:

1. Aggiungere un file JSON (ad esempio *MockLanguageExtensionSettings.json*) al progetto che contiene le impostazioni e i relativi valori predefiniti. Ad esempio:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Fare clic con il pulsante destro del mouse sul file JSON e scegliere **Proprietà**. Impostare l'azione di **compilazione** su "contenuto" e la proprietà "Includi in VSIX" su **true**.

3. Implementare ConfigurationSections e restituire l'elenco di prefissi per le impostazioni definite nel file JSON (in Visual Studio Code, viene mappato al nome della sezione di configurazione in package.jssu):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Aggiungere un file con estensione pkgdef al progetto (aggiungere un nuovo file di testo e modificare l'estensione del file in. pkgdef). Il file pkgdef deve contenere queste informazioni:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Esempio:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Fare clic con il pulsante destro del mouse sul file con estensione pkgdef e scegliere **Proprietà**. Impostare l'azione di **compilazione** su **contenuto** e la proprietà **Includi in VSIX** su **true**.

6. Aprire il file *source. Extension. vsixmanifest* e aggiungere un asset nella scheda **Asset** :

   ![modifica asset VSPackage](media/lsp-add-vspackage-asset.png)

   * **Tipo**: Microsoft. VisualStudio. VSPackage
   * **Origine**: file nel file System
   * **Path**: [percorso del file con *estensione pkgdef* ]

### <a name="user-editing-of-settings-for-a-workspace"></a>Modifica di impostazioni utente per un'area di lavoro

1. L'utente apre un'area di lavoro contenente i file di proprietà del server.
2. L'utente aggiunge un file nella cartella *. vs* denominato *VSWorkspaceSettings.json*.
3. L'utente aggiunge una riga al *VSWorkspaceSettings.js* file per un'impostazione fornita dal server. Ad esempio:

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>Abilita traccia diagnostica

La traccia di diagnostica può essere abilitata per l'output di tutti i messaggi tra il client e il server, che può essere utile durante il debug dei problemi. Per abilitare la traccia diagnostica, procedere come segue:

1. Aprire o creare il file di impostazioni dell'area di lavoro *VSWorkspaceSettings.jsin* (vedere "modifica di impostazioni utente per un'area di lavoro").
2. Aggiungere la riga seguente nel file JSON delle impostazioni:

```json
{
    "foo.trace.server": "Off"
}
```

Per il livello di dettaglio della traccia sono possibili tre valori:

* "Off": la traccia è stata disattivata completamente
* "Messages": la traccia è attivata ma solo il nome del metodo e l'ID di risposta vengono tracciati.
* "Verbose": traccia attivata; viene tracciata l'intero messaggio RPC.

Quando la traccia è attivata, il contenuto viene scritto in un file nella directory *%Temp%\VisualStudio\LSP* Il log segue il formato di denominazione *[LanguageClientName]-[DateTime Stamp]. log*. Attualmente, la traccia può essere abilitata solo per scenari di cartelle aperte. L'apertura di un singolo file per l'attivazione di un server di linguaggio non dispone del supporto per la traccia di diagnostica.

### <a name="custom-messages"></a>Messaggi personalizzati

Sono disponibili API per facilitare il passaggio di messaggi e la ricezione di messaggi dal server di linguaggio che non fanno parte del protocollo server di linguaggio standard. Per gestire i messaggi personalizzati, implementare l'interfaccia [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) nella classe del client del linguaggio. La libreria [vs-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) viene utilizzata per trasmettere messaggi personalizzati tra il client del linguaggio e il server di linguaggio. Poiché l'estensione client del linguaggio LSP è analoga a qualsiasi altra estensione di Visual Studio, è possibile decidere di aggiungere altre funzionalità, che non sono supportate da LSP, a Visual Studio (usando altre API di Visual Studio) nell'estensione tramite messaggi personalizzati.

#### <a name="receive-custom-messages"></a>Ricezione di messaggi personalizzati

Per ricevere messaggi personalizzati dal server di linguaggio, implementare la proprietà [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017&preserve-view=true) su [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) e restituire un oggetto che sa come gestire i messaggi personalizzati. Di seguito è riportato un esempio:

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

#### <a name="send-custom-messages"></a>Invia messaggi personalizzati

Per inviare messaggi personalizzati al server di linguaggio, implementare il metodo [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017&preserve-view=true) in [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true). Questo metodo viene richiamato quando il server di linguaggio viene avviato e pronto per la ricezione di messaggi. Un oggetto [jsonrpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) viene passato come parametro, che può quindi essere mantenuto per inviare messaggi al server di linguaggio usando le API di [Visual Studio StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) . Di seguito è riportato un esempio:

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

In alcuni casi uno sviluppatore di estensioni potrebbe voler intercettare i messaggi LSP inviati e ricevuti dal server di linguaggio. Ad esempio, uno sviluppatore di estensioni potrebbe voler modificare il parametro del messaggio inviato per un particolare messaggio LSP oppure modificare i risultati restituiti dal server di linguaggio per una funzionalità LSP (ad esempio, completamenti). Quando è necessario, gli sviluppatori di estensioni possono usare l'API MiddleLayer per intercettare i messaggi LSP.

Ogni messaggio LSP ha una propria interfaccia del livello intermedio per l'intercettazione. Per intercettare un messaggio specifico, creare una classe che implementi l'interfaccia del livello intermedio per quel messaggio. Implementare quindi l'interfaccia [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) nella classe del client del linguaggio e restituire un'istanza dell'oggetto nella proprietà [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017&preserve-view=true) . Di seguito è riportato un esempio:

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

La funzionalità livello intermedio è ancora in fase di sviluppo e non è ancora completa.

## <a name="sample-lsp-language-server-extension"></a>Estensione del server di linguaggio LSP di esempio

Per visualizzare il codice sorgente di un'estensione di esempio usando l'API client LSP in Visual Studio, vedere esempio di VSSDK-Extensibility-Samples [LSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>Domande frequenti

**Si desidera creare un sistema di progetto personalizzato per integrare il server di linguaggio LSP per offrire un supporto più completo per le funzionalità in Visual Studio, come procedere?**

Il supporto per i server di linguaggi basati su LSP in Visual Studio si basa sulla [funzionalità Apri cartella](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) ed è progettato per non richiedere un sistema di progetto personalizzato. È possibile creare un sistema di progetto personalizzato seguendo le istruzioni riportate [qui](https://github.com/Microsoft/VSProjectSystem), ma alcune funzionalità, ad esempio le impostazioni, potrebbero non funzionare. La logica di inizializzazione predefinita per i server di linguaggio LSP consiste nel passare il percorso della cartella radice della cartella attualmente aperta. Se si utilizza un sistema di progetto personalizzato, potrebbe essere necessario fornire la logica personalizzata durante l'inizializzazione per garantire che il server di linguaggio possa essere avviato correttamente.

**Ricerca per categorie aggiungere il supporto del debugger?**

In una versione futura verrà fornito supporto per il [protocollo di debug comune](https://code.visualstudio.com/docs/extensionAPI/api-debugging) .

**Se è già installato un servizio di linguaggio supportato da Visual Studio (ad esempio, JavaScript), è comunque possibile installare un'estensione del server di linguaggio LSP che offre funzionalità aggiuntive (ad esempio, la mancata presenza)?**

Sì, ma non tutte le funzionalità funzioneranno correttamente. L'obiettivo finale per le estensioni del server di linguaggio LSP è quello di abilitare i servizi di linguaggio non supportati in modo nativo da Visual Studio. È possibile creare estensioni che offrono supporto aggiuntivo utilizzando i server di linguaggio LSP, ma alcune funzionalità (ad esempio IntelliSense) non saranno un'esperienza uniforme. In generale, si consiglia di utilizzare le estensioni del server di linguaggio LSP per offrire nuove esperienze di linguaggio, senza estendere quelle esistenti.

**Dove è possibile pubblicare il progetto VSIX Language Server completato?**

Vedere le istruzioni di Marketplace [qui](walkthrough-publishing-a-visual-studio-extension.md).

## <a name="see-also"></a>Vedere anche

- [Aggiungere il supporto di altri linguaggi all'editor di Visual Studio](../ide/adding-visual-studio-editor-support-for-other-languages.md)
