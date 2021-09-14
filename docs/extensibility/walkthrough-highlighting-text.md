---
title: 'Procedura dettagliata: Evidenziazione del testo | Microsoft Docs'
description: Informazioni su come evidenziare ogni occorrenza della parola corrente in un file di testo aggiungendo effetti visivi all'editor in questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0ccbc7dd098112706fb26d19a35e7d961fd89842
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710267"
---
# <a name="walkthrough-highlight-text"></a>Procedura dettagliata: Evidenziare il testo
È possibile aggiungere diversi effetti visivi all'editor creando Managed Extensibility Framework componenti mef (MeF). Questa procedura dettagliata illustra come evidenziare ogni occorrenza della parola corrente in un file di testo. Se una parola si trova più di una volta in un file di testo e si posiziona il cursore in un'occorrenza, ogni occorrenza viene evidenziata.

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>Creare un progetto MEF

1. Creare un progetto VSIX C#. Nella finestra **di dialogo Project** nuovo progetto selezionare Visual **C# /Extensibility**, quindi **VSIX Project**. Assegnare alla soluzione il nome `HighlightWordTest` .

2. Aggiungere un modello di elemento Editor Classifier al progetto. Per altre informazioni, vedere Creare [un'estensione con un modello di elemento dell'editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Eliminare i file di classe esistenti.

## <a name="define-a-textmarkertag"></a>Definire un TextMarkerTag
 Il primo passaggio per evidenziare il testo consiste nel sottoclassare <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> e definirne l'aspetto.

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Per definire textMarkerTag e MarkerFormatDefinition

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

4. Creare una classe che eredita da <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> e assegnare alla classe il nome `HighlightWordTag` .

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. Creare una seconda classe che eredita da e assegnare alla classe <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> il nome `HighlightWordFormatDefinition` . Per usare questa definizione di formato per il tag, è necessario esportarla con gli attributi seguenti:

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: i tag lo usano per fare riferimento a questo formato

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: in questo modo il formato viene visualizzato nell'interfaccia utente

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. Nel costruttore per HighlightWordFormatDefinition definire il nome visualizzato e l'aspetto. La proprietà Background definisce il colore di riempimento, mentre la proprietà Foreground definisce il colore del bordo.

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

## <a name="implement-an-itagger"></a>Implementare un ITagger
 Il passaggio successivo consiste nell'implementare <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> l'interfaccia . Questa interfaccia assegna, a un buffer di testo specificato, tag che forniscono l'evidenziazione del testo e altri effetti visivi.

### <a name="to-implement-a-tagger"></a>Per implementare un tagger

1. Creare una classe che implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> di tipo `HighlightWordTag` e assegnare alla classe il nome `HighlightWordTagger` .

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. Aggiungere i campi privati e le proprietà seguenti alla classe :

    - Oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> che corrisponde alla visualizzazione testo corrente.

    - Oggetto <xref:Microsoft.VisualStudio.Text.ITextBuffer> che corrisponde al buffer di testo alla base della visualizzazione testo.

    - Oggetto <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> utilizzato per trovare il testo.

    - Oggetto <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> che dispone di metodi per spostarsi all'interno di intervalli di testo.

    - Oggetto <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> che contiene il set di parole da evidenziare.

    - Oggetto <xref:Microsoft.VisualStudio.Text.SnapshotSpan> che corrisponde alla parola corrente.

    - Oggetto <xref:Microsoft.VisualStudio.Text.SnapshotPoint> che corrisponde alla posizione corrente del cursore.

    - Oggetto di blocco.

    ```csharp
    ITextView View { get; set; }
    ITextBuffer SourceBuffer { get; set; }
    ITextSearchService TextSearchService { get; set; }
    ITextStructureNavigator TextStructureNavigator { get; set; }
    NormalizedSnapshotSpanCollection WordSpans { get; set; }
    SnapshotSpan? CurrentWord { get; set; }
    SnapshotPoint RequestedPoint { get; set; }
    object updateLock = new object();

    ```

3. Aggiungere un costruttore che inizializza le proprietà elencate in precedenza e aggiunge <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> i gestori eventi e <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> .

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

4. I gestori eventi chiamano entrambi il `UpdateAtCaretPosition` metodo .

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

5. È inoltre necessario aggiungere `TagsChanged` un evento chiamato dal metodo update.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkhighlightwordtest/cs/highlightwordtag.cs" id="Snippet10":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhighlightwordtest/vb/highlightwordtag.vb" id="Snippet10":::


6. Il metodo trova ogni parola nel buffer di testo identica alla parola in cui è posizionato il cursore e costruisce un elenco di oggetti che corrispondono alle `UpdateAtCaretPosition()` <xref:Microsoft.VisualStudio.Text.SnapshotSpan> occorrenze della parola. Chiama quindi `SynchronousUpdate` , che genera l'evento `TagsChanged` .

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
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit
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
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)
    {
        return word.IsSignificant
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));
    }

    ```

7. esegue `SynchronousUpdate` un aggiornamento sincrono delle proprietà e e `WordSpans` genera `CurrentWord` `TagsChanged` l'evento .

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

8. È necessario implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodo . Questo metodo accetta una raccolta di <xref:Microsoft.VisualStudio.Text.SnapshotSpan> oggetti e restituisce un'enumerazione di intervalli di tag.

     In C# implementare questo metodo come iteratore yield, che consente la valutazione differita (ovvero la valutazione del set solo quando si accede a singoli elementi) dei tag. In Visual Basic aggiungere i tag a un elenco e restituire l'elenco.

     In questo caso il metodo restituisce <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> un oggetto con un oggetto "blu" che fornisce uno sfondo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> blu.

    ```csharp
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)
    {
        if (CurrentWord == null)
            yield break;

        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same
        // collection throughout
        SnapshotSpan currentWord = CurrentWord.Value;
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;

        if (spans.Count == 0 || wordSpans.Count == 0)
            yield break;

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
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());

        // Second, yield all the other words in the file 
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))
        {
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());
        }
    }
    ```

## <a name="create-a-tagger-provider"></a>Creare un provider di tagger
 Per creare il tagger, è necessario implementare <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> . Questa classe è una parte del componente MEF, pertanto è necessario impostare gli attributi corretti in modo che questa estensione sia riconosciuta.

> [!NOTE]
> Per altre informazioni su MEF, vedere [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-create-a-tagger-provider"></a>Per creare un provider di tagger

1. Creare una classe `HighlightWordTaggerProvider` denominata che implementa ed <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> esportarla con un oggetto di tipo <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" e <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> un oggetto di <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. È necessario importare due servizi editor, e <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> , per <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> creare un'istanza del tagger.

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. Implementare <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> il metodo per restituire un'istanza di `HighlightWordTagger` .

    ```csharp
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag
    {
        //provide highlighting only on the top buffer 
        if (textView.TextBuffer != buffer)
            return null;

        ITextStructureNavigator textStructureNavigator =
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);

        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;
    }
    ```

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione HighlightWordTest ed eseguirla nell'istanza sperimentale.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Per compilare e testare la soluzione HighlightWordTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda Visual Studio di .

3. Creare un file di testo e digitare un testo in cui le parole vengono ripetute, ad esempio "hello hello hello".

4. Posizionare il cursore in una delle occorrenze di "hello". Ogni occorrenza deve essere evidenziata in blu.

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
