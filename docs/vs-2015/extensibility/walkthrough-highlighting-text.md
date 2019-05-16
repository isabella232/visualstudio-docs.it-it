---
title: 'Procedura dettagliata: Evidenziazione del testo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
caps.latest.revision: 43
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d398164e910f7700645c01d26afbc631b1d434bc
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65693331"
---
# <a name="walkthrough-highlighting-text"></a>Procedura dettagliata: Evidenziazione del testo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile aggiungere effetti visivi diversi per l'editor creando parti componente Managed Extensibility Framework (MEF). Questa procedura dettagliata viene illustrato come evidenziare tutte le occorrenze della parola corrente in un file di testo. Se una parola si verifica più volte in un file di testo e si posiziona il punto di inserimento in una sola occorrenza, viene evidenziato ogni occorrenza.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
1. Creare un progetto c# VSIX. (Nelle **nuovo progetto** finestra di dialogo, seleziona **Visual c# / Extensibility**, quindi **progetto VSIX**.) Assegnare alla soluzione il nome `HighlightWordTest`.  
  
2. Aggiungere un modello di elemento di classificatore Editor al progetto. Per altre informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Eliminare i file di classe esistenti.  
  
## <a name="defining-a-textmarkertag"></a>La definizione di un TextMarkerTag  
 Il primo passaggio nell'evidenziazione del testo è per creare una sottoclasse <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> e definire l'aspetto del controllo.  
  
#### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Per definire un TextMarkerTag e un MarkerFormatDefinition  
  
1. Aggiungere un file di classe e denominarla **HighlightWordTag**.  
  
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
  
4. Creare una classe che eredita da <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> e denominarlo `HighlightWordTag`.  
  
    ```csharp  
    internal class HighlightWordTag : TextMarkerTag  
    {  
  
    }  
    ```  
  
5. Creare una seconda classe che eredita da <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>e denominarla HighlightWordFormatDefinition. Per usare questa definizione di formato per il tag, è necessario esportarlo con gli attributi seguenti:  
  
    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: i tag di utilizzare questa opzione per fare riferimento a questo formato  
  
    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: in questo modo, il formato da visualizzare nell'interfaccia utente  
  
    ```csharp  
  
    [Export(typeof(EditorFormatDefinition))]  
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
    [UserVisible(true)]  
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
    {  
  
    }  
    ```  
  
6. Nel costruttore per HighlightWordFormatDefinition, definire il nome visualizzato e l'aspetto. La proprietà Background definisce il colore di riempimento, mentre la proprietà Foreground definisce il colore del bordo.  
  
    ```csharp  
    public HighlightWordFormatDefinition()  
    {  
                this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";  
        this.ZOrder = 5;  
    }  
    ```  
  
7. Nel costruttore per HighlightWordTag, passare il nome di definizione del formato che appena creato.  
  
    ```  
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }  
    ```  
  
## <a name="implementing-an-itagger"></a>Implementazione di un ITagger  
 Il passaggio successivo consiste nell'implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> interfaccia. Questa interfaccia viene assegnato a un buffer di testo specificato, i tag che forniscono l'evidenziazione del testo e altri effetti visivi.  
  
#### <a name="to-implement-a-tagger"></a>Per implementare un tagger  
  
1. Creare una classe che implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu `HighlightWordTag`e denominarla `HighlightWordTagger`.  
  
    ```csharp  
    internal class HighlightWordTagger : ITagger<HighlightWordTag>  
    {  
  
    }  
    ```  
  
2. Aggiungere le proprietà e campi privati seguenti alla classe:  
  
    - Un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, che corrisponde alla visualizzazione di testo corrente.  
  
    - Un <xref:Microsoft.VisualStudio.Text.ITextBuffer>, che corrisponde al buffer di testo sottostante alla visualizzazione di testo.  
  
    - Un <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, che viene usato per trovare testo.  
  
    - Un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, che dispone di metodi per spostarsi all'interno di intervalli di testo.  
  
    - Oggetto <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, che contiene il set di parole da evidenziare.  
  
    - Oggetto <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, che corrisponde alla parola corrente.  
  
    - Oggetto <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, che corrisponde alla posizione corrente del punto di inserimento.  
  
    - Un oggetto di blocco.  
  
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
  
3. Aggiungere un costruttore che inizializza le proprietà elencate in precedenza e aggiunge <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> e <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> gestori eventi.  
  
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
  
4. I gestori di eventi entrambi chiamano il `UpdateAtCaretPosition` (metodo).  
  
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
  
5. È inoltre necessario aggiungere un `TagsChanged` evento che verrà chiamato dal metodo update.  
  
     [!code-csharp[VSSDKHighlightWordTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkhighlightwordtest/cs/highlightwordtag.cs#10)]
     [!code-vb[VSSDKHighlightWordTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhighlightwordtest/vb/highlightwordtag.vb#10)]  
  
6. Il `UpdateAtCaretPosition()` metodo trova tutte le parole nel buffer di testo che è identico a word in cui il cursore è posizionato e crea un elenco di <xref:Microsoft.VisualStudio.Text.SnapshotSpan> oggetti che corrispondono alle occorrenze della parola. Chiama poi `SynchronousUpdate`, che genera il `TagsChanged` evento.  
  
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
  
7. Il `SynchronousUpdate` esegue un aggiornamento sincrono sul `WordSpans` e `CurrentWord` delle proprietà e genera il `TagsChanged` evento.  
  
    ```vb  
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
  
8. È necessario implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> (metodo). Questo metodo accetta una raccolta di <xref:Microsoft.VisualStudio.Text.SnapshotSpan> degli oggetti e restituisce un'enumerazione di intervalli di tag.  
  
     In c#, è possibile implementare questo metodo come iteratore yield, che consente la valutazione lazy (vale a dire, valutazione del set di solo quando si accede a singoli elementi) dei tag. In Visual Basic, aggiungere i tag per un elenco e restituisce l'elenco.  
  
     In questo caso il metodo restituisce un <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> oggetto che ha un "blue" <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, che forniscono uno sfondo blu.  
  
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
  
## <a name="creating-a-tagger-provider"></a>Creazione di un Provider di Tagger  
 Per creare il tagger, è necessario implementare un <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Questa classe è una parte del componente MEF, pertanto è necessario impostare gli attributi corretti in modo che questa estensione viene riconosciuta.  
  
> [!NOTE]
> Per altre informazioni su MEF, vedere [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
#### <a name="to-create-a-tagger-provider"></a>Per creare un provider di tagger  
  
1. Creare una classe denominata `HighlightWordTaggerProvider` che implementa <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> impostato su "text" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
    ```csharp  
    [Export(typeof(IViewTaggerProvider))]  
    [ContentType("text")]  
    [TagType(typeof(TextMarkerTag))]  
    internal class HighlightWordTaggerProvider : IViewTaggerProvider  
    { }  
    ```  
  
2. È necessario importare due servizi dell'editor, il <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> e il <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, per creare un'istanza il tagger.  
  
    ```csharp  
    [Import]  
    internal ITextSearchService TextSearchService { get; set; }  
  
    [Import]  
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }  
  
    ```  
  
3. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> per restituire un'istanza di `HighlightWordTagger`.  
  
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
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione HighlightWordTest ed eseguirlo nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Per compilare e testare la soluzione HighlightWordTest  
  
1. Compilare la soluzione.  
  
2. Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3. Creare un file di testo e digitare un testo in cui le parole vengono ripetute, ad esempio, "hello hello hello".  
  
4. Posizionare il cursore in una delle occorrenze di "hello". Ogni occorrenza deve essere evidenziato in blu.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: collegamento di un tipo di contenuto a un'estensione](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
