---
title: "Procedura dettagliata: utilizzo di un comando della shell con un'estensione dell'editor Documenti Microsoft"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52b151b09c1bb7306b4270f9408d0f04a7600aa2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697158"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>Procedura dettagliata: Usare un comando della shell con un'estensione dell'editorWalkthrough: Use a shell command with an editor extension
Da un pacchetto VSPackage, è possibile aggiungere funzionalità, ad esempio i comandi di menu per l'editor. Questa procedura dettagliata viene illustrato come aggiungere un'area di controllo a una visualizzazione di testo nell'editor richiamando un comando di menu.

 Questa procedura dettagliata viene illustrato l'utilizzo di un VSPackage con una parte del componente Managed Extensibility Framework (MEF). È necessario utilizzare un VSPackage per registrare il comando di menu con la shell di Visual Studio.You must use a VSPackage to register the menu command with the Visual Studio shell. Inoltre, è possibile utilizzare il comando per accedere alla parte del componente MEF.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It's included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-menu-command"></a>Creare un'estensione con un comando di menuCreate an extension with a menu command
 Creare un pacchetto VSPackage che inserisce un comando di menu denominato **Aggiungi area di controllo** nel **strumenti** menu.

1. Creare un progetto VSIX `MenuCommandTest`di C, denominato , quindi aggiungere un nome di modello di elemento Di comando personalizzato **AddAdornment**. Per ulteriori informazioni, consultate [Creare un'estensione con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)di menu.

2. Verrà aperta una soluzione denominata MenuCommandTest.A solution named MenuCommandTest opens. Il menu MenuCommandTestPackage file contiene il codice che crea il comando di menu e lo inserisce nel **strumenti** menu. A questo punto, il comando provoca solo una finestra di messaggio. I passaggi successivi mostreranno come modificare questa impostazione per visualizzare l'area di controllo dei commenti.

3. Aprire il file *source.extension.vsixmanifest* nell'Editor manifesto VSIX. La `Assets` scheda deve avere una riga per un Microsoft.VisualStudio.VsPackage denominato MenuCommandTest.The tab should have a row for a Microsoft.VisualStudio.VsPackage named MenuCommandTest.

4. Salvare e chiudere il file *source.extension.vsixmanifest.*

## <a name="add-a-mef-extension-to-the-command-extension"></a>Aggiungere un'estensione MEF all'estensione del comando

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo della soluzione, **scegliere Aggiungi**, quindi Nuovo **progetto**. Nella finestra di dialogo **Aggiungi nuovo progetto** fare clic su **Estensibilità** in **Visual Cè**, quindi **Progetto VSIX**. Assegnare al progetto il nome `CommentAdornmentTest`.

2. Poiché questo progetto interagirà con l'assembly VSPackage con nome sicuro, è necessario firmare l'assembly. È possibile riutilizzare il file di chiave già creato per l'assembly VSPackage.You can reuse the key file already created for the VSPackage assembly.

    1. Aprire le proprietà del progetto e selezionare la scheda **Firma.**

    2. Selezionare **Firma l'assieme**.

    3. In **Scegliere un file**di chiave con nome sicuro selezionare il file *Key.snk* generato per l'assembly MenuCommandTest.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>Fare riferimento all'estensione MEF nel progetto VSPackage
 Poiché si aggiunge un componente MEF al pacchetto VSPackage, è necessario specificare entrambi i tipi di risorse nel manifesto.

> [!NOTE]
> Per ulteriori informazioni su MEF, vedere [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Per fare riferimento al componente MEF nel progetto VSPackageTo refer to the MEF component in the VSPackage project

1. Nel progetto MenuCommandTest aprire il file *source.extension.vsixmanifest* nell'editor del manifesto VSIX.

2. Nella scheda **Risorse** fare clic su **Nuovo**.

3. Nell'elenco **Tipo** scegliere **Microsoft.VisualStudio.MefComponent**.

4. Nell'elenco **Origine** scegliere **Un progetto nella soluzione corrente.**

5. Nell'elenco **Progetto** scegliere **CommentAdornmentTest**.

6. Salvare e chiudere il file *source.extension.vsixmanifest.*

7. Assicurarsi che il MenuCommandTest progetto dispone di un riferimento al CommentAdornmentTest progetto.

8. Nel progetto CommentAdornmentTest impostare il progetto per produrre un assembly. In **Esplora soluzioni**selezionare il progetto e cercare **la** proprietà Copia output di compilazione in **OutputDirectory** e impostarlo su **true**.

## <a name="define-a-comment-adornment"></a>Definire un'area di controllo per i commentiDefine a comment adornment
 L'area di controllo <xref:Microsoft.VisualStudio.Text.ITrackingSpan> del commento è costituita da un che tiene traccia del testo selezionato e di alcune stringhe che rappresentano l'autore e la descrizione del testo.

#### <a name="to-define-a-comment-adornment"></a>Per definire un'area di controllo per i commentiTo define a comment adornment

1. Nel progetto CommentAdornmentTest aggiungere un nuovo file `CommentAdornment`di classe e denominarlo .

2. Aggiungere i riferimenti seguenti:

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.VisualStudio.Text.Logic

    4. Microsoft.VisualStudio.Text.UI

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Composition

    7. PresentationCore

    8. PresentationFramework

    9. WindowsBase

3. Aggiungere la `using` direttiva seguente.

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. Il file deve contenere una classe denominata `CommentAdornment`.

    ```csharp
    internal class CommentAdornment
    ```

5. Aggiungere tre campi `CommentAdornment` alla <xref:Microsoft.VisualStudio.Text.ITrackingSpan>classe per , l'autore e la descrizione.

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6. Aggiungere un costruttore che inizializza i campi.

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>Creare un elemento visivo per l'area di controlloCreate a visual element for the adornment
 Definire un elemento visivo per l'area di controllo. Per questa procedura dettagliata, definire un controllo che eredita <xref:System.Windows.Controls.Canvas>dalla classe Windows Presentation Foundation (WPF).

1. Creare una classe nel progetto CommentAdornmentTest `CommentBlock`e denominarla .

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

3. Fare `CommentBlock` in modo <xref:System.Windows.Controls.Canvas>che la classe erediti da .

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. Aggiungere alcuni campi privati per definire gli aspetti visivi dell'area di controllo.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. Aggiungere un costruttore che definisce l'area di controllo del commento e aggiunge il testo pertinente.

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

6. Implementare <xref:System.Windows.Controls.Panel.OnRender%2A> anche un gestore eventi che disegna l'area di controllo.

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

## <a name="add-an-iwpftextviewcreationlistener"></a>Aggiungere un iWpfTextViewCreationListenerAdd an IWpfTextViewCreationListener
 Si <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> tratta di una parte componente MEF che è possibile utilizzare per ascoltare gli eventi di creazione della vista.

1. Aggiungere un file di classe al progetto `Connector`CommentAdornmentTest e denominarlo .

2. Aggiungere le `using` direttive seguenti.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Dichiarare una classe <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>che implementa , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> ed esportarla <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> con <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>un di "text" e a of . L'attributo del tipo di contenuto specifica il tipo di contenuto a cui si applica il componente. Il tipo di testo è il tipo di base per tutti i tipi di file non binari. Pertanto, quasi tutte le visualizzazioni di testo create saranno di questo tipo. L'attributo del ruolo della visualizzazione di testo specifica il tipo di visualizzazione di testo a cui si applica il componente. I ruoli di visualizzazione del testo del documento mostrano in genere il testo composto da righe e archiviato in un file.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. Implementare <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> il metodo in `Create()` modo che `CommentAdornmentManager`chiami l'evento statico dell'oggetto .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. Aggiungere un metodo che è possibile utilizzare per eseguire il comando.

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

## <a name="define-an-adornment-layer"></a>Definire un livello di area di controlloDefine an adornment layer
 Per aggiungere una nuova area di controllo, è necessario definire un livello di area di controllo.

### <a name="to-define-an-adornment-layer"></a>Per definire un livello di area di controlloTo define an adornment layer

1. Nella `Connector` classe dichiarare un campo <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>pubblico di tipo <xref:Microsoft.VisualStudio.Utilities.NameAttribute> ed esportarlo con un oggetto che <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> specifichi un nome univoco per il layer dell'area di controllo e un oggetto che definisca la relazione dell'ordine z di questo livello di area di testo agli altri livelli della visualizzazione testo (testo, punto di inserimento e selezione).

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>Fornire aree di controllo di commentoProvide comment ornamentments
 Quando si definisce un'area di controllo, implementare anche un provider di area di controllo di commento e un gestore dell'area di controllo di commento. Il provider di aree di controllo di commento <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> mantiene un elenco di aree di controllo di commento, ascolta gli eventi nel buffer di testo sottostante ed elimina le aree di controllo di commento quando viene eliminato il testo sottostante.

1. Aggiungere un nuovo file di classe al progetto `CommentAdornmentProvider`CommentAdornmentTest e denominarlo .

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

4. Aggiungere campi privati per il buffer di testo e l'elenco delle aree di controllo di commento relative al buffer.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. Aggiungere un `CommentAdornmentProvider`costruttore per . Questo costruttore deve avere accesso privato perché `Create()` viene creata un'istanza del provider dal metodo. Il costruttore `OnBufferChanged` aggiunge il <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> gestore eventi all'evento.

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

8. Aggiungere `OnBufferChanged` il gestore eventi.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. Aggiungere una dichiarazione per un `CommentsChanged` evento.

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. Creare `Add()` un metodo per aggiungere l'area di controllo.

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

11. Aggiungere `RemoveComments()` un metodo.

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

12. Aggiungere `GetComments()` un metodo che restituisce tutti i commenti in un intervallo di snapshot specificato.

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

13. Aggiungere una `CommentsChangedEventArgs`classe denominata , come indicato di seguito.

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

## <a name="manage-comment-adornments"></a>Gestire le aree di controllo dei commenti
 Il gestore dell'area di controllo del commento crea l'area di controllo e la aggiunge al livello dell'area di controllo. È in ascolto degli <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> eventi e <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> in modo che possa spostare o eliminare l'area di controllo. È inoltre in `CommentsChanged` ascolto dell'evento generato dal provider dell'area di controllo dei commenti quando vengono aggiunti o rimossi commenti.

1. Aggiungere un file di classe al progetto `CommentAdornmentManager`CommentAdornmentTest e denominarlo .

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

5. Aggiungere un costruttore che sottoscrive <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> il gestore `CommentsChanged` agli eventi <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> e e anche all'evento. Il costruttore è privato perché viene `Create()` creata un'istanza del gestore dal metodo statico.

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

6. Aggiungere `Create()` il metodo che ottiene un provider o ne crea uno se necessario.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. Aggiungere `CommentsChanged` il gestore.

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

8. Aggiungere <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> il gestore.

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. Aggiungere <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> il gestore.

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

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Usare il comando di menu per aggiungere l'area di controllo dei commenti
 È possibile utilizzare il comando di menu per `MenuItemCallback` creare un'area di controllo di commento implementando il metodo del pacchetto VSPackage.You can use the menu command to create a comment adornment by implementing the method of the VSPackage.

1. Aggiungere i seguenti riferimenti al progetto MenuCommandTest:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.Editor

    - Microsoft.VisualStudio.Text.UI.Wpf

2. Aprire il file *di* `using` AddAdornment.cs e aggiungere le direttive seguenti.

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. Eliminare `Execute()` il metodo e aggiungere il gestore comandi seguente.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. Aggiungere codice per ottenere la visualizzazione attiva. È necessario `SVsTextManager` ottenere il codice della shell `IVsTextView`di Visual Studio per ottenere l'oggetto active .

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. Se questa visualizzazione di testo è un'istanza di una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> visualizzazione di <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> testo dell'editor, è possibile eseguire il cast all'interfaccia e quindi ottenere il file e associarlo <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>. Utilizzare <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> il per `Connector.Execute()` chiamare il metodo , che ottiene il provider dell'area di controllo di commento e aggiunge l'area di controllo. Il gestore dei comandi dovrebbe ora essere simile al codice seguente:The command handler should now look like this code:

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

6. Impostare il AddAdornmentHandler metodo come gestore per il AddAdornment comando nel AddAdornment costruttore.

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

## <a name="build-and-test-the-code"></a>Compilare e testare il codiceBuild and test the code

1. Compilare la soluzione e avviare il debug. Verrà visualizzata l'istanza sperimentale.

2. Creare un file di testo. Digitare del testo e selezionarlo.

3. Scegliere Richiama Aggiungi **area di adorna**dal menu **Strumenti** . Un fumetto deve essere visualizzato sul lato destro della finestra di testo e deve contenere testo simile al testo seguente.

     NomeUtente

     Fourscore...

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di fileWalkthrough: Link a content type to a file name extension](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
