---
title: "Procedura dettagliata: uso di un comando della shell con un'estensione dell'editor | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e9f7de69cfd969db8ae905ea65bbf868cf2c88a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904455"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>Procedura dettagliata: usare un comando della shell con un'estensione dell'editor
Da un VSPackage, è possibile aggiungere funzionalità come i comandi di menu all'editor. In questa procedura dettagliata viene illustrato come aggiungere un'area di controllo a una visualizzazione di testo nell'editor richiamando un comando di menu.

 Questa procedura dettagliata illustra l'uso di un pacchetto VSPackage insieme a una parte del componente Managed Extensibility Framework (MEF). È necessario usare un pacchetto VSPackage per registrare il comando di menu con la shell di Visual Studio. È possibile utilizzare il comando per accedere alla parte del componente MEF.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Creare un'estensione con un comando di menu
 Creare un pacchetto VSPackage che inserisce un comando di menu denominato **Aggiungi** area di controllo dal menu **strumenti** .

1. Creare un progetto VSIX C# denominato `MenuCommandTest` e aggiungere un nome del modello di elemento di comando personalizzato **AddAdornment**. Per altre informazioni, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Viene aperta una soluzione denominata MenuCommandTest. Il file MenuCommandTestPackage contiene il codice che crea il comando di menu e lo inserisce nel menu **strumenti** . A questo punto, il comando causa solo la visualizzazione di una finestra di messaggio. Nei passaggi successivi verrà illustrato come modificare questa operazione per visualizzare l'area di visualizzazione dei commenti.

3. Aprire il file *source. Extension. vsixmanifest* nell'editor del manifesto VSIX. La `Assets` scheda deve contenere una riga per Microsoft. VisualStudio. VSPackage denominata MenuCommandTest.

4. Salvare e chiudere il file *source. Extension. vsixmanifest* .

## <a name="add-a-mef-extension-to-the-command-extension"></a>Aggiungere un'estensione MEF all'estensione del comando

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo soluzione, scegliere **Aggiungi**, quindi fare clic su **nuovo progetto**. Nella finestra di dialogo **Aggiungi nuovo progetto** fare clic su **estendibilità** in **Visual C#**, quindi **progetto VSIX**. Assegnare al progetto il nome `CommentAdornmentTest`.

2. Poiché questo progetto interagirà con l'assembly VSPackage con nome sicuro, sarà necessario firmare l'assembly. È possibile riutilizzare il file di chiave già creato per l'assembly VSPackage.

    1. Aprire le proprietà del progetto e selezionare la scheda **firma** .

    2. Selezionare **Firma assembly**.

    3. In **scegliere un file di chiave con nome sicuro**selezionare il file *Key. snk* generato per l'assembly MenuCommandTest.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>Vedere l'estensione MEF nel progetto VSPackage
 Poiché si sta aggiungendo un componente MEF al pacchetto VSPackage, è necessario specificare entrambi i tipi di asset nel manifesto.

> [!NOTE]
> Per ulteriori informazioni su MEF, vedere [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Per fare riferimento al componente MEF nel progetto VSPackage

1. Nel progetto MenuCommandTest aprire il file *source. Extension. vsixmanifest* nell'editor del manifesto VSIX.

2. Nella scheda **Asset** fare clic su **nuovo**.

3. Nell'elenco **tipo** scegliere **Microsoft. VisualStudio. MefComponent**.

4. Nell'elenco **origine** scegliere **un progetto nella soluzione corrente**.

5. Nell'elenco **progetto** scegliere **CommentAdornmentTest**.

6. Salvare e chiudere il file *source. Extension. vsixmanifest* .

7. Verificare che il progetto MenuCommandTest includa un riferimento al progetto CommentAdornmentTest.

8. Nel progetto CommentAdornmentTest impostare il progetto in modo da produrre un assembly. Nella **Esplora soluzioni**selezionare il progetto e cercare nella proprietà **Copia output di compilazione in OutputDirectory** nella finestra **Proprietà** e impostarla su **true**.

## <a name="define-a-comment-adornment"></a>Definire un'area di osservazione del commento
 L'adorning dei commenti è costituito da un oggetto <xref:Microsoft.VisualStudio.Text.ITrackingSpan> che tiene traccia del testo selezionato e da alcune stringhe che rappresentano l'autore e la descrizione del testo.

#### <a name="to-define-a-comment-adornment"></a>Per definire un'area di osservazione del commento

1. Nel progetto CommentAdornmentTest aggiungere un nuovo file di classe e denominarlo `CommentAdornment` .

2. Aggiungere i riferimenti seguenti:

    1. Microsoft. VisualStudio. CoreUtility

    2. Microsoft. VisualStudio. Text. Data

    3. Microsoft. VisualStudio. Text. Logic

    4. Microsoft. VisualStudio. Text. UI

    5. Microsoft. VisualStudio. Text. UI. WPF

    6. System.ComponentModel.Composition

    7. PresentationCore

    8. PresentationFramework

    9. WindowsBase

3. Aggiungere la `using` direttiva seguente.

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. Il file deve contenere una classe denominata `CommentAdornment` .

    ```csharp
    internal class CommentAdornment
    ```

5. Aggiungere tre campi alla `CommentAdornment` classe per <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , l'autore e la descrizione.

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6. Aggiungere un costruttore che Inizializza i campi.

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>Creare un elemento visivo per l'area di visualizzazione
 Definire un elemento visivo per l'area di lavoro. Per questa procedura dettagliata, definire un controllo che erediti dalla classe Windows Presentation Foundation (WPF) <xref:System.Windows.Controls.Canvas> .

1. Creare una classe nel progetto CommentAdornmentTest e denominarla `CommentBlock` .

2. Aggiungere le `using` direttive seguenti.

    ```csharp
    using Microsoft.VisualStudio.Text;
    using System;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Media;
    using System.Windows.Shapes;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Fare in modo che la `CommentBlock` classe erediti da <xref:System.Windows.Controls.Canvas> .

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. Aggiungere alcuni campi privati per definire gli aspetti visivi dell'area di visualizzazione.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. Aggiungere un costruttore che definisce l'area di interesse del commento e aggiunge il testo pertinente.

    ```csharp
    public CommentBlock(double textRightEdge, double viewRightEdge,
            Geometry newTextGeometry, string author, string body)
    {
        if (brush == null)
        {
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));
            brush.Freeze();
            Brush penBrush = new SolidColorBrush(Colors.Green);
            penBrush.Freeze();
            solidPen = new Pen(penBrush, 0.5);
            solidPen.Freeze();
            dashPen = new Pen(penBrush, 0.5);
            dashPen.DashStyle = DashStyles.Dash;
            dashPen.Freeze();
        }

        this.textGeometry = newTextGeometry;

        TextBlock tb1 = new TextBlock();
        tb1.Text = author;
        TextBlock tb2 = new TextBlock();
        tb2.Text = body;

        const int MarginWidth = 8;
        this.commentGrid = new Grid();
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        ColumnDefinition cEdge = new ColumnDefinition();
        cEdge.Width = new GridLength(MarginWidth);
        ColumnDefinition cEdge2 = new ColumnDefinition();
        cEdge2.Width = new GridLength(MarginWidth);
        this.commentGrid.ColumnDefinitions.Add(cEdge);
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());
        this.commentGrid.ColumnDefinitions.Add(cEdge2);

        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();
        rect.RadiusX = 6;
        rect.RadiusY = 3;
        rect.Fill = brush;
        rect.Stroke = Brushes.Green;

            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);
            tb1.Measure(inf);
            tb2.Measure(inf);
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;

        Grid.SetColumn(rect, 0);
        Grid.SetRow(rect, 0);
        Grid.SetRowSpan(rect, 2);
        Grid.SetColumnSpan(rect, 3);
        Grid.SetRow(tb1, 0);
        Grid.SetColumn(tb1, 1);
        Grid.SetRow(tb2, 1);
        Grid.SetColumn(tb2, 1);
        this.commentGrid.Children.Add(rect);
        this.commentGrid.Children.Add(tb1);
        this.commentGrid.Children.Add(tb2);

        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));
        Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);

        this.Children.Add(this.commentGrid);
    }
    ```

6. Implementare anche un <xref:System.Windows.Controls.Panel.OnRender%2A> gestore eventi che disegna l'area di disegno.

    ```csharp
    protected override void OnRender(DrawingContext dc)
    {
        base.OnRender(dc);
        if (this.textGeometry != null)
        {
            dc.DrawGeometry(brush, solidPen, this.textGeometry);
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);
            dc.DrawLine(dashPen, p1, p2);
            dc.DrawLine(dashPen, p2, p3);
        }
    }
    ```

## <a name="add-an-iwpftextviewcreationlistener"></a>Aggiungere un IWpfTextViewCreationListener
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>È una parte del componente MEF che è possibile usare per ascoltare la visualizzazione degli eventi di creazione.

1. Aggiungere un file di classe al progetto CommentAdornmentTest e denominarlo `Connector` .

2. Aggiungere le `using` direttive seguenti.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Dichiarare una classe che implementa <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> ed esportarla con un valore <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "Text" e <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> di <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> . L'attributo Content Type specifica il tipo di contenuto a cui si applica il componente. Il tipo di testo è il tipo base per tutti i tipi di file non binari. Pertanto, quasi tutte le visualizzazioni di testo create saranno di questo tipo. L'attributo del ruolo Visualizzazione testo specifica il tipo di visualizzazione di testo a cui si applica il componente. Nei ruoli della visualizzazione di testo del documento viene in genere visualizzato testo composto da righe e archiviato in un file.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. Implementare il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodo in modo che chiami l' `Create()` evento statico di `CommentAdornmentManager` .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. Aggiungere un metodo che è possibile usare per eseguire il comando.

    ```csharp
    static public void Execute(IWpfTextViewHost host)
    {
        IWpfTextView view = host.TextView;
        //Add a comment on the selected text. 
        if (!view.Selection.IsEmpty)
        {
            //Get the provider for the comment adornments in the property bag of the view.
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));

            //Add some arbitrary author and comment text. 
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;
            string comment = "Four score....";

            //Add the comment adornment using the provider.
            provider.Add(view.Selection.SelectedSpans[0], author, comment);
        }
    }
    ```

## <a name="define-an-adornment-layer"></a>Definire un livello di area di strumenti
 Per aggiungere una nuova area di strumenti, è necessario definire un livello di area di strumenti.

### <a name="to-define-an-adornment-layer"></a>Per definire un livello di area di strumenti

1. Nella `Connector` classe dichiarare un campo pubblico di tipo <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> ed esportarlo con un oggetto <xref:Microsoft.VisualStudio.Utilities.NameAttribute> che specifica un nome univoco per il livello di area di visualizzazione e un oggetto <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> che definisce la relazione dell'ordine Z di questo livello di area di visualizzazione agli altri livelli di visualizzazione di testo (testo, punto di inserimento e selezione).

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>Fornire le aree di osservazione del commento
 Quando si definisce un'area di utilizzo, implementare anche un provider di aree di osservazione e un gestore dell'area di gestione del commento. Il provider dell'area di visualizzazione dei commenti mantiene un elenco di aree di visualizzazione dei commenti, resta in attesa <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> degli eventi nel buffer di testo sottostante ed Elimina le aree di visualizzazione dei commenti quando il testo sottostante viene eliminato.

1. Aggiungere un nuovo file di classe al progetto CommentAdornmentTest e denominarlo `CommentAdornmentProvider` .

2. Aggiungere le `using` direttive seguenti.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    ```

3. Aggiungere una classe denominata `CommentAdornmentProvider`.

    ```csharp
    internal class CommentAdornmentProvider
    {
    }
    ```

4. Aggiungere campi privati per il buffer di testo e l'elenco di aree di visualizzazione dei commenti correlati al buffer.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. Aggiungere un costruttore per `CommentAdornmentProvider` . Questo costruttore deve avere accesso privato perché il metodo crea un'istanza del provider `Create()` . Il costruttore aggiunge il `OnBufferChanged` gestore eventi all' <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.

    ```csharp
    private CommentAdornmentProvider(ITextBuffer buffer)
    {
        this.buffer = buffer;
        //listen to the Changed event so we can react to deletions. 
        this.buffer.Changed += OnBufferChanged;
    }

    ```

6. Aggiungere il metodo `Create()`.

    ```csharp
    public static CommentAdornmentProvider Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });
    }

    ```

7. Aggiungere il metodo `Detach()`.

    ```csharp
    public void Detach()
    {
        if (this.buffer != null)
        {
            //remove the Changed listener 
            this.buffer.Changed -= OnBufferChanged;
            this.buffer = null;
        }
    }
    ```

8. Aggiungere il `OnBufferChanged` gestore eventi.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. Aggiungere una dichiarazione per un `CommentsChanged` evento.

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. Creare un `Add()` metodo per aggiungere l'area di strumenti.

    ```csharp
    public void Add(SnapshotSpan span, string author, string text)
    {
        if (span.Length == 0)
            throw new ArgumentOutOfRangeException("span");
        if (author == null)
            throw new ArgumentNullException("author");
        if (text == null)
            throw new ArgumentNullException("text");

        //Create a comment adornment given the span, author and text.
        CommentAdornment comment = new CommentAdornment(span, author, text);

        //Add it to the list of comments. 
        this.comments.Add(comment);

        //Raise the changed event.
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;
        if (commentsChanged != null)
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));
    }

    ```

11. Aggiungere un `RemoveComments()` metodo.

    ```csharp
    public void RemoveComments(SnapshotSpan span)
    {
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;

        //Get a list of all the comments that are being kept
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);

        foreach (CommentAdornment comment in this.comments)
        {
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith. 
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
            {
                //Raise the change event to delete this comment. 
                if (commentsChanged != null)
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));
            }
            else
                keptComments.Add(comment);
        }

        this.comments = keptComments;
    }
    ```

12. Aggiungere un `GetComments()` metodo che restituisca tutti i commenti in un intervallo di snapshot specificato.

    ```csharp
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)
    {
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();
        foreach (CommentAdornment comment in this.comments)
        {
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
                overlappingComments.Add(comment);
        }

        return new Collection<CommentAdornment>(overlappingComments);
    }
    ```

13. Aggiungere una classe denominata `CommentsChangedEventArgs` , come indicato di seguito.

    ```csharp
    internal class CommentsChangedEventArgs : EventArgs
    {
        public readonly CommentAdornment CommentAdded;

        public readonly CommentAdornment CommentRemoved;

        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)
        {
            this.CommentAdded = added;
            this.CommentRemoved = removed;
        }
    }
    ```

## <a name="manage-comment-adornments"></a>Gestisci aree di osservazione Commenti
 Il gestore dell'area di gestione dei commenti crea l'area di modifica e la aggiunge al livello dell'area di strumenti. Ascolta gli <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> eventi e per <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> poter spostare o eliminare l'area di modifica. Ascolta anche l' `CommentsChanged` evento che viene generato dal provider di adorning dei commenti quando vengono aggiunti o rimossi commenti.

1. Aggiungere un file di classe al progetto CommentAdornmentTest e denominarlo `CommentAdornmentManager` .

2. Aggiungere le `using` direttive seguenti.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Windows.Media;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Formatting;
    ```

3. Aggiungere una classe denominata `CommentAdornmentManager`.

    ```csharp
    internal class CommentAdornmentManager
        {
        }
    ```

4. Aggiungere alcuni campi privati.

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. Aggiungere un costruttore che sottoscrive il gestore agli <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> eventi e e anche all' `CommentsChanged` evento. Il costruttore è privato perché viene creata un'istanza del gestore tramite il `Create()` metodo statico.

    ```csharp
    private CommentAdornmentManager(IWpfTextView view)
    {
        this.view = view;
        this.view.LayoutChanged += OnLayoutChanged;
        this.view.Closed += OnClosed;

        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");

        this.provider = CommentAdornmentProvider.Create(view);
        this.provider.CommentsChanged += OnCommentsChanged;
    }
    ```

6. Aggiungere il `Create()` metodo che ottiene un provider o ne crea uno se necessario.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. Aggiungere il `CommentsChanged` gestore.

    ```csharp
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)
    {
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag). 
        if (e.CommentRemoved != null)
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);

        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout). 
        if (e.CommentAdded != null)
            this.DrawComment(e.CommentAdded);
    }
    ```

8. Aggiungere il <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> gestore.

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. Aggiungere il <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> gestore.

    ```csharp
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        //Get all of the comments that intersect any of the new or reformatted lines of text.
        List<CommentAdornment> newComments = new List<CommentAdornment>();

        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.  
        //Use the latter to find the comments that intersect the new or reformatted lines of text. 
        foreach (Span span in e.NewOrReformattedSpans)
        {
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));
        }

        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not. 
        //Sort the list and skip duplicates.
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });

        CommentAdornment lastComment = null;
        foreach (CommentAdornment comment in newComments)
        {
            if (comment != lastComment)
            {
                lastComment = comment;
                this.DrawComment(comment);
            }
        }
    }
    ```

10. Aggiungere il metodo privato che disegna il commento.

     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Usare il comando di menu per aggiungere l'area di controllo del commento
 È possibile usare il comando di menu per creare un'area di controllo dei commenti implementando il `MenuItemCallback` metodo del pacchetto VSPackage.

1. Aggiungere i riferimenti seguenti al progetto MenuCommandTest:

    - Microsoft. VisualStudio. TextManager. Interop

    - Microsoft. VisualStudio. Editor

    - Microsoft. VisualStudio. Text. UI. WPF

2. Aprire il file *AddAdornment.cs* e aggiungere le `using` direttive seguenti.

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. Eliminare il `Execute()` metodo e aggiungere il gestore di comandi seguente.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. Aggiungere il codice per ottenere la visualizzazione attiva. È necessario ottenere la `SVsTextManager` della shell di Visual Studio per ottenere l'oggetto attivo `IVsTextView` .

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. Se questa visualizzazione di testo è un'istanza di una visualizzazione di testo dell'editor, è possibile eseguirne il cast all' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> interfaccia e quindi ottenere l'oggetto <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> e il relativo oggetto associato <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> . Usare <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> per chiamare il `Connector.Execute()` metodo, che ottiene il provider dell'area di visualizzazione dei commenti e aggiunge l'area di visualizzazione. Il gestore di comandi dovrebbe ora essere simile a questo codice:

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
        IVsUserData userData = vTextView as IVsUserData;
         if (userData == null)
        {
            Console.WriteLine("No text view is currently open");
            return;
        }
        IWpfTextViewHost viewHost;
        object holder;
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;
        userData.GetData(ref guidViewHost, out holder);
        viewHost = (IWpfTextViewHost)holder;
        Connector.Execute(viewHost);
    }
    ```

6. Impostare il metodo AddAdornmentHandler come gestore per il comando AddAdornment nel costruttore AddAdornment.

    ```csharp
    private AddAdornment(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new MenuCommand(this.AddAdornmentHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

## <a name="build-and-test-the-code"></a>Compilare e testare il codice

1. Compilare la soluzione e avviare il debug. Verrà visualizzata l'istanza sperimentale.

2. Creare un file di testo. Digitare il testo e selezionarlo.

3. Scegliere **richiama Aggiungi**area di strumenti dal menu **strumenti** . Un fumetto dovrebbe essere visualizzato sul lato destro della finestra di testo e deve contenere testo simile al testo seguente.

     Nomeutente

     Ottanta...

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
