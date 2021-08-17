---
title: Aggiunta di un'estensione del protocollo del server di | Microsoft Docs
description: Informazioni su come creare un'estensione Visual Studio che integra un server di linguaggio basato sul protocollo LSP (Language Server Protocol).
ms.custom: SEO-VS-2020
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 250c164a6e9537b6ec972571ecb83efb2f0aebe3d8f7d9e1b02c5e84260158d6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435057"
---
# <a name="add-a-language-server-protocol-extension"></a>Aggiungere un'estensione del protocollo di server di linguaggio

Il protocollo LSP (Language Server Protocol) è un protocollo comune, sotto forma di RPC JSON v2.0, usato per fornire funzionalità del servizio di linguaggio a diversi editor di codice. Usando il protocollo , gli sviluppatori possono scrivere un singolo server di linguaggio per fornire funzionalità del servizio di linguaggio come IntelliSense, diagnostica degli errori, trovare tutti i riferimenti e così via, in vari editor di codice che supportano LSP. In genere, i servizi di linguaggio in Visual Studio possono essere aggiunti usando file di grammatica TextMate per fornire funzionalità di base, ad esempio l'evidenziazione della sintassi o la scrittura di servizi di linguaggio personalizzati che usano il set completo di API di estendibilità di Visual Studio per fornire dati più completi. Con Visual Studio supporto per LSP, è disponibile una terza opzione.

![language server protocol service in Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Protocollo di server di linguaggio

![implementazione del protocollo del server di linguaggio](media/lsp-implementation.png)

Questo articolo descrive come creare un'estensione Visual Studio che usa un server di linguaggio basato su LSP. Si presuppone che sia già stato sviluppato un server di linguaggio basato su LSP e che si voglia semplicemente integrarlo in Visual Studio.

Per il supporto all'Visual Studio, i server di linguaggio possono comunicare con il client (Visual Studio) tramite qualsiasi meccanismo di trasmissione basato su flusso, ad esempio:

* Flussi di input/output standard
* Named Pipes
* Socket (solo TCP)

Lo scopo del provider di servizi di configurazione locale e il suo supporto in Visual Studio è l'onboard di servizi di linguaggio che non fanno parte Visual Studio prodotto. Non è progettato per estendere i servizi di linguaggio esistenti (ad esempio C#) in Visual Studio. Per estendere i linguaggi esistenti, vedere la guida all'estendibilità del servizio di linguaggio (ad esempio, ["Roslyn" .NET Compiler Platform](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)) o vedere Estendere l'editor e i servizi [di linguaggio](../extensibility/extending-the-editor-and-language-services.md).

Per altre informazioni sul protocollo stesso, vedere la documentazione [qui.](https://github.com/Microsoft/language-server-protocol)

Per altre informazioni su come creare un server di linguaggio di esempio o su come integrare un server di linguaggio esistente in Visual Studio Code, vedere la documentazione [qui](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-supported-features"></a>Funzionalità supportate dal protocollo del server di linguaggio

Le tabelle seguenti illustrano le funzionalità di LSP supportate in Visual Studio:

Message | Supporto in Visual Studio
--- | ---
inizializzazione | sì
inizializzato | sì
shutdown | sì
exit | sì
$/cancelRequest | sì
window/showMessage | sì
window/showMessageRequest | sì
window/logMessage | sì
telemetry/event |
client/registerCapability |
client/unregisterCapability |
workspace/didChangeConfiguration | sì
workspace/didChangeWatchedFiles | sì
area di lavoro/simbolo | sì
workspace/executeCommand | sì
workspace/applyEdit | sì
textDocument/publishDiagnostics | sì
textDocument/didOpen | sì
textDocument/didChange | sì
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | sì
textDocument/didClose | sì
textDocument/completion | sì
completamento/risoluzione | sì
textDocument/hover | sì
textDocument/signatureHelp | sì
textDocument/references | sì
textDocument/documentHighlight | sì
textDocument/documentSymbol | sì
textDocument/formatting | sì
textDocument/rangeFormatting | sì
textDocument/onTypeFormatting |
textDocument/definition | sì
textDocument/codeAction | sì
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/resolve |
textDocument/rename | sì

## <a name="get-started"></a>Introduzione

> [!NOTE]
> A partire Visual Studio 2017 versione 15.8, il supporto per common language server protocol è integrato in Visual Studio. Se sono stati compilati estensioni LSP usando la versione [VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) di Language Server Client di anteprima, queste smetteranno di funzionare dopo l'aggiornamento alla versione 15.8 o successiva. Per fare in modo che le estensioni LSP funzionino di nuovo, è necessario eseguire le operazioni seguenti:
>
> 1. Disinstallare vsIX Microsoft Visual Studio Language Server Protocol Preview.
>
>    A partire dalla versione 15.8, ogni volta che si esegue un aggiornamento in Visual Studio vsix di anteprima viene rilevato e rimosso automaticamente.
>
> 2. Aggiornare il riferimento a Nuget alla versione più recente non in anteprima per [i pacchetti LSP.](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)
>
> 3. Rimuovere la dipendenza da VSIX Microsoft Visual Studio Language Server Protocol Preview nel manifesto VSIX.
>
> 4. Assicurarsi che vsix specifichi Visual Studio 2017 versione 15.8 Preview 3 come limite inferiore per la destinazione di installazione.
>
> 5. Ricompilare e ridistribuire.

### <a name="create-a-vsix-project"></a>Creare un progetto VSIX

Per creare un'estensione del servizio di linguaggio usando un  server di linguaggio basato su LSP, assicurarsi prima di tutto di aver installato il carico di lavoro sviluppo dell'estensione Visual Studio per l'istanza di Visual Studio.

Creare quindi un nuovo progetto VSIX passando a **File**  >  **New Project** Visual  >  **C#**  >  **Extensibility**  >  **VSIX Project**:

![creare un progetto vsix](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Installazione del server di linguaggio e del runtime

Per impostazione predefinita, le estensioni create per supportare i server di linguaggio basati su LSP Visual Studio non contengono i server di linguaggio stessi o i runtime necessari per eseguirli. Gli sviluppatori di estensioni sono responsabili della distribuzione dei server del linguaggio e dei runtime necessari. Esistono diversi modi per eseguire questa operazione:

* I server di linguaggio possono essere incorporati in VSIX come file di contenuto.
* Creare un file MSI per installare il server di linguaggio e/o i runtime necessari.
* Fornire istruzioni sul Marketplace per informare gli utenti su come ottenere runtime e server di linguaggio.

### <a name="textmate-grammar-files"></a>File di grammatica TextMate

LSP non include la specifica su come fornire la colorazione del testo per le lingue. Per fornire una colorazione personalizzata per le lingue Visual Studio, gli sviluppatori di estensioni possono usare un file di grammatica TextMate. Per aggiungere file di grammatica o tema TextMate personalizzati, seguire questa procedura:

1. Creare una cartella denominata "Grammars" all'interno dell'estensione (o può essere qualsiasi nome scelto).

2. All'interno della cartella *Grammars* includere tutti i file con estensione *\* tmlanguage,* *\* plist,* *\* tmtheme* o *\* json* che forniscono colorazione personalizzata.

   > [!TIP]
   > Un file *con estensione tmtheme* definisce il mapping degli ambiti Visual Studio classificazioni (chiavi di colore denominate). Per istruzioni, è possibile fare riferimento al file con estensione *tmtheme* globale nella directory *%ProgramFiles(x86)%\Microsoft Visual Studio \\ \<version> \\ \<SKU> \Common7\IDE\CommonExtensions\Microsoft\TextMate\Starterkit\Themesg.*

3. Creare un file *con estensione pkgdef* e aggiungere una riga simile alla seguente:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Fare clic con il pulsante destro del mouse sui file e **scegliere Proprietà**. Impostare **l'azione** Compila **su Contenuto** e impostare **la proprietà Includi in VSIX** su **true.**

Dopo aver completato i passaggi precedenti, viene aggiunta una cartella *Grammars* alla directory di installazione del pacchetto come origine del repository denominata "MyLang" ('MyLang' è solo un nome per la risoluzione dell'ambiguità e può essere qualsiasi stringa univoca). Tutte le grammatiche (file con estensione *tmlanguage)* e i file di tema (file con estensione *tmtheme)* in questa directory vengono prelevate come potenziali e sostienino le grammatiche incorporate fornite con TextMate. Se le estensioni dichiarate del file di grammatica corrispondono all'estensione del file aperto, TextMate verrà aperto.

## <a name="create-a-simple-language-client"></a>Creare un client di linguaggio semplice

### <a name="main-interface---ilanguageclient"></a>Interfaccia principale - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)

Dopo aver creato il progetto VSIX, aggiungere NuGet seguenti al progetto:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Quando si accetta una dipendenza dal pacchetto NuGet dopo aver completato i passaggi precedenti, anche i pacchetti Newtonsoft.Json e StreamJsonRpc vengono aggiunti al progetto. Non aggiornare questi pacchetti a meno che non si sia certi che tali nuove versioni verranno installate nella versione di **Visual Studio destinazione dell'estensione.** Gli assembly non verranno inclusi in VSIX. verranno invece prelevati dalla directory di Visual Studio di installazione. Se si fa riferimento a una versione più recente degli assembly rispetto a quella installata nel computer di un utente, l'estensione non funzionerà.

È quindi possibile creare una nuova classe che implementa [l'interfaccia ILanguageClient,](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true) ovvero l'interfaccia principale necessaria per i client di linguaggio che si connettono a un server linguistico basato su LSP.

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

I metodi principali che devono essere implementati sono [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) [e ActivateAsync.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true) [OnLoadedAsync viene](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) chiamato quando Visual Studio ha caricato l'estensione e il server di linguaggio è pronto per l'avvio. In questo metodo è possibile richiamare immediatamente il delegato [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) per segnalare che il server del linguaggio deve essere avviato oppure è possibile eseguire logica aggiuntiva e richiamare [StartAsync in un secondo](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) momento. **Per attivare il server di linguaggio, è necessario chiamare StartAsync a un certo punto.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true) è il metodo eventualmente richiamato chiamando il [delegato StartAsync.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) Contiene la logica per avviare il server di linguaggio e stabilire la connessione. Deve essere restituito un oggetto connessione che contiene flussi per la scrittura nel server e la lettura dal server. Tutte le eccezioni generate qui vengono intercettate e visualizzate all'utente tramite un messaggio della barra informazioni in Visual Studio.

### <a name="activation"></a>Activation

Dopo aver implementato la classe client del linguaggio, è necessario definire due attributi per definire come verrà caricata in Visual Studio e attivata:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio usa [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) per gestire i relativi punti di estendibilità. [L'attributo](/dotnet/api/system.componentmodel.composition.exportattribute) Export indica Visual Studio che questa classe deve essere prelevata come punto di estensione e caricata nel momento appropriato.

Per usare MEF, è anche necessario definire MEF come asset nel manifesto VSIX.

Aprire la finestra di progettazione del manifesto VSIX e passare alla **scheda** Asset:

![aggiungere un asset MEF](media/lsp-add-asset.png)

Fare **clic su** Nuovo per creare un nuovo asset:

![definire l'asset MEF](media/lsp-define-asset.png)

* **Tipo:** Microsoft.VisualStudio.MefComponent
* **Origine:** progetto nella soluzione corrente
* **Project**: [Progetto]

### <a name="content-type-definition"></a>Definizione del tipo di contenuto

Attualmente, l'unico modo per caricare l'estensione del server del linguaggio basata su LSP è il tipo di contenuto file. Ovvero, quando si definisce la classe client del linguaggio (che implementa [ILanguageClient),](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)è necessario definire i tipi di file che, quando aperti, causeranno il caricamento dell'estensione. Se non viene aperto alcun file corrispondente al tipo di contenuto definito, l'estensione non verrà caricata.

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

Nell'esempio precedente viene creata una definizione del tipo di contenuto per i file che terminano con *l'estensione bar.* Alla definizione del tipo di contenuto viene assegnato il nome "bar" e deve derivare da [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017&preserve-view=true).

Dopo aver aggiunto una definizione del tipo di contenuto, è possibile definire quando caricare l'estensione client del linguaggio nella classe client del linguaggio:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

L'aggiunta del supporto per i server di linguaggio LSP non richiede l'implementazione del proprio sistema di progetto Visual Studio. I clienti possono aprire un singolo file o una cartella in Visual Studio iniziare a usare il servizio di linguaggio. In realtà, il supporto per i server di linguaggio LSP è progettato per funzionare solo in scenari di file/cartelle aperte. Se viene implementato un sistema di progetto personalizzato, alcune funzionalità ,ad esempio le impostazioni, non funzionano.

## <a name="advanced-features"></a>Funzionalità avanzate

### <a name="settings"></a>Impostazioni

Il supporto per le impostazioni personalizzate specifiche del server di lingua è disponibile, ma è ancora in corso di miglioramento. Impostazioni specifici di ciò che il server linguistico supporta e in genere controllano il modo in cui il server di linguaggio genera dati. Ad esempio, un server linguistico potrebbe avere un'impostazione per il numero massimo di errori segnalati. Gli autori di estensioni definiscono un valore predefinito, che può essere modificato dagli utenti per progetti specifici.

Seguire questa procedura per aggiungere il supporto per le impostazioni all'estensione del servizio di linguaggio LSP:

1. Aggiungere un file JSON (ad esempio, *MockLanguageExtensionSettings.jssu*) al progetto che contiene le impostazioni e i relativi valori predefiniti. Esempio:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Fare clic con il pulsante destro del mouse sul file JSON e **scegliere Proprietà**. Impostare **l'azione** di compilazione su "Content" e la proprietà "Include in VSIX" su **true.**

3. Implementare ConfigurationSections e restituire l'elenco di prefissi per le impostazioni definite nel file JSON (in Visual Studio Code verrà mappato al nome della sezione di configurazione in package.jssu):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Aggiungere un file con estensione pkgdef al progetto (aggiungere un nuovo file di testo e modificare l'estensione del file in .pkgdef). Il file pkgdef deve contenere queste informazioni:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Esempio:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Fare clic con il pulsante destro del mouse sul file con estensione pkgdef e scegliere **Proprietà**. Impostare **l'azione** Di compilazione **su Contenuto** e la proprietà Includi **in VSIX** su **true.**

6. Aprire il file *source.extension.vsixmanifest* e aggiungere un asset nella **scheda** Asset:

   ![modificare l'asset vspackage](media/lsp-add-vspackage-asset.png)

   * **Tipo:** Microsoft.VisualStudio.VsPackage
   * **Origine:** file nel file system
   * **Percorso**: [Percorso del file *con estensione pkgdef]*

### <a name="user-editing-of-settings-for-a-workspace&quot;></a>Modifica da parte dell'utente delle impostazioni per un'area di lavoro

1. L'utente apre un'area di lavoro contenente i file di proprietà del server.
2. L'utente aggiunge un file nella *cartella vs* denominata *VSWorkspaceSettings.jsin*.
3. L'utente aggiunge una riga *alVSWorkspaceSettings.jsfile* per un'impostazione fornita dal server. Esempio:

    ```json
    {
        &quot;foo.maxNumberOfProblems&quot;: 10
    }
    ```

### <a name=&quot;enable-diagnostics-tracing&quot;></a>Abilitare la traccia diagnostica

La traccia diagnostica può essere abilitata per l'output di tutti i messaggi tra il client e il server, che può essere utile durante il debug dei problemi. Per abilitare la traccia diagnostica, eseguire le operazioni seguenti:

1. Aprire o creare il file di impostazioni dell'VSWorkspaceSettings.jsdi lavoro (vedere &quot;Modifica delle impostazioni per *un'area* di lavoro da parte dell'utente").
2. Aggiungere la riga seguente nel file JSON delle impostazioni:

```json
{
    "foo.trace.server": "Off"
}
```

Esistono tre valori possibili per il livello di dettaglio della traccia:

* "Off": traccia disattivata completamente
* "Messages": traccia attivata, ma vengono tracciati solo il nome del metodo e l'ID risposta.
* "Verbose": traccia attivata; viene tracciato l'intero messaggio RPC.

Quando la traccia è attivata, il contenuto viene scritto in un file nella directory *%temp%\VisualStudio\LSP.* Il log segue il formato di *denominazione [LanguageClientName]-[Datetime Stamp].log*. Attualmente, la traccia può essere abilitata solo per scenari di apertura di cartelle. L'apertura di un singolo file per attivare un server di linguaggio non dispone del supporto per la traccia diagnostica.

### <a name="custom-messages"></a>Messaggi personalizzati

Sono disponibili API per facilitare il passaggio e la ricezione di messaggi dal server di linguaggio che non fanno parte del protocollo server di linguaggio standard. Per gestire i messaggi personalizzati, implementare [l'interfaccia ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) nella classe client del linguaggio. [La libreria VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) viene usata per trasmettere messaggi personalizzati tra il client del linguaggio e il server di linguaggio. Poiché l'estensione client del linguaggio LSP è esattamente come qualsiasi altra estensione Visual Studio, è possibile decidere di aggiungere altre funzionalità (non supportate dal provider di servizi di configurazione locale) a Visual Studio (usando altre API Visual Studio) nell'estensione tramite messaggi personalizzati.

#### <a name="receive-custom-messages"></a>Ricevere messaggi personalizzati

Per ricevere messaggi personalizzati dal server di linguaggio, implementare la proprietà [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017&preserve-view=true) in [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) e restituire un oggetto in grado di gestire i messaggi personalizzati. Di seguito è riportato un esempio:

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

Per inviare messaggi personalizzati al server di linguaggio, implementare [il metodo AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017&preserve-view=true) in [ILanguageClientCustomMessage.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) Questo metodo viene richiamato quando il server di linguaggio viene avviato e pronto per ricevere messaggi. Un [oggetto JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) viene passato come parametro, che è quindi possibile mantenere per inviare messaggi al server di linguaggio usando le API [VS-StreamJsonRpc.](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) Di seguito è riportato un esempio:

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

A volte uno sviluppatore di estensioni potrebbe voler intercettare i messaggi LSP inviati e ricevuti dal server di linguaggio. Ad esempio, uno sviluppatore di estensioni potrebbe voler modificare il parametro del messaggio inviato per un messaggio LSP specifico o modificare i risultati restituiti dal server di linguaggio per una funzionalità LSP (ad esempio completamenti). Quando necessario, gli sviluppatori di estensioni possono usare l'API MiddleLayer per intercettare i messaggi LSP.

Ogni messaggio LSP ha una propria interfaccia di livello intermedio per l'intercettazione. Per intercettare un messaggio specifico, creare una classe che implementa l'interfaccia del livello intermedio per il messaggio. Implementare quindi [l'interfaccia ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) nella classe client del linguaggio e restituire un'istanza dell'oggetto nella [proprietà MiddleLayer.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017&preserve-view=true) Di seguito è riportato un esempio:

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

La funzionalità del livello intermedio è ancora in fase di sviluppo e non è ancora completa.

## <a name="sample-lsp-language-server-extension"></a>Estensione del server del linguaggio LSP di esempio

Per visualizzare il codice sorgente di un'estensione di esempio usando l'API client LSP in Visual Studio, vedere l'esempio [LSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol)VSSDK-Extensibility-Samples .

## <a name="faq"></a>Domande frequenti

**Si vuole creare un sistema di progetto personalizzato per integrare il server di linguaggio LSP per offrire un supporto delle funzionalità più ricco in Visual Studio, come procedere?**

Il supporto per i server di linguaggi basati su [](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) LSP in Visual Studio si basa sulla funzionalità apri cartella ed è progettato per non richiedere un sistema di progetto personalizzato. È possibile compilare un sistema di progetto personalizzato seguendo le istruzioni riportate [qui,](https://github.com/Microsoft/VSProjectSystem)ma alcune funzionalità, ad esempio le impostazioni, potrebbero non funzionare. La logica di inizializzazione predefinita per i server di linguaggio LSP è passare il percorso della cartella radice della cartella attualmente aperta, quindi se si usa un sistema di progetto personalizzato, potrebbe essere necessario fornire logica personalizzata durante l'inizializzazione per assicurarsi che il server del linguaggio possa essere avviato correttamente.

**Ricerca per categorie il supporto del debugger?**

In una versione futura verrà fornito il [supporto per il](https://code.visualstudio.com/docs/extensionAPI/api-debugging) protocollo di debug comune.

**Se è già installato un servizio di linguaggio supportato da Visual Studio ,ad esempio JavaScript, è comunque possibile installare un'estensione del server di linguaggio LSP che offre funzionalità aggiuntive,ad esempio linting?**

Sì, ma non tutte le funzionalità funzionano correttamente. L'obiettivo finale per le estensioni del server del linguaggio LSP è abilitare i servizi di linguaggio non supportati in modo nativo da Visual Studio. È possibile creare estensioni che offrono supporto aggiuntivo usando i server di linguaggio LSP, ma alcune funzionalità ( ad esempio IntelliSense) non saranno un'esperienza uniforme. In generale, è consigliabile usare le estensioni del server del linguaggio LSP per offrire nuove esperienze di linguaggio, non estendendo quelle esistenti.

**Dove si pubblica il vsIX del server di linguaggio LSP completato?**

Vedere le istruzioni del Marketplace [qui.](walkthrough-publishing-a-visual-studio-extension.md)

## <a name="see-also"></a>Vedi anche

- [Aggiungere il supporto di altri linguaggi all'editor di Visual Studio](../ide/adding-visual-studio-editor-support-for-other-languages.md)
