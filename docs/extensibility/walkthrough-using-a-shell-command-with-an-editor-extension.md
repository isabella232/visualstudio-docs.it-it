---
title: "Procedura dettagliata: Utilizzo di un comando della Shell con un'estensione dell'Editor | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a7e0b86bc5058195733c49f5d804a38a5421737
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685157"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>Procedura dettagliata: Usare un comando della shell con un'estensione dell'editor
Da un pacchetto VSPackage, è possibile aggiungere le funzionalità, ad esempio i comandi di menu per l'editor. Questa procedura dettagliata illustra come aggiungere un'area di controllo a una visualizzazione di testo nell'editor quando si richiama un comando di menu.

 Questa procedura dettagliata illustra l'uso di un pacchetto VSPackage insieme a una parte di componente Managed Extensibility Framework (MEF). Per registrare il comando di menu con la shell di Visual Studio, è necessario usare un pacchetto VSPackage. E, è possibile usare il comando per accedere alla parte del componente MEF.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, Visual Studio SDK è non installare dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Creare un'estensione con un comando di menu
 Creare un pacchetto VSPackage che inserisce un comando di menu denominato **Aggiungi area di controllo** nel **Tools** menu.

1.  Creare un progetto VSIX c# denominato `MenuCommandTest`e aggiungere un nome di modello di elemento di comando personalizzati **AddAdornment**. Per altre informazioni, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2.  Si apre una soluzione denominata MenuCommandTest. Il file MenuCommandTestPackage ha il codice che crea il comando di menu e lo aggiunge il **strumenti** menu. A questo punto, il comando verifica semplicemente una finestra di messaggio da visualizzare. Passaggi successivi mostrerà come modificare questa opzione per visualizzare l'area di controllo di commento.

3.  Aprire il *vsixmanifest* file nell'Editor Manifest VSIX. Il `Assets` scheda deve essere presente una riga per una Microsoft.VisualStudio.VsPackage denominato MenuCommandTest.

4.  Salvare e chiudere il *vsixmanifest* file.

## <a name="add-a-mef-extension-to-the-command-extension"></a>Aggiungere un'estensione MEF all'estensione di comando

1.  Nella **Esplora soluzioni**, fare doppio clic sul nodo della soluzione, fare clic su **Add**, quindi fare clic su **nuovo progetto**. Nel **Aggiungi nuovo progetto** finestra di dialogo, fare clic su **Extensibility** sotto **Visual c#**, quindi **progetto VSIX**. Denominare il progetto `CommentAdornmentTest`.

2.  Poiché questo progetto interagirà con il pacchetto VSPackage assembly con nome sicuro, è necessario firmare l'assembly. È possibile riutilizzare il file di chiave già creato per l'assembly VSPackage.

    1.  Aprire le proprietà del progetto e selezionare il **firma** scheda.

    2.  Selezionare **firmare l'assembly**.

    3.  Sotto **Scegli un file chiave con nome sicuro**, selezionare la *snk* file generato per l'assembly MenuCommandTest.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>Fare riferimento all'estensione MEF nel progetto VSPackage
 Poiché si sta aggiungendo un componente MEF per il pacchetto VSPackage, è necessario specificare entrambi i tipi di asset nel manifesto.

> [!NOTE]
>  Per altre informazioni su MEF, vedere [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Per fare riferimento al componente MEF in progetto VSPackage

1.  Nel progetto MenuCommandTest, aprire il *vsixmanifest* file nell'Editor Manifest VSIX.

2.  Nel **Assets** scheda, fare clic su **New**.

3.  Nel **tipo** casella di riepilogo **MEFComponent**.

4.  Nel **origine** casella di riepilogo **un progetto nella soluzione corrente**.

5.  Nel **Project** casella di riepilogo **CommentAdornmentTest**.

6.  Salvare e chiudere il *vsixmanifest* file.

7.  Assicurarsi che il progetto MenuCommandTest contiene un riferimento al progetto CommentAdornmentTest.

8.  Nel progetto CommentAdornmentTest, impostare il progetto per produrre un assembly. Nel **Esplora soluzioni**, selezionare il progetto ed esaminare le **proprietà** finestra per il **copia Output di compilazione per OutputDirectory** proprietà e impostarlo su **true**.

## <a name="define-a-comment-adornment"></a>Definire un'area di controllo di commento
 L'area di controllo di commento stesso è costituito da un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> che tiene traccia del testo selezionato e alcune stringhe che rappresentano l'autore e la descrizione del testo.

#### <a name="to-define-a-comment-adornment"></a>Per definire un'area di controllo di commento

1.  Nel progetto CommentAdornmentTest, aggiungere un nuovo file di classe e denominarla `CommentAdornment`.

2.  Aggiungere i riferimenti seguenti:

    1.  Microsoft.VisualStudio.CoreUtility

    2.  Microsoft.VisualStudio.Text.Data

    3.  Microsoft.VisualStudio.Text.Logic

    4.  Microsoft.VisualStudio.Text.UI

    5.  Microsoft.VisualStudio.Text.UI.Wpf

    6.  System.ComponentModel.Composition

    7.  PresentationCore

    8.  PresentationFramework

    9. WindowsBase

3.  Aggiungere il codice seguente `using` istruzione.

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4.  Il file deve contenere una classe denominata `CommentAdornment`.

    ```csharp
    internal class CommentAdornment
    ```

5.  Aggiungere tre campi per il `CommentAdornment` classe per il <xref:Microsoft.VisualStudio.Text.ITrackingSpan>, l'autore e la descrizione.

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6.  Aggiungere un costruttore che inizializza i campi.

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>Creare un elemento visivo per l'area di controllo
 Definire un elemento visivo per l'area di controllo. Per questa procedura dettagliata, definire un controllo che eredita dalla classe di Windows Presentation Foundation (WPF) <xref:System.Windows.Controls.Canvas>.

1.  Creare una classe nel progetto CommentAdornmentTest e denominarlo `CommentBlock`.

2.  Aggiungere le istruzioni `using` riportate di seguito.

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

3.  Verificare i `CommentBlock` classe ereditare da <xref:System.Windows.Controls.Canvas>.

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4.  Aggiungere alcuni campi privati per definire gli aspetti visivi dell'area di controllo.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5.  Aggiungere un costruttore che definisce l'area di controllo di commento e aggiunge il testo corrispondente.

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

6.  Implementare anche un <xref:System.Windows.Controls.Panel.OnRender%2A> gestore eventi che consente di disegnare l'area di controllo.

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
 Il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> è una parte del componente MEF che è possibile usare per l'ascolto per visualizzare gli eventi di creazione.

1.  Aggiungere un file di classe al progetto CommentAdornmentTest e denominarlo `Connector`.

2.  Aggiungere le istruzioni `using` riportate di seguito.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3.  Dichiarare una classe che implementa <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> impostato su "text" e un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> di <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>. L'attributo di tipo di contenuto specifica il tipo di contenuto a cui viene applicata al componente. Il tipo di testo è il tipo di base per tutti i tipi di file non binari. Pertanto, quasi tutte le visualizzazione di testo che viene creata sarà di questo tipo. L'attributo del ruolo visualizzazione testo specifica il tipo di visualizzazione di testo a cui viene applicata al componente. In genere ruoli della visualizzazione documento di testo mostrano il testo che è composto da righe e viene archiviato in un file.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4.  Implementare il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodo in modo che venga chiamato il metodo statico `Create()` eventi del `CommentAdornmentManager`.

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5.  Aggiungere un metodo che è possibile usare per eseguire il comando.

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

## <a name="define-an-adornment-layer"></a>Definire un livello di area di controllo
 Per aggiungere una nuova area di controllo, è necessario definire un livello di area di controllo.

### <a name="to-define-an-adornment-layer"></a>Per definire un livello di area di controllo

1.  Nel `Connector` classe, dichiarare un campo pubblico di tipo <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> che specifica un nome univoco per il livello di area di controllo e un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> che definisce la relazione nell'ordine Z di questo livello di area di controllo a altro testo visualizzare i livelli (testo, cursore e selezione).

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>Fornire le aree di controllo di commento
 Quando si definisce un'area di controllo, anche implementare un provider dell'area di controllo di commento e un gestore dell'area di controllo di commento. Il provider dell'area di controllo di commento mantiene un elenco di aree di controllo di commento, resta in attesa <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> gli eventi nel buffer di testo sottostante e le aree di controllo di eliminazioni commento quando viene eliminato il testo sottostante.

1.  Aggiungere un nuovo file di classe al progetto CommentAdornmentTest e denominarlo `CommentAdornmentProvider`.

2.  Aggiungere le istruzioni `using` riportate di seguito.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    ```

3.  Aggiungere una classe denominata `CommentAdornmentProvider`.

    ```csharp
    internal class CommentAdornmentProvider
    {
    }
    ```

4.  Aggiungere campi privati per il buffer di testo e l'elenco delle aree di controllo di commento relative al buffer.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5.  Aggiungere un costruttore per `CommentAdornmentProvider`. Questo costruttore deve avere accesso privato perché il provider viene creato mediante il `Create()` (metodo). Il costruttore aggiunge il `OnBufferChanged` gestore dell'evento per il <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.

    ```csharp
    private CommentAdornmentProvider(ITextBuffer buffer)
    {
        this.buffer = buffer;
        //listen to the Changed event so we can react to deletions. 
        this.buffer.Changed += OnBufferChanged;
    }

    ```

6.  Aggiungere il metodo `Create()`.

    ```csharp
    public static CommentAdornmentProvider Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });
    }

    ```

7.  Aggiungere il metodo `Detach()`.

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

8.  Aggiungere il `OnBufferChanged` gestore dell'evento.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. Aggiungere una dichiarazione per un `CommentsChanged` evento.

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. Creare un `Add()` metodo per aggiungere l'area di controllo.

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

11. Aggiungere un `RemoveComments()` (metodo).

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

12. Aggiungere un `GetComments()` metodo che restituisce tutti i commenti in un intervallo di snapshot specificato.

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

13. Aggiungere una classe denominata `CommentsChangedEventArgs`, come indicato di seguito.

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

## <a name="manage-comment-adornments"></a>Gestire le aree di controllo di commento
 Il gestore dell'area di controllo di commento crea l'area di controllo e lo aggiunge al livello di area di controllo. È in ascolto il <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> e <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> gli eventi in modo che sia possibile spostare o eliminare l'area di controllo. È inoltre in ascolto il `CommentsChanged` evento generato dal provider dell'area di controllo di commento quando i commenti vengono aggiunti o rimossi.

1.  Aggiungere un file di classe al progetto CommentAdornmentTest e denominarlo `CommentAdornmentManager`.

2.  Aggiungere le istruzioni `using` riportate di seguito.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Windows.Media;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Formatting;
    ```

3.  Aggiungere una classe denominata `CommentAdornmentManager`.

    ```csharp
    internal class CommentAdornmentManager
        {
        }
    ```

4.  Aggiungere alcuni campi privati.

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5.  Aggiungere un costruttore che sottoscrive il gestore per il <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> e <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> eventi, nonché al `CommentsChanged` evento. Il costruttore è privato perché il gestore viene creato mediante il metodo statico `Create()` (metodo).

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

6.  Aggiungere il `Create()` metodo che ottiene un provider o ne crea uno se necessario.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7.  Aggiungere il `CommentsChanged` gestore.

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

8.  Aggiungere il <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> gestore.

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

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Usare il comando di menu per aggiungere l'area di controllo di commento
 È possibile utilizzare il comando di menu per creare un'area di controllo di commento implementando il `MenuItemCallback` metodo del pacchetto VSPackage.

1.  Aggiungere i riferimenti seguenti al progetto MenuCommandTest:

    -   Microsoft.VisualStudio.TextManager.Interop

    -   Microsoft.VisualStudio.Editor

    -   Microsoft.VisualStudio.Text.UI.Wpf

2.  Aprire il *AddAdornment.cs* del file e aggiungere quanto segue `using` istruzioni.

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3.  Eliminare il `Execute()` (metodo) e aggiungere il gestore del comando seguente.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4.  Aggiungere codice per ottenere la visualizzazione attiva. È necessario ottenere il `SVsTextManager` della shell di Visual Studio per ottenere attivo `IVsTextView`.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5.  Se questa visualizzazione di testo è un'istanza di una visualizzazione di testo dell'editor, è possibile eseguirne il cast per la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> l'interfaccia e quindi ottenere il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> e l'identificatore associato <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>. Usare la <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> chiamare il `Connector.Execute()` metodo, che ottiene il provider dell'area di controllo di commento e aggiunge l'area di controllo. Il gestore del comando sarà ora simile a questo codice:

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

6.  Impostare il metodo AddAdornmentHandler come gestore per il comando AddAdornment nel costruttore AddAdornment.

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

1.  Compilare la soluzione e avviare il debug. L'istanza sperimentale dovrebbe essere visualizzato.

2.  Creare un file di testo. Digitare un testo e quindi selezionarlo.

3.  Nel **Tools** menu, fare clic su **richiamare Aggiungi dell'area di controllo**. Un fumetto dovrebbe essere visualizzato sul lato destro della finestra di testo e deve contenere il testo che è simile al testo seguente.

     Nome utente

     Fourscore...

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
