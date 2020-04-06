---
title: Aggiunta di un'estensione Language Server Protocol Documenti Microsoft
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef2093915538f09f425fc961420c4a3078043c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740227"
---
# <a name="add-a-language-server-protocol-extension"></a>Aggiungere un'estensione del protocollo di server di linguaggio

Il protocollo LSP (Language Server Protocol) è un protocollo comune, sotto forma di JSON RPC v2.0, utilizzato per fornire funzionalità del servizio di linguaggio a vari editor di codice. Utilizzando il protocollo, gli sviluppatori possono scrivere un singolo server di linguaggio per fornire funzionalità del servizio di linguaggio come IntelliSense, diagnostica degli errori, trovare tutti i riferimenti e così via, a vari editor di codice che supportano il provider LSP. Tradizionalmente, i servizi di linguaggio in Visual Studio possono essere aggiunti usando i file di grammatica TextMate per fornire funzionalità di base, ad esempio l'evidenziazione della sintassi o scrivendo servizi di linguaggio personalizzati che usano il set completo di API di estensibilità di Visual Studio per fornire dati più completi. Con il supporto di Visual Studio per LSP, è disponibile una terza opzione.

![servizio di protocollo del server di linguaggio in Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Protocollo di server di linguaggio

![implementazione del protocollo del server di linguaggio](media/lsp-implementation.png)

In questo articolo viene descritto come creare un'estensione di Visual Studio che utilizza un server di linguaggio basato su LSP. Si presuppone che sia già stato sviluppato un server di linguaggio basato su LSP e si desideri semplicemente integrarlo in Visual Studio.

Per il supporto all'interno di Visual Studio, i server di linguaggio possono comunicare con il client (Visual Studio) tramite qualsiasi meccanismo di trasmissione basato sul flusso, ad esempio:For support within Visual Studio, language servers can communicate with the client (Visual Studio) via any stream-based transmission mechanism, for example:

* Flussi di input/output standard
* Named Pipes
* Prese (solo TCP)

Lo scopo del provider LSP e il supporto per esso in Visual Studio consiste nell'onboard servizi di linguaggio che non fanno parte del prodotto Visual Studio. Non è destinato a estendere i servizi di linguaggio esistenti (ad esempio c'è) in Visual Studio. Per estendere i linguaggi esistenti, fare riferimento alla guida all'estendibilità del servizio di linguaggio (ad esempio, la [piattaforma del compilatore .NET "Roslyn")](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)oppure vedere [Estendere l'editor e i servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md).

Per ulteriori informazioni sul protocollo stesso, vedere la documentazione [qui](https://github.com/Microsoft/language-server-protocol).

Per ulteriori informazioni su come creare un server di linguaggio di esempio o su come integrare un server di linguaggio esistente nel codice di Visual Studio, vedere la documentazione [qui](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-supported-features"></a>Funzionalità supportate dal protocollo Language Server Protocol

Nelle tabelle seguenti vengono illustrate le funzionalità LSP supportate in Visual Studio:

Message | Supporto in Visual Studio
--- | ---
inizializzazione | sì
inizializzato | sì
shutdown | sì
exit | sì
/cancelRichiesta | sì
finestra/showMessage | sì
finestra/showMessageRequest | sì
finestra/logMessage | sì
telemetria/evento |
client/registerCapability |
client/unregisterCapability |
area di lavoro/didChangeConfiguration | sì
area di lavoro/didChangeWatchedFiles | sì
area di lavoro/simbolo | sì
workspace/executeCommand | sì
area di lavoro/applicaModifica | sì
textDocument/publishDiagnostics | sì
textDocument/didApri | sì
textDocument/didCambia | sì
textDocument/willSalva |
textDocument/willSaveWaitUntil (FileText)<a1/a1><a2>< |
textDocument/didSalva | sì
textDocument/didChiudi | sì
textDocument/completamento | sì
completamento/risoluzione | sì
textDocument/hover | sì
textDocument/firmaAiuto | sì
textDocument/riferimenti | sì
textDocument/documentoEvidenziazione | sì
textDocument/documentSymbol (Simbolo di documento) | sì
textDocument/formattazione | sì
textDocument/intervalloFormattazione | sì
TextDocument/onTypeFormatting (Documentodi testo/onTypeFormatting) |
textDocumento/definizione | sì
textDocument/codiceAzione | sì
textDocument/codeLens |
codeLens/risolvere |
textDocument/documentLink (Documentoditesto) |
documentLink/risoluzione |
textDocumentazione/ridenominazione | sì

## <a name="get-started"></a>Introduzione

> [!NOTE]
> A partire da Visual Studio 2017 versione 15.8, il supporto per il protocollo Language Server comune è integrato in Visual Studio. Se sono state create estensioni LSP utilizzando la versione [VSIX del](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) client Language Server di anteprima, questa smetterà di funzionare dopo l'aggiornamento alla versione 15.8 o successiva. Per far funzionare di nuovo le estensioni LSP, è necessario eseguire le operazioni seguenti:
>
> 1. Disinstallare il VSIX di Microsoft Visual Studio Language Server Protocol Preview VSIX.
>
>    A partire dalla versione 15.8, ogni volta che si esegue un aggiornamento in Visual Studio il VSIX di anteprima viene rilevato e rimosso automaticamente.
>
> 2. Aggiornare il riferimento Nuget alla versione non di anteprima più recente per [i pacchetti LSP.](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)
>
> 3. Rimuovere la dipendenza per Microsoft Visual Studio Language Server Protocol Preview VSIX nel manifesto VSIX.
>
> 4. Assicurarsi che il codice VSIX specifichi Visual Studio 2017 versione 15.8 Preview 3 come limite inferiore per la destinazione di installazione.
>
> 5. Ricompilare e ridistribuire.

### <a name="create-a-vsix-project"></a>Creare un progetto VSIXCreate a VSIX project

Per creare un'estensione del servizio di linguaggio utilizzando un server di linguaggio basato su LSP, assicurarsi innanzitutto di avere il carico di lavoro di **sviluppo dell'estensione** di Visual Studio installato per l'istanza di VS.

Successivamente, creare un nuovo progetto VSIX passando a **File** > **Nuovo progetto** > **Visual C .** > **Extensibility** > **VSIX Project**

![creare un progetto vsix](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Installazione del server di linguaggio e del runtime

Per impostazione predefinita, le estensioni create per supportare i server di linguaggio basati su LSP in Visual Studio non contengono i server di linguaggio stessi o i runtime necessari per eseguirli. Gli sviluppatori di estensioni sono responsabili della distribuzione dei server di linguaggio e dei runtime necessari. Ci sono diversi modi per farlo:

* I server di linguaggio possono essere incorporati nel file VSIX come file di contenuto.
* Creare un file MSI per installare il server di linguaggio e/o i runtime necessari.
* Fornire istruzioni su Marketplace per informare gli utenti su come ottenere runtime e server di linguaggio.

### <a name="textmate-grammar-files"></a>File di grammatica di TextMate

L'LSP non include specifiche su come fornire la colorazione del testo per le lingue. Per fornire la colorazione personalizzata per le lingue in Visual Studio, gli sviluppatori di estensioni possono usare un file di grammatica TextMate.To provide custom colorization for languages in Visual Studio, extension developers can use a TextMate grammar file. Per aggiungere file di grammatica o tema TextMate personalizzati, attenersi alla seguente procedura:

1. Creare una cartella denominata "Grammars" all'interno dell'estensione (o può essere qualsiasi nome si sceglie).

2. All'interno della cartella *Grammars,* includere qualsiasi * \*file .tmlanguage*, * \*.plist*, * \*.tmtheme*o * \*.json* che si desidera che forniscono la colorazione personalizzata.

   > [!TIP]
   > Un file *con estensione tmtheme* definisce il modo in cui gli ambiti eseguono il mapping alle classificazioni di Visual Studio (chiavi colore denominate). Per istruzioni, è possibile fare riferimento al file con *estensione tmtheme* globale nella directory *\\\<%ProgramFiles(x86)>>% \\ \<* .

3. Creare un file *.pkgdef* e aggiungere una riga simile alla seguente:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Fare clic con il pulsante destro del mouse sui file e selezionare **Proprietà**. Impostare l'azione **di compilazione su** **Contenuto** e modificare la proprietà Includi **in VSIX** su **true**.

Dopo aver completato i passaggi precedenti, una cartella *Grammars* viene aggiunta alla directory di installazione del pacchetto come origine del repository denominata MyLang ('MyLang' è solo un nome per la disambiguazione e può essere qualsiasi stringa univoca). Tutte le grammatiche (file con estensione*tmlanguage)* e i file dei temi ( file *.tmtheme)* in questa directory vengono rilevati come potenziali e sostituiscono le grammatiche incorporate fornite con TextMate. Se le estensioni dichiarate del file di grammatica corrispondono all'estensione del file da aprire, TextMate interverrà.

## <a name="create-a-simple-language-client"></a>Creare un client di linguaggio sempliceCreate a simple language client

### <a name="main-interface---ilanguageclient"></a>Interfaccia principale - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Dopo aver creato il progetto VSIX, aggiungere i seguenti pacchetti NuGet al progetto:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Quando si esegue una dipendenza dal pacchetto NuGet dopo aver completato i passaggi precedenti, anche i pacchetti Newtonsoft.Json e StreamJsonRpc vengono aggiunti al progetto. **Non aggiornare questi pacchetti a meno che non si sia certi che tali nuove versioni verranno installate nella versione di Visual Studio**a cui è destinata l'estensione . Gli assembly non verranno inclusi nel valore VSIX. verranno invece prelevati dalla directory di installazione di Visual Studio. Se si fa riferimento a una versione più recente degli assembly rispetto a quella installata nel computer di un utente, l'estensione non funzionerà.

È quindi possibile creare una nuova classe che implementa l'interfaccia [ILanguageClient,](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) che è l'interfaccia principale necessaria per i client di linguaggio che si connettono a un server di linguaggio basato su LSP.

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

I metodi principali che devono essere implementati sono [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) e [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) viene chiamato quando Visual Studio ha caricato l'estensione e il server di linguaggio è pronto per essere avviato. In questo metodo, è possibile richiamare immediatamente il delegato [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) per segnalare che il server di linguaggio deve essere avviato oppure è possibile eseguire logica aggiuntiva e richiamare [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) in un secondo momento. **Per attivare il server di linguaggio, è necessario chiamare StartAsync a un certo punto.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) è il metodo eventualmente richiamato chiamando il [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) delegato. Contiene la logica per avviare il server di linguaggio e stabilire la connessione ad esso. È necessario restituire un oggetto connessione che contiene flussi per la scrittura nel server e la lettura dal server. Eventuali eccezioni generate qui vengono intercettate e visualizzate all'utente tramite un messaggio della barra informazioni in Visual Studio.Any exceptions thrown here are caught and displayed to user via an InfoBar message in Visual Studio.

### <a name="activation"></a>Activation

Una volta implementata la classe client del linguaggio, è necessario definire due attributi per definire come verrà caricata in Visual Studio e attivata:Once your language client class is implemented, you'll need to define two attributes for it for it to define how it will be loaded into Visual Studio and activated:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio utilizza [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) per gestire i punti di estendibilità. Il [Export](/dotnet/api/system.componentmodel.composition.exportattribute) attributo indica a Visual Studio che questa classe deve essere selezionata come punto di estensione e caricata al momento appropriato.

Per utilizzare MEF, è inoltre necessario definire MEF come Asset nel manifesto VSIX.

Aprire la finestra di progettazione del manifesto VSIX e passare alla scheda **Asset:Open** up your VSIX manifest designer and navigate to the Assets tab:

![aggiungere asset MEF](media/lsp-add-asset.png)

Fare clic su **Nuovo** per creare una nuova risorsa:

![definire asset MEF](media/lsp-define-asset.png)

* **Tipo**: Microsoft.VisualStudio.MefComponent
* **Fonte**: Un progetto nella soluzione corrente
* **Progetto**: [Il tuo progetto]

### <a name="content-type-definition"></a>Definizione del tipo di contenuto

Attualmente, l'unico modo per caricare l'estensione del server di linguaggio basato su LSP è in base al tipo di contenuto del file. Ovvero, quando si definisce la classe client del linguaggio (che implementa [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), è necessario definire i tipi di file che, una volta aperti, causeranno il caricamento dell'estensione. Se non vengono aperti file che corrispondono al tipo di contenuto definito, l'estensione non verrà caricata.

Questa operazione viene eseguita `ContentTypeDefinition` tramite la definizione di una o più classi:This is done through defining one or more classes:

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

Nell'esempio precedente viene creata una definizione del tipo di contenuto per i file che terminano con l'estensione *.bar.* Alla definizione del tipo di contenuto viene assegnato il nome "bar" e deve derivare da [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Dopo aver aggiunto una definizione del tipo di contenuto, è possibile definire quando caricare l'estensione client del linguaggio nella classe client del linguaggio:After adding a content type definition, you can then define when to load your language client extension in the language client class:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

L'aggiunta del supporto per i server di linguaggio LSP non richiede l'implementazione di un sistema di progetto personalizzato in Visual Studio. I clienti possono aprire un singolo file o una cartella in Visual Studio per iniziare a usare il servizio di linguaggio. Infatti, il supporto per i server di linguaggio LSP è progettato per funzionare solo in scenari di file/cartella aperta. Se viene implementato un sistema di progetto personalizzato, alcune funzionalità (ad esempio le impostazioni) non funzioneranno.

## <a name="advanced-features"></a>Funzionalità avanzate

### <a name="settings"></a>Impostazioni

È disponibile il supporto per le impostazioni specifiche del server di linguaggio personalizzate, ma è ancora in corso di miglioramento. Le impostazioni sono specifiche per il supporto del server di linguaggio e in genere controllano il modo in cui il server di linguaggio genera i dati. Ad esempio, un server di lingua potrebbe avere un'impostazione per il numero massimo di errori segnalati. Gli autori di estensioni definireno un valore predefinito, che può essere modificato dagli utenti per progetti specifici.

Attenersi alla seguente procedura per aggiungere il supporto per le impostazioni per l'estensione del servizio di linguaggio LSP:

1. Aggiungere un file JSON (ad *esempio, MockLanguageExtensionSettings.json*) al progetto che contiene le impostazioni e i relativi valori predefiniti. Ad esempio:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Fare clic con il pulsante destro del mouse sul file JSON e scegliere **Proprietà**. Impostare l'azione **di compilazione su** "Contenuto" e la proprietà "Includi in VSIX" su **true**.

3. Implementare ConfigurationSections e restituire l'elenco di prefissi per le impostazioni definite nel file JSON (nel codice di Visual Studio, questo verrebbe mappato al nome della sezione di configurazione in package.json):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Aggiungere un file con estensione pkgdef al progetto (aggiungere un nuovo file di testo e modificare l'estensione del file in pkgdef). Il file pkgdef deve contenere queste informazioni:The pkgdef file should contain this info:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Esempio:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Fare clic con il pulsante destro del mouse sul file .pkgdef e selezionare **Proprietà**. Impostare l'azione **di compilazione su** **Contenuto** e la proprietà **Includi in VSIX** su **true**.

6. Aprite il file *source.extension.vsixmanifest* e aggiungete un asset nella scheda **Asset:**

   ![modificare l'asset vspackage](media/lsp-add-vspackage-asset.png)

   * **Tipo**: Microsoft.VisualStudio.VsPackage
   * **Origine**: File nel file system
   * **Percorso**: [Percorso del file *.pkgdef]*

### <a name="user-editing-of-settings-for-a-workspace"></a>Modifica delle impostazioni da parte dell'utente per un'area di lavoro

1. L'utente apre un'area di lavoro contenente i file di proprietà del server.
2. L'utente aggiunge un file nella cartella *VS.vs* denominato *VSWorkspaceSettings.json*.
3. L'utente aggiunge una riga al file *VSWorkspaceSettings.json* per un'impostazione fornita dal server. Ad esempio:

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>Abilitare la traccia diagnosticaEnable diagnostics tracing

L'analisi diagnostica può essere abilitata per l'output di tutti i messaggi tra il client e il server, il che può essere utile durante il debug dei problemi. Per abilitare la traccia diagnostica, eseguire le operazioni seguenti:To enable diagnostic tracing, do the following:

1. Aprire o creare il file di impostazioni dell'area di lavoro *VSWorkspaceSettings.json* (vedere "Modifica delle impostazioni utente per un'area di lavoro").
2. Aggiungere la riga seguente nel file json delle impostazioni:

```json
{
    "foo.trace.server": "Off"
}
```

Esistono tre valori possibili per il livello di dettaglio della traccia:There are three possible values for trace verbosity:

* "Off": la traccia è disattivata completamente
* "Messaggi": traccia attivata ma vengono tracciati solo il nome del metodo e l'ID di risposta.
* "Verbose": traccia accesa; l'intero messaggio rpc viene tracciato.

Quando l'analisi è attivata, il contenuto viene scritto in un file nella directory *%temp%.* Il log segue il formato di denominazione *[LanguageClientName]-[Datetime Stamp].log*. Attualmente, la traccia può essere abilitata solo per gli scenari di cartelle aperte. L'apertura di un singolo file per attivare un server di linguaggio non dispone del supporto per la traccia diagnostica.

### <a name="custom-messages"></a>Messaggi personalizzati

Sono disponibili API per facilitare il passaggio e la ricezione di messaggi dal server di linguaggio che non fanno parte del protocollo Standard DiLanguage Server Protocol. Per gestire i messaggi personalizzati, implementare [l'interfaccia ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) nella classe client del linguaggio. La libreria [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) viene utilizzata per trasmettere messaggi personalizzati tra il client della lingua e il server di linguaggio. Poiché l'estensione client del linguaggio LSP è analoga a qualsiasi altra estensione di Visual Studio, è possibile decidere di aggiungere funzionalità aggiuntive (non supportate da LSP) a Visual Studio (utilizzando altre API di Visual Studio) nell'estensione tramite messaggi personalizzati.

#### <a name="receive-custom-messages"></a>Ricevere messaggi personalizzati

Per ricevere messaggi personalizzati dal server di linguaggio, implementare la proprietà [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) in [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) e restituire un oggetto in grado di gestire i messaggi personalizzati. Esempio seguente:

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

#### <a name="send-custom-messages"></a>Inviare messaggi personalizzati

Per inviare messaggi personalizzati al server di linguaggio, implementare il metodo [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) in [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Questo metodo viene richiamato quando il server di linguaggio è avviato e pronto a ricevere messaggi. Un oggetto [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) viene passato come parametro, che è quindi possibile mantenere per inviare messaggi al server di linguaggio utilizzando le API [VS-StreamJsonRpc.](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) Esempio seguente:

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

### <a name="middle-layer"></a>Strato intermedio

A volte uno sviluppatore di estensioni potrebbe voler intercettare i messaggi LSP inviati e ricevuti dal server di linguaggio. Ad esempio, uno sviluppatore di estensioni potrebbe voler modificare il parametro del messaggio inviato per un determinato messaggio LSP o modificare i risultati restituiti dal server di linguaggio per una funzionalità LSP (ad esempio, completamenti). Quando questo è necessario, gli sviluppatori di estensioni possono utilizzare l'API MiddleLayer per intercettare i messaggi LSP.

Ogni messaggio LSP ha la propria interfaccia di livello intermedio per l'intercettazione. Per intercettare un messaggio specifico, creare una classe che implementa l'interfaccia di livello intermedio per il messaggio. Implementare quindi l'interfaccia [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) nella classe client del linguaggio e restituire un'istanza dell'oggetto nella proprietà [MiddleLayer.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) Esempio seguente:

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

La funzione strato intermedio è ancora in fase di sviluppo e non ancora completa.

## <a name="sample-lsp-language-server-extension"></a>Estensione del server di linguaggio LSP di esempio

Per visualizzare il codice sorgente di un'estensione di esempio utilizzando l'API client LSP in Visual Studio, vedere Esempio [DiSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol)VSSDK-Extensibility-Samples .

## <a name="faq"></a>Domande frequenti

**Vorrei costruire un sistema di progetto personalizzato per integrare il mio server di linguaggio LSP per fornire il supporto più ricco di funzionalità in Visual Studio, come è possibile eseguire questa operazione?**

Il supporto per i server di linguaggio basati su LSP in Visual Studio si basa sulla [funzionalità di apertura delle cartelle](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) ed è progettato per non richiedere un sistema di progetto personalizzato. È possibile creare un sistema di progetto personalizzato seguendo le istruzioni [riportate](https://github.com/Microsoft/VSProjectSystem)di seguito, ma alcune funzionalità, ad esempio le impostazioni, potrebbero non funzionare. La logica di inizializzazione predefinita per i server di linguaggio LSP consiste nel passare il percorso della cartella radice della cartella attualmente aperta, pertanto se si utilizza un sistema di progetto personalizzato, potrebbe essere necessario fornire logica personalizzata durante l'inizializzazione per garantire che il server di linguaggio possa essere avviato correttamente.

**Come si aggiunge il supporto del debugger?**

In una versione futura verrà fornito il supporto per il protocollo di [debug comune.](https://code.visualstudio.com/docs/extensionAPI/api-debugging)

**Se è già installato un servizio di linguaggio supportato da VS (ad esempio, JavaScript), è comunque possibile installare un'estensione del server di linguaggio LSP che offre funzionalità aggiuntive (ad esempio linting)?**

Sì, ma non tutte le funzioni funzioneranno correttamente. L'obiettivo finale per le estensioni del server del linguaggio LSP è abilitare i servizi di linguaggio non supportati in modo nativo da Visual Studio. È possibile creare estensioni che offrono supporto aggiuntivo utilizzando i server di linguaggio LSP, ma alcune funzionalità (ad esempio IntelliSense) non sarà un'esperienza semplice. In generale, si consiglia di utilizzare le estensioni del server del linguaggio LSP per fornire nuove esperienze linguistiche, non per estendere quelle esistenti.

**Dove pubblicare il server di linguaggio LSP completato VSIX?**

Vedere le istruzioni del Marketplace [qui](walkthrough-publishing-a-visual-studio-extension.md).

## <a name="see-also"></a>Vedere anche

- [Aggiungere il supporto di altri linguaggi all'editor di Visual Studio](../ide/adding-visual-studio-editor-support-for-other-languages.md)
