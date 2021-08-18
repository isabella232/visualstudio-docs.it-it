---
title: 'Procedura dettagliata: Visualizzazione di suggerimenti per lampadine | Microsoft Docs'
description: Informazioni su come creare una lampadina nell'editor di Visual Studio visualizzato nella parola corrente e con due azioni suggerite usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f7775d370bb6502ef87751dbeea1a6d53966870e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028423"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Procedura dettagliata: Visualizzare i suggerimenti per le lampadine
Le lampadine sono icone nell'editor Visual Studio che si espandono per visualizzare un set di azioni, ad esempio correzioni per i problemi identificati dagli analizzatori di codice predefiniti o dal refactoring del codice.

 Negli editor di Visual C# e Visual Basic è anche possibile usare il .NET Compiler Platform ("Roslyn") per scrivere e creare un pacchetto di analizzatori di codice personalizzati con azioni che visualizzano automaticamente le lampadine. Per altre informazioni, vedere:

- [Procedura: Scrivere una correzione di codice e diagnostica C#](https://github.com/dotnet/roslyn/blob/master/docs/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix.md)

- [Procedura: Scrivere una correzione Visual Basic diagnostica e codice](https://github.com/dotnet/roslyn/blob/master/docs/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix.md)

  Altri linguaggi come C++ forniscono anche lampadine per alcune azioni rapide, ad esempio un suggerimento per creare un'implementazione stub di tale funzione.

  Ecco l'aspetto di una lampadina. In un Visual Basic o in un progetto Visual C# viene visualizzata una barra arrossata rossa sotto un nome di variabile quando non è valida. Se si passa il mouse sull'identificatore non valido, accanto al cursore viene visualizzata una lampadina.

  ![lampadina](../extensibility/media/lightbulb.png "Lampadina")

  Se si fa clic sulla freccia giù accanto alla lampadina, viene visualizzato un set di azioni suggerite, insieme a un'anteprima dell'azione selezionata. In questo caso, vengono visualizzate le modifiche apportate al codice se si esegue l'azione.

  ![anteprima di lampadina](../extensibility/media/lightbulbpreview.png "LightBulbPreview")

  È possibile usare le lampadine per fornire le proprie azioni suggerite. Ad esempio, è possibile fornire azioni per spostare le parentesi graffe di apertura in una nuova riga o spostarle alla fine della riga precedente. La procedura dettagliata seguente illustra come creare una lampadina visualizzata nella parola corrente e con due azioni suggerite: **Converti** in maiuscolo e **Converti in minuscolo.**

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Creare un Managed Extensibility Framework (MEF)

1. Creare un progetto VSIX C#. Nella finestra **di dialogo Nuovo Project** selezionare Visual **C# /Extensibility** e quindi **VSIX Project**. Assegnare alla soluzione il nome `LightBulbTest` .

2. Aggiungere un **modello di elemento Editor Classifier** al progetto. Per altre informazioni, vedere [Creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Eliminare i file di classe esistenti.

4. Aggiungere il riferimento seguente al progetto e impostare **Copia locale** su `False` :

     *Microsoft.VisualStudio.Language.Intellisense*

5. Aggiungere un nuovo file di classe e **denomarlo LightBulbTest**.

6. Aggiungere le seguenti direttive using:

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

## <a name="implement-the-light-bulb-source-provider"></a>Implementare il provider di sorgente lampadina

1. Nel file *di classe LightBulbTest.cs* eliminare la classe LightBulbTest. Aggiungere una classe denominata **TestSuggestedActionsSourceProvider che** implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> . Esportarlo con il nome Test Suggested Actions (Azioni **suggerite test)** e <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> un valore di "text".

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. All'interno della classe del provider di origine <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> importare e aggiungerlo come proprietà.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> il metodo per restituire un oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> . L'origine viene illustrata nella sezione successiva.

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

## <a name="implement-the-isuggestedactionsource"></a>Implementare ISuggestedActionSource
 L'origine dell'azione suggerita è responsabile della raccolta del set di azioni suggerite e dell'aggiunta nel contesto giusto. In questo caso, il contesto è la parola corrente e le azioni suggerite sono **UpperCaseSuggestedAction** e **LowerCaseSuggestedAction**, illustrate nella sezione seguente.

1. Aggiungere una classe **TestSuggestedActionsSource che** implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. Aggiungere campi privati di sola lettura per il provider di origine dell'azione suggerito, il buffer di testo e la visualizzazione di testo.

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. Aggiungere un costruttore che imposta i campi privati.

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. Aggiungere un metodo privato che restituisce la parola attualmente sotto il cursore. Il metodo seguente esamina la posizione corrente del cursore e chiede allo strumento di navigazione della struttura del testo l'estensione della parola. Se il cursore si trova su una parola, viene restituito nel parametro out; in caso contrario, il parametro è <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> e il metodo restituisce `out` `null` `false` .

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

5. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>. L'editor chiama questo metodo per determinare se visualizzare la lampadina. Questa chiamata viene effettuata spesso, ad esempio, ogni volta che il cursore si sposta da una riga a un'altra o quando il puntatore del mouse passa su una riga a scorrimento a scorrimento. È asincrono per consentire ad altre operazioni dell'interfaccia utente di continuare mentre questo metodo funziona. Nella maggior parte dei casi, questo metodo deve eseguire alcune analisi e analisi della riga corrente, quindi l'elaborazione potrebbe richiedere del tempo.

     In questa implementazione ottiene in modo asincrono e determina se l'extent è significativo, come in , se contiene testo diverso <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> da spazi vuoti.

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

6. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> il metodo , che restituisce una matrice di oggetti che contengono i diversi oggetti <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> . Questo metodo viene chiamato quando la lampadina viene espansa.

    > [!WARNING]
    > È necessario assicurarsi che le implementazioni di e siano coerenti, ad esempio se restituisce , devono essere visualizzate `HasSuggestedActionsAsync()` `GetSuggestedActions()` alcune `HasSuggestedActionsAsync()` `true` `GetSuggestedActions()` azioni. In molti casi, `HasSuggestedActionsAsync()` viene chiamato subito prima di , ma questo non è sempre il `GetSuggestedActions()` caso. Ad esempio, se l'utente richiama le azioni della lampadina premendo (**CTRL+** .) viene chiamato `GetSuggestedActions()` solo .

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

7. Definire un `SuggestedActionsChanged` evento.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. Per completare l'implementazione, aggiungere le implementazioni per `Dispose()` i metodi e `TryGetTelemetryId()` . Non si vogliono eseguire dati di telemetria, quindi è sufficiente restituire `false` e impostare il GUID su `Empty` .

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

## <a name="implement-light-bulb-actions"></a>Implementare azioni lampadina

1. Nel progetto aggiungere un riferimento aMicrosoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll *e* impostare **Copia locale** su `False` .

2. Creare due classi, denominate `UpperCaseSuggestedAction` e `LowerCaseSuggestedAction`. Entrambe le classi implementano <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Le due classi sono simili, con l'unica eccezione che una chiama <xref:System.String.ToUpper%2A> e l'altra chiama <xref:System.String.ToLower%2A>. Anche se i passaggi seguenti descrivono solo la classe dell'azione per le maiuscole, è necessario implementarle entrambe. Usare i passaggi per l'implementazione dell'azione per le maiuscole come criterio per l'implementazione dell'azione per le minuscole.

3. Aggiungere le direttive using seguenti per queste classi:

    ```csharp
    using Microsoft.VisualStudio.Imaging.Interop;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Documents;
    using System.Windows.Media;

    ```

4. Dichiarare un set di campi privati.

    ```csharp
    private ITrackingSpan m_span;
    private string m_upper;
    private string m_display;
    private ITextSnapshot m_snapshot;
    ```

5. Aggiungere un costruttore che imposta i campi.

    ```csharp
    public UpperCaseSuggestedAction(ITrackingSpan span)
    {
        m_span = span;
        m_snapshot = span.TextBuffer.CurrentSnapshot;
        m_upper = span.GetText(m_snapshot).ToUpper();
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));
    }
    ```

6. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> metodo in modo che visualizzi l'anteprima dell'azione.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> il metodo in modo che restituisca un'enumerazione <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> vuota.

    ```csharp
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)
    {
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);
    }
    ```

8. Implementare le proprietà nel modo indicato di seguito.

    ```csharp
    public bool HasActionSets
    {
        get { return false; }
    }
    public string DisplayText
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
    public void Invoke(CancellationToken cancellationToken)
    {
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);
    }
    ```

    > [!WARNING]
    > Non è previsto che il metodo Invoke dell'azione **della** lampadina mostri l'interfaccia utente. Se l'azione visualizza una nuova interfaccia utente ,ad esempio una finestra di dialogo di anteprima o di selezione, non visualizzare l'interfaccia utente direttamente dal metodo **Invoke,** ma pianificare la visualizzazione dell'interfaccia utente dopo la restituzione da **Invoke.**

10. Per completare l'implementazione, aggiungere `Dispose()` i metodi `TryGetTelemetryId()` e .

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

11. Non dimenticare di eseguire la stessa operazione per modificare il testo visualizzato `LowerCaseSuggestedAction` in "Convert ' ' to lower case" e {0} la chiamata a <xref:System.String.ToUpper%2A> <xref:System.String.ToLower%2A> .

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione LightBulbTest ed eseguirla nell'istanza sperimentale.

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo e digitare alcune parole. A sinistra del testo dovrebbe essere visualizzata una lampadina.

     ![test della lampadina](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. Posizionare il punto sulla lampadina. Verrà visualizzata una freccia verso il basso.

5. Quando si fa clic sulla lampadina, vengono visualizzate due azioni suggerite, insieme all'anteprima dell'azione selezionata.

     ![test della lampadina, espanso](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")

6. Se si fa clic sulla prima azione, tutto il testo nella parola corrente deve essere convertito in maiuscolo. Se si fa clic sulla seconda azione, tutto il testo deve essere convertito in lettere minuscole.
