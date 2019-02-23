---
title: 'Procedura dettagliata: Displaying Light Bulb Suggestions | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ce896b0d0039f8ae06680b730fc7bd3793a8206
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694426"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Procedura dettagliata: Visualizzare suggerimenti con lampadina
Le lampadine sono icone nell'editor di Visual Studio che si espandono per visualizzare un set di azioni, ad esempio, correzioni dei problemi identificati dagli analizzatori di codice predefiniti o il refactoring del codice.

 Negli editor di Visual c# e Visual Basic, è anche possibile usare .NET Compiler Platform ("Roslyn") per scrivere e creare pacchetti personalizzati analizzatori di codice con le azioni che consentono di visualizzare le lampadine automaticamente. Per altre informazioni, vedere:

- [Procedura: Scrivere un C# diagnostica e correzione del codice](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [Procedura: Scrivere una diagnostica di Visual Basic e correzione del codice](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  Altri linguaggi come C++ forniscono anche le lampadine per alcune azioni rapide, ad esempio, un suggerimento per creare un'implementazione stub della funzione.

  Ecco come appare una lampadina. In un progetto Visual Basic o Visual c#, una sottolineatura ondulata rossa viene visualizzata sotto un nome di variabile quando non è valido. Se si passa il mouse sull'identificatore non valido, un indicatore lampadina viene visualizzata accanto al cursore.

  ![lampadina](../extensibility/media/lightbulb.png "a forma di lampadina")

  Se si fa clic sulla freccia in giù per la lampadina, viene visualizzato un set di azioni consigliate, insieme a un'anteprima dell'azione selezionata. In questo caso, Mostra le modifiche apportate al codice se si esegue l'azione.

  ![Anteprima lampadina](../extensibility/media/lightbulbpreview.png "LightBulbPreview")

  È possibile usare le lampadine per fornire il proprio le azioni consigliate. Ad esempio, è possibile fornire azioni per spostare aprendo le parentesi graffe in una nuova riga o li sposta alla fine della riga precedente. Procedura dettagliata illustra come creare un indicatore lampadina che viene visualizzato sulla parola corrente e ha due azioni consigliate: **Converti in maiuscolo** e **Convert in lettere minuscole**.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, Visual Studio SDK è non installare dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Creare un progetto Managed Extensibility Framework (MEF)

1.  Creare un progetto c# VSIX. (Nelle **nuovo progetto** finestra di dialogo, seleziona **Visual c# / Extensibility**, quindi **progetto VSIX**.) Assegnare alla soluzione il nome `LightBulbTest`.

2.  Aggiungere un **classificatore Editor** modello di elemento al progetto. Per altre informazioni, vedere [creare un'estensione con un modello di elemento editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3.  Eliminare i file di classe esistenti.

4.  Aggiungere il seguente riferimento al progetto e impostare **Copia localmente** a `False`:

     *Microsoft.VisualStudio.Language.Intellisense*

5.  Aggiungere un nuovo file di classe e denominarla **LightBulbTest**.

6.  Aggiungere quanto segue usando istruzioni:

    ```csharp
    using System;
    using System.Linq;
    using System.Collections.Generic;
    using System.Threading.Tasks;
    using Microsoft.VisualStudio.Language.Intellisense;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Operations;
    using Microsoft.VisualStudio.Utilities;
    using System.ComponentModel.Composition;
    using System.Threading;

    ```

## <a name="implement-the-light-bulb-source-provider"></a>Implementare il provider dell'origine lampadina

1.  Nel *LightBulbTest.cs* file di classe, eliminare la classe LightBulbTest. Aggiungere una classe denominata **TestSuggestedActionsSourceProvider** che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Esportarla con il nome **Test azioni consigliate** e un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> impostato su "text".

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2.  All'interno della classe di provider di origine, importare il <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> e aggiungerlo come una proprietà.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> per restituire un <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> oggetto. L'origine è descritto nella sezione successiva.

    ```csharp
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)
    {
        if (textBuffer == null || textView == null)
        {
            return null;
        }
        return new TestSuggestedActionsSource(this, textView, textBuffer);
    }
    ```

## <a name="implement-the-isuggestedactionsource"></a>Implementare il ISuggestedActionSource
 L'origine azione suggerita è responsabile per la raccolta di set di azioni consigliate e aggiungerli nel contesto corretto. In questo caso, il contesto è la parola corrente e le azioni consigliate sono **UpperCaseSuggestedAction** e **LowerCaseSuggestedAction**, come descritto nella sezione seguente.

1.  Aggiungere una classe **TestSuggestedActionsSource** che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2.  Aggiungere i campi privati, di sola lettura per il provider dell'origine azione suggerita, buffer di testo e la visualizzazione di testo.

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3.  Aggiungere un costruttore che imposta i campi privati.

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4.  Aggiungere un metodo privato che restituisce la parola che si trova attualmente sotto il cursore. Il metodo seguente è simile nella posizione corrente del cursore e chiede lo strumento di navigazione di struttura di testo per l'ambito della parola. Se il cursore si trova in una parola, il <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> viene restituito nel parametro out; in caso contrario, il `out` parametro è `null` e il metodo restituisce `false`.

    ```csharp
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)
    {
        ITextCaret caret = m_textView.Caret;
        SnapshotPoint point;

        if (caret.Position.BufferPosition > 0)
        {
            point = caret.Position.BufferPosition - 1;
        }
        else
        {
            wordExtent = default(TextExtent);
            return false;
        }

        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);

        wordExtent = navigator.GetExtentOfWord(point);
        return true;
    }
    ```

5.  Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>. L'editor chiama questo metodo per sapere se si desidera visualizzare la lampadina. Viene effettuata la chiamata spesso, ad esempio, ogni volta che il cursore si sposta da una riga a altra o quando il mouse sulla sottolineatura a zigzag di un errore. È asincrona per consentire altre operazioni dell'interfaccia utente di svolgere le proprie e che stia usando questo metodo. Nella maggior parte dei casi, questo metodo deve eseguire alcune analisi e l'analisi della riga corrente, in modo che l'elaborazione potrebbe richiedere alcuni minuti.

     In questa implementazione, ottiene in modo asincrono il <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> e determina se l'extent è significativo, come illustrato, se questo dispone di un testo diverso da uno spazio vuoto.

    ```csharp
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)
    {
        return Task.Factory.StartNew(() =>
        {
            TextExtent extent;
            if (TryGetWordUnderCaret(out extent))
            {
                // don't display the action if the extent has whitespace
                return extent.IsSignificant;
              }
            return false;
        });
    }
    ```

6.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> metodo, che restituisce una matrice di <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> oggetti che contengono i diversi <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> oggetti. Questo metodo viene chiamato quando la lampadina viene espanso.

    > [!WARNING]
    >  Assicurarsi che le implementazioni di `HasSuggestedActionsAsync()` e `GetSuggestedActions()` sono coerente; ovvero, se `HasSuggestedActionsAsync()` restituisce `true`, quindi `GetSuggestedActions()` deve avere alcune azioni per la visualizzazione. In molti casi `HasSuggestedActionsAsync()` viene chiamato appena prima `GetSuggestedActions()`, ma non sempre è il caso. Ad esempio, se l'utente richiama le azioni di lampadina premendo (**CTRL +** .) solo `GetSuggestedActions()` viene chiamato.

    ```csharp
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)
    {
        TextExtent extent;
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)
        {
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };
        }
        return Enumerable.Empty<SuggestedActionSet>();
    }
    ```

7.  Definire un `SuggestedActionsChanged` evento.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8.  Per completare l'implementazione, aggiungere le implementazioni per le `Dispose()` e `TryGetTelemetryId()` metodi. Non si vuole eseguire operazioni di dati di telemetria, restituire `false` e impostare il GUID `Empty`.

    ```csharp
    public void Dispose()
    {
    }

    public bool TryGetTelemetryId(out Guid telemetryId)
    {
        // This is a sample provider and doesn't participate in LightBulb telemetry
        telemetryId = Guid.Empty;
        return false;
    }
    ```

## <a name="implement-light-bulb-actions"></a>Implementare le azioni di lampadina

1.  Nel progetto, aggiungere un riferimento a *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* e impostare **Copia localmente** a `False`.

2.  Creare due classi, denominate `UpperCaseSuggestedAction` e `LowerCaseSuggestedAction`. Entrambe le classi implementano <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Le due classi sono simili, con l'unica eccezione che una chiama <xref:System.String.ToUpper%2A> e l'altra chiama <xref:System.String.ToLower%2A>. Anche se i passaggi seguenti descrivono solo la classe dell'azione per le maiuscole, è necessario implementarle entrambe. Usare i passaggi per l'implementazione dell'azione per le maiuscole come criterio per l'implementazione dell'azione per le minuscole.

3.  Aggiungere quanto segue usando istruzioni per queste classi:

    ```csharp
    using Microsoft.VisualStudio.Imaging.Interop;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Documents;
    using System.Windows.Media;

    ```

4.  Dichiarare un set di campi privati.

    ```csharp
    private ITrackingSpan m_span;
    private string m_upper;
    private string m_display;
    private ITextSnapshot m_snapshot;
    ```

5.  Aggiungere un costruttore che imposta i campi.

    ```csharp
    public UpperCaseSuggestedAction(ITrackingSpan span)
    {
        m_span = span;
        m_snapshot = span.TextBuffer.CurrentSnapshot;
        m_upper = span.GetText(m_snapshot).ToUpper();
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));
    }
    ```

6.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> metodo in modo che venga visualizzato l'anteprima di azione.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> metodo in modo che restituisca un oggetto vuoto <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> enumerazione.

    ```csharp
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)
    {
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);
    }
    ```

8.  Implementare le proprietà nel modo indicato di seguito.

    ```csharp
    public bool HasActionSets
    {
        get { return false; }
    }
    public string DisplayText
    {
        get { return m_display; }
    }
    public ImageMoniker IconMoniker
    {
       get { return default(ImageMoniker); }
    }
    public string IconAutomationText
    {
        get
        {
            return null;
        }
    }
    public string InputGestureText
    {
        get
        {
            return null;
        }
    }
    public bool HasPreview
    {
        get { return true; }
    }
    ```

9. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> sostituendo il testo nell'intervallo con l'equivalente in maiuscole.

    ```csharp
    public void Invoke(CancellationToken cancellationToken)
    {
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);
    }
    ```

    > [!WARNING]
    >  L'azione lampadina **Invoke** metodo non dovrebbe visualizzare l'interfaccia utente. Se l'azione di visualizzare la nuova interfaccia utente (ad esempio una finestra di anteprima o la selezione), non viene visualizzata l'interfaccia utente direttamente dall'interno di **Invoke** metodo ma invece pianificare per visualizzare l'interfaccia utente dopo la restituzione da **Invoke**.

10. Per completare l'implementazione, aggiungere il `Dispose()` e `TryGetTelemetryId()` metodi.

    ```csharp
    public void Dispose()
    {
    }

    public bool TryGetTelemetryId(out Guid telemetryId)
    {
        // This is a sample action and doesn't participate in LightBulb telemetry
        telemetryId = Guid.Empty;
        return false;
    }
    ```

11. Non dimenticare di eseguire la stessa operazione `LowerCaseSuggestedAction` modificando il testo visualizzato per "convertire"{0}' in lettere minuscole "e la chiamata <xref:System.String.ToUpper%2A> a <xref:System.String.ToLower%2A>.

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione LightBulbTest ed eseguirlo nell'istanza sperimentale.

1.  Compilare la soluzione.

2.  Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3.  Creare un file di testo e digitare alcune parole. Verrà visualizzata una lampadina a sinistra del testo.

     ![test della lampadina](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4.  Posizionare la lampadina. Verrà visualizzata una freccia verso il basso.

5.  Quando si fa clic sulla lampadina, dovrebbe essere visualizzata la finestra di due azioni consigliate, con l'anteprima dell'azione selezionata.

     ![test della lampadina, espanso](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")

6.  Se si sceglie la prima azione, tutto il testo nella parola corrente deve essere convertito in lettere maiuscole. Se si sceglie la seconda azione, tutto il testo deve essere convertito in lettere minuscole.
