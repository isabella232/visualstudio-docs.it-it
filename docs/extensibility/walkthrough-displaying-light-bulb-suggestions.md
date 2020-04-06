---
title: 'Procedura dettagliata: Visualizzazione dei suggerimenti per lampadina Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09773e2be81ce51971709db590a07ca9960104fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697482"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Procedura dettagliata: Visualizzare i suggerimenti per le lampadine
Le lampadine sono icone nell'editor di Visual Studio che si espandono per visualizzare un set di azioni, ad esempio le correzioni per i problemi identificati dagli analizzatori di codice incorporati o dal refactoring del codice.

 Negli editor di Visual C e Visual Basic è inoltre possibile utilizzare la piattaforma del compilatore .NET ("Roslyn") per scrivere e creare pacchetti di analizzatori di codice personalizzati con azioni che visualizzano automaticamente le lampadine. Per altre informazioni, vedere:

- [Procedura: Scrivere una correzione di codice e diagnostica di C](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [Procedura: scrivere una correzione di codice e diagnostica di Visual BasicHow To: Write a Visual Basic diagnostic and code fix](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  Anche altri linguaggi, ad esempio il linguaggio C, forniscono lampadine per alcune azioni rapide, ad esempio un suggerimento per creare un'implementazione stub di tale funzione.

  Ecco come appare una lampadina. In un progetto di Visual Basic o Visual C, una sottolineatura ondulata rossa viene visualizzata sotto un nome di variabile quando non è valido. Se si passa il mouse sull'identificatore non valido, viene visualizzata una lampadina accanto al cursore.

  ![lampadina](../extensibility/media/lightbulb.png "Lampadina")

  Se si fa clic sulla freccia giù accanto alla lampadina, viene visualizzato un set di azioni suggerite, insieme a un'anteprima dell'azione selezionata. In questo caso, mostra le modifiche apportate al codice se si esegue l'azione.

  ![anteprima di lampadina](../extensibility/media/lightbulbpreview.png "LightBulbPreview")

  È possibile utilizzare le lampadine per fornire le proprie azioni suggerite. Ad esempio, è possibile fornire azioni per spostare le parentesi graffe di apertura in una nuova riga o spostarle alla fine della riga precedente. Nella procedura dettagliata seguente viene illustrato come creare una lampadina che viene visualizzata nella parola corrente e dispone di due azioni suggerite: Converti in **maiuscolo** e **Converti in minuscolo**.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It's included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Creare un progetto Managed Extensibility Framework (MEF)

1. Creare un progetto VSIX di C. (Nella finestra di dialogo **Nuovo progetto,** selezionare **Visual Cè / Extensibility**, quindi **Progetto VSIX**. Denominare `LightBulbTest`la soluzione .

2. Aggiungere un modello di elemento **Classificatore editor** al progetto. Per ulteriori informazioni, consultate [Creare un'estensione con un modello di elemento dell'editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Eliminare i file di classe esistenti.

4. Aggiungere il seguente riferimento al progetto e `False`impostare **Copia localmente** su:

     *Microsoft.VisualStudio.Language.Intellisense*

5. Aggiungere un nuovo file di classe e denominarlo **LightBulbTest**.

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

## <a name="implement-the-light-bulb-source-provider"></a>Implementare il fornitore della sorgente di lampadina

1. Nel file di *classe LightBulbTest.cs* eliminare la classe LightBulbTest. Aggiungere una classe denominata **TestSuggestedActionsSourceProvider** che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Esportatelo con un nome di <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> **Azioni suggerite** di prova e un "testo".

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. All'interno della classe <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> del provider di origine, importare l'oggetto e aggiungerlo come proprietà.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> per restituire un oggetto. L'origine viene descritta nella sezione successiva.

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

## <a name="implement-the-isuggestedactionsource"></a>Implementare ISuggestedActionSourceImplement the ISuggestedActionSource
 L'origine dell'azione suggerita è responsabile della raccolta del set di azioni suggerite e dell'aggiunta nel contesto corretto. In questo caso, il contesto è la parola corrente e le azioni suggerite sono **UpperCaseSuggestedAction** e **LowerCaseSuggestedAction**, descritte nella sezione seguente.

1. Aggiungere una classe **TestSuggestedActionsSource** che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.

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

4. Aggiungere un metodo privato che restituisce la parola attualmente sotto il cursore. Il metodo seguente esamina la posizione corrente del cursore e chiede al navigatore della struttura di testo l'estensione della parola. Se il cursore si <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> trova su una parola, l'oggetto viene restituito nel parametro out; in caso `out` contrario, il parametro is `null` e il metodo restituisce `false`.

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

5. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>. L'editor chiama questo metodo per scoprire se visualizzare la lampadina. Questa chiamata viene effettuata spesso, ad esempio, ogni volta che il cursore si sposta da una riga a un'altra o quando il mouse passa su una linea ondulata di errore. È asincrono per consentire ad altre operazioni dell'interfaccia utente di continuare mentre questo metodo funziona. Nella maggior parte dei casi, questo metodo deve eseguire alcune analisi e analisi della riga corrente, pertanto l'elaborazione potrebbe richiedere del tempo.

     In questa implementazione, ottiene <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> in modo asincrono il e determina se l'estensione è significativa, come in, se ha un testo diverso da spazio vuoto.

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

6. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> il metodo , <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> che restituisce <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> una matrice di oggetti che contengono i diversi oggetti. Questo metodo viene chiamato quando la lampadina viene espansa.

    > [!WARNING]
    > È necessario assicurarsi che `HasSuggestedActionsAsync()` le `GetSuggestedActions()` implementazioni di e sono coerenti; ovvero, se `HasSuggestedActionsAsync()` `true`restituisce `GetSuggestedActions()` , devono avere alcune azioni da visualizzare. In molti `HasSuggestedActionsAsync()` casi, viene `GetSuggestedActions()`chiamato poco prima , ma questo non è sempre il caso. Ad esempio, se l'utente richiama le azioni lampadina `GetSuggestedActions()` premendo solo (**CTRL .)** viene chiamato.

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

7. Definire `SuggestedActionsChanged` un evento.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. Per completare l'implementazione, `Dispose()` `TryGetTelemetryId()` aggiungere implementazioni per i metodi e . Non si vuole eseguire dati di `false` telemetria, quindi `Empty`è sufficiente restituire e impostare il GUID su .

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

## <a name="implement-light-bulb-actions"></a>Implementare le azioni della lampadina

1. Nel progetto aggiungere un riferimento a *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* `False`e **impostare Copia locale** su .

2. Creare due classi, denominate `UpperCaseSuggestedAction` e `LowerCaseSuggestedAction`. Entrambe le classi implementano <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Le due classi sono simili, con l'unica eccezione che una chiama <xref:System.String.ToUpper%2A> e l'altra chiama <xref:System.String.ToLower%2A>. Anche se i passaggi seguenti descrivono solo la classe dell'azione per le maiuscole, è necessario implementarle entrambe. Usare i passaggi per l'implementazione dell'azione per le maiuscole come criterio per l'implementazione dell'azione per le minuscole.

3. Aggiungere le direttive using seguenti per queste classi:Add the following using directives for these classes:

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
    private string m_upper;
    private string m_display;
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

6. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> il metodo in modo che visualizzi l'anteprima dell'azione.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> il metodo in <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> modo che restituisca un'enumerazione vuota.

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
    > Il metodo **Invoke** dell'azione lampadina non deve visualizzare l'interfaccia utente. Se l'azione visualizza una nuova interfaccia utente (ad esempio un'anteprima o una finestra di dialogo di selezione), non visualizzare l'interfaccia utente direttamente dal metodo **Invoke,** ma pianificare la visualizzazione dell'interfaccia utente dopo la restituzione da **Invoke**.

10. Per completare l'implementazione, aggiungere i `Dispose()` metodi e `TryGetTelemetryId()` .

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

11. Non dimenticare di fare la `LowerCaseSuggestedAction` stessa cosa per cambiare{0}il testo visualizzato in <xref:System.String.ToUpper%2A> "Converti ' in minuscolo" e la chiamata a <xref:System.String.ToLower%2A>.

## <a name="build-and-test-the-code"></a>Compilare e testare il codiceBuild and test the code
 Per testare questo codice, compilare la soluzione LightBulbTest ed eseguirla nell'istanza sperimentale.

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo e digitare alcune parole. Dovresti vedere una lampadina a sinistra del testo.

     ![test della lampadina](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. Puntare la lampadina. Dovresti vedere una freccia in giù.

5. Quando si fa clic sulla lampadina, dovrebbero essere visualizzate due azioni suggerite, insieme all'anteprima dell'azione selezionata.

     ![test della lampadina, espanso](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")

6. Se si fa clic sulla prima azione, tutto il testo nella parola corrente deve essere convertito in maiuscolo. Se si fa clic sulla seconda azione, tutto il testo deve essere convertito in lettere minuscole.
