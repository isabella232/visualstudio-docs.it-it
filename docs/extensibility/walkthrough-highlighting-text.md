---
title: 'Procedura dettagliata: Evidenziazione del testo Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c35b1a032993a6c183191aafff77d8adeba4a3ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697394"
---
# <a name="walkthrough-highlight-text"></a>Procedura dettagliata: Evidenziare il testoWalkthrough: Highlight text
È possibile aggiungere diversi effetti visivi all'editor creando parti del componente Managed Extensibility Framework (MEF). In questa procedura dettagliata viene illustrato come evidenziare ogni occorrenza della parola corrente in un file di testo. Se una parola si verifica più di una volta in un file di testo e si posiziona il punto di inserimento in un'occorrenza, ogni occorrenza viene evidenziata.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It's included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>Creare un progetto MEF

1. Creare un progetto VSIX di C. (Nella finestra di dialogo **Nuovo progetto,** selezionare **Visual Cè / Extensibility**, quindi **Progetto VSIX**. Denominare `HighlightWordTest`la soluzione .

2. Aggiungere un modello di elemento Classificatore editor al progetto. Per ulteriori informazioni, consultate [Creare un'estensione con un modello di elemento dell'editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Eliminare i file di classe esistenti.

## <a name="define-a-textmarkertag"></a>Definire un TextMarkerTagDefine a TextMarkerTag
 Il primo passaggio per evidenziare <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> il testo consiste nel creare una sottoclasse e definirne l'aspetto.

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Per definire un TextMarkerTag e un MarkerFormatDefinitionTo define a TextMarkerTag and a MarkerFormatDefinition

1. Aggiungere un file di classe e denominarlo **HighlightWordTag**.

2. Aggiungere i riferimenti seguenti:

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.VisualStudio.Text.Logic

    4. Microsoft.VisualStudio.Text.UI

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Composition

    7. Presentation.Core

    8. Presentation.Framework

3. Importare gli spazi dei nomi seguenti.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Linq;
    using System.Threading;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Operations;
    using Microsoft.VisualStudio.Text.Tagging;
    using Microsoft.VisualStudio.Utilities;
    using System.Windows.Media;
    ```

4. Creare una classe che <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> eredita `HighlightWordTag`da e denominarla .

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. Creare una seconda classe <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>che eredita `HighlightWordFormatDefinition`da e denominarla . Per utilizzare questa definizione di formato per il tag, è necessario esportarla con i seguenti attributi:

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: i tag utilizzano questo per fare riferimento a questo formato

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: in questo modo il formato viene visualizzato nell'interfaccia utente

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. Nel costruttore per HighlightWordFormatDefinition, definire il nome visualizzato e l'aspetto. Il Background proprietà definisce il colore di riempimento, mentre il Foreground proprietà definisce il colore del bordo.

    ```csharp
    public HighlightWordFormatDefinition()
    {
                this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. Nel costruttore per HighlightWordTag passare il nome della definizione di formato creata.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>Implementare un ITaggerImplement an ITagger
 Il passaggio successivo <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> consiste nell'implementare l'interfaccia. Questa interfaccia assegna, a un buffer di testo specificato, i tag che forniscono l'evidenziazione del testo e altri effetti visivi.

### <a name="to-implement-a-tagger"></a>Per implementare un tagger

1. Creare una classe <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> che `HighlightWordTag`implementa di `HighlightWordTagger`tipo e denominarla .

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. Aggiungere i seguenti campi privati e proprietà alla classe:

    - Oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, che corrisponde alla visualizzazione di testo corrente.

    - Oggetto <xref:Microsoft.VisualStudio.Text.ITextBuffer>, che corrisponde al buffer di testo che si trova alla base della visualizzazione di testo.

    - Oggetto <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, utilizzato per trovare testo.

    - Oggetto <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, che dispone di metodi per spostarsi all'interno di intervalli di testo.

    - Oggetto <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, che contiene l'insieme di parole da evidenziare.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, che corrisponde alla parola corrente.

    - Oggetto <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, che corrisponde alla posizione corrente del punti di inserimento.

    - Oggetto di blocco.

    ```csharp
    ITextView View { get; set; }
    ITextBuffer SourceBuffer { get; set; }
    ITextSearchService TextSearchService { get; set; }
    ITextStructureNavigator TextStructureNavigator { get; set; }
    NormalizedSnapshotSpanCollection WordSpans { get; set; }
    SnapshotSpan? CurrentWord { get; set; }
    SnapshotPoint RequestedPoint { get; set; }
    object updateLock = new object();

    ```

3. Aggiungere un costruttore che inizializza le <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> proprietà elencate in precedenza e aggiunge e gestori eventi.

    ```csharp
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,
    ITextStructureNavigator textStructureNavigator)
    {
        this.View = view;
        this.SourceBuffer = sourceBuffer;
        this.TextSearchService = textSearchService;
        this.TextStructureNavigator = textStructureNavigator;
        this.WordSpans = new NormalizedSnapshotSpanCollection();
        this.CurrentWord = null;
        this.View.Caret.PositionChanged += CaretPositionChanged;
        this.View.LayoutChanged += ViewLayoutChanged;
    }

    ```

4. I gestori eventi `UpdateAtCaretPosition` chiamano entrambi il metodo .

    ```csharp
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        // If a new snapshot wasn't generated, then skip this layout 
        if (e.NewSnapshot != e.OldSnapshot)
        {
            UpdateAtCaretPosition(View.Caret.Position);
        }
    }

    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)
    {
        UpdateAtCaretPosition(e.NewPosition);
    }
    ```

5. È inoltre necessario `TagsChanged` aggiungere un evento chiamato dal metodo update.

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6. Il `UpdateAtCaretPosition()` metodo trova ogni parola nel buffer di testo che è identica alla <xref:Microsoft.VisualStudio.Text.SnapshotSpan> parola in cui è posizionato il cursore e costruisce un elenco di oggetti che corrispondono alle occorrenze della parola. Chiama quindi `SynchronousUpdate`, che `TagsChanged` genera l'evento .

    ```csharp
    void UpdateAtCaretPosition(CaretPosition caretPosition)
    {
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);

        if (!point.HasValue)
            return;

        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it 
        if (CurrentWord.HasValue
            && CurrentWord.Value.Snapshot == View.TextSnapshot
            && point.Value >= CurrentWord.Value.Start
            && point.Value <= CurrentWord.Value.End)
        {
            return;
        }

        RequestedPoint = point.Value;
        UpdateWordAdornments();
    }

    void UpdateWordAdornments()
    {
        SnapshotPoint currentRequest = RequestedPoint;
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();
        //Find all words in the buffer like the one the caret is on
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);
        bool foundWord = true;
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit
        if (!WordExtentIsValid(currentRequest, word))
        {
            //Before we retry, make sure it is worthwhile 
            if (word.Span.Start != currentRequest
                 || currentRequest == currentRequest.GetContainingLine().Start
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))
            {
                foundWord = false;
            }
            else
            {
                // Try again, one character previous.  
                //If the caret is at the end of a word, pick up the word.
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);

                //If the word still isn't valid, we're done 
                if (!WordExtentIsValid(currentRequest, word))
                    foundWord = false;
            }
        }

        if (!foundWord)
        {
            //If we couldn't find a word, clear out the existing markers
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);
            return;
        }

        SnapshotSpan currentWord = word.Span;
        //If this is the current word, and the caret moved within a word, we're done. 
        if (CurrentWord.HasValue && currentWord == CurrentWord)
            return;

        //Find the new spans
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;

        wordSpans.AddRange(TextSearchService.FindAll(findData));

        //If another change hasn't happened, do a real update 
        if (currentRequest == RequestedPoint)
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);
    }
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)
    {
        return word.IsSignificant
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));
    }

    ```

7. `SynchronousUpdate` L'oggetto esegue un `WordSpans` `CurrentWord` aggiornamento sincrono `TagsChanged` sulle proprietà e e genera l'evento .

    ```csharp
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)
    {
        lock (updateLock)
        {
            if (currentRequest != RequestedPoint)
                return;

            WordSpans = newSpans;
            CurrentWord = newCurrentWord;

            var tempEvent = TagsChanged;
            if (tempEvent != null)
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));
        }
    }
    ```

8. È necessario <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> implementare il metodo. Questo metodo accetta <xref:Microsoft.VisualStudio.Text.SnapshotSpan> una raccolta di oggetti e restituisce un'enumerazione di intervalli di tag.

     In C'è, implementare questo metodo come un iteratore di rendimento, che consente la valutazione differita (vale a dire, la valutazione del set solo quando si accede a singoli elementi) dei tag. In Visual Basic aggiungere i tag a un elenco e restituire l'elenco.

     In questo caso <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> il metodo restituisce <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>un oggetto che ha un "blu", che fornisce uno sfondo blu.

    ```csharp
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)
    {
        if (CurrentWord == null)
            yield break;

        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same
        // collection throughout
        SnapshotSpan currentWord = CurrentWord.Value;
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;

        if (spans.Count == 0 || wordSpans.Count == 0)
            yield break;

        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot 
        if (spans[0].Snapshot != wordSpans[0].Snapshot)
        {
            wordSpans = new NormalizedSnapshotSpanCollection(
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));

            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);
        }

        // First, yield back the word the cursor is under (if it overlaps) 
        // Note that we'll yield back the same word again in the wordspans collection; 
        // the duplication here is expected. 
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());

        // Second, yield all the other words in the file 
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))
        {
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());
        }
    }
    ```

## <a name="create-a-tagger-provider"></a>Creare un provider TaggerCreate a Tagger provider
 Per creare il tagger, <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>è necessario implementare un file . Questa classe è una parte del componente MEF, pertanto è necessario impostare gli attributi corretti in modo che questa estensione venga riconosciuta.

> [!NOTE]
> Per ulteriori informazioni su MEF, vedere [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-create-a-tagger-provider"></a>Per creare un provider di tagger

1. Creare una `HighlightWordTaggerProvider` classe <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>denominata che implementa <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> ed esportarla <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> con <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>un di "text" e a of .

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. È necessario importare due <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> servizi <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>editor, e , per creare un'istanza del tagger.

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. Implementare <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> il metodo per `HighlightWordTagger`restituire un'istanza di .

    ```csharp
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag
    {
        //provide highlighting only on the top buffer 
        if (textView.TextBuffer != buffer)
            return null;

        ITextStructureNavigator textStructureNavigator =
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);

        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;
    }
    ```

## <a name="build-and-test-the-code"></a>Compilare e testare il codiceBuild and test the code
 Per testare questo codice, compilare la soluzione HighlightWordTest ed eseguirla nell'istanza sperimentale.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Per compilare e testare la soluzione HighlightWordTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo e digitare del testo in cui le parole vengono ripetute, ad esempio "ciao ciao".

4. Posizionare il cursore in una delle occorrenze di "ciao". Ogni occorrenza deve essere evidenziata in blu.

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di fileWalkthrough: Link a content type to a file name extension](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
