---
title: Estendi proprietà, Elenco attività, output, finestre opzioni
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c968544c6bf52a901052fc7aedbbee66dcc10e62
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038478"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Estendere le finestre Proprietà, Elenco attività, output e opzioni
È possibile accedere a qualsiasi finestra degli strumenti in Visual Studio. In questa procedura dettagliata viene illustrato come integrare le informazioni relative alla finestra degli strumenti in una nuova pagina **Opzioni** e una nuova impostazione nella pagina **Proprietà** e come scrivere nelle finestre di **elenco attività** e **output** .

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-tool-window"></a>Creare un'estensione con una finestra degli strumenti

1. Creare un progetto denominato **todo** usando il modello VSIX e aggiungere un modello di elemento della finestra degli strumenti personalizzato denominato **TodoWindow**.

    > [!NOTE]
    > Per ulteriori informazioni sulla creazione di un'estensione con una finestra degli strumenti, vedere [creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="set-up-the-tool-window"></a>Configurare la finestra degli strumenti
 Aggiungere una casella di testo in cui digitare un nuovo elemento ToDo, un pulsante per aggiungere il nuovo elemento all'elenco e una casella di riepilogo per visualizzare gli elementi nell'elenco.

1. In *TodoWindow. XAML*, eliminare i controlli Button, TextBox e StackPanel da UserControl.

    > [!NOTE]
    > Questa operazione non elimina il gestore dell'evento **Button1_Click** , che verrà riutilizzato in un passaggio successivo.

2. Dalla sezione **tutti i controlli WPF** della **casella degli strumenti**trascinare un controllo **Canvas** nella griglia.

3. Trascinare una **casella di testo**, un **pulsante**e una **casella di riepilogo** nell'area di disegno. Disporre gli elementi in modo che la casella di testo e il pulsante si trovino sullo stesso livello e la casella di riepilogo riempie il resto della finestra sottostante, come nell'immagine seguente.

     ![Finestra degli strumenti finita](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")

4. Nel riquadro XAML trovare il pulsante e impostarne la proprietà Content su **Add**. Riconnettere il gestore dell'evento Button al controllo Button aggiungendo un `Click="button1_Click"` attributo. Il blocco canvas avrà un aspetto simile al seguente:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Personalizzare il costruttore

1. Nel file *TodoWindowControl.XAML.cs* aggiungere la direttiva using seguente:

    ```csharp
    using System;
    ```

2. Aggiungere un riferimento pubblico a TodoWindow e fare in modo che il costruttore TodoWindowControl accetta un parametro TodoWindow. Il codice dovrebbe essere simile al seguente:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. In *TodoWindow.cs*modificare il costruttore TodoWindowControl in modo da includere il parametro TodoWindow. Il codice dovrebbe essere simile al seguente:

    ```csharp
    public TodoWindow() : base(null)
    {
        this.Caption = "TodoWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;

         this.Content = new TodoWindowControl(this);
    }
    ```

## <a name="create-an-options-page"></a>Creare una pagina di opzioni
 È possibile specificare una pagina nella finestra di dialogo **Opzioni** in modo che gli utenti possano modificare le impostazioni per la finestra degli strumenti. La creazione di una pagina di opzioni richiede sia una classe che descrive le opzioni e una voce nel file *TodoListPackage.cs* o *TodoListPackage. vb* .

1. Aggiungere una classe denominata `ToolsOptions.cs`. Fare in modo che la `ToolsOptions` classe erediti da <xref:Microsoft.VisualStudio.Shell.DialogPage> .

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Aggiungere la seguente direttiva using:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. Nella pagina Opzioni di questa procedura dettagliata è disponibile una sola opzione denominata DaysAhead. Aggiungere un campo privato denominato **daysAhead** e una proprietà denominata **daysAhead** alla `ToolsOptions` classe:

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   A questo punto è necessario rendere il progetto consapevole della pagina Opzioni.

### <a name="make-the-options-page-available-to-users"></a>Rendere disponibile la pagina opzioni agli utenti

1. In *TodoWindowPackage.cs*aggiungere un <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> alla `TodoWindowPackage` classe:

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. Il primo parametro del costruttore ProvideOptionPage è il tipo della classe creata in `ToolsOptions` precedenza. Il secondo parametro, "ToDo", è il nome della categoria nella finestra di dialogo **Opzioni** . Il terzo parametro, "General", è il nome della sottocategoria della finestra di dialogo **Opzioni** in cui sarà disponibile la pagina Opzioni. I due parametri successivi sono gli ID risorsa per le stringhe. il primo è il nome della categoria e il secondo è il nome della sottocategoria. Il parametro finale determina se è possibile accedere a questa pagina tramite l'automazione.

     Quando un utente apre la pagina di opzioni, dovrebbe essere simile all'immagine seguente.

     ![Pagina Opzioni](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     Si noti la categoria **todo** e la sottocategoria **generale**.

## <a name="make-data-available-to-the-properties-window"></a>Rendere i dati disponibili per l'Finestra Proprietà
 È possibile rendere disponibili le informazioni sull'elenco ToDo creando una classe denominata `TodoItem` che archivia le informazioni sui singoli elementi nell'elenco attività.

1. Aggiungere una classe denominata `TodoItem.cs`.

     Quando la finestra degli strumenti è disponibile per gli utenti, gli elementi nella casella di riepilogo verranno rappresentati da TodoItems. Quando l'utente seleziona uno di questi elementi nella casella di riepilogo, nella finestra **Proprietà** vengono visualizzate le informazioni sull'elemento.

     Per rendere disponibili i dati nella finestra **Proprietà** , è necessario trasformarli in proprietà pubbliche con due attributi speciali, `Description` e `Category` . `Description` testo visualizzato nella parte inferiore della finestra delle **Proprietà** . `Category` determina la posizione in cui la proprietà deve essere visualizzata quando la finestra **Proprietà** viene visualizzata nella vista **categorizzata** . Nella figura seguente, la finestra **Proprietà** è in visualizzazione **categorizzata** , la proprietà **Name** nella categoria **campi todo** è selezionata e la descrizione della proprietà **Name** viene visualizzata nella parte inferiore della finestra.

     ![Finestra Proprietà](../extensibility/media/t5properties.png "T5Properties")

2. Aggiungere le direttive using seguenti al file *TodoItem.cs* .

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Aggiungere il `public` modificatore di accesso alla dichiarazione della classe.

    ```csharp
    public class TodoItem
    {
    }
    ```

     Aggiungere le due proprietà, `Name` e `DueDate` . Verranno eseguite le operazioni `UpdateList()` e `CheckForErrors()` versioni successive.

    ```csharp
    public class TodoItem
    {
        private TodoWindowControl parent;
        private string name;
        [Description("Name of the ToDo item")]
        [Category("ToDo Fields")]
        public string Name
        {
            get { return name; }
            set
            {
                name = value;
                parent.UpdateList(this);
            }
        }

        private DateTime dueDate;
        [Description("Due date of the ToDo item")]
        [Category("ToDo Fields")]
        public DateTime DueDate
        {
            get { return dueDate; }
            set
            {
                dueDate = value;
                parent.UpdateList(this);
                parent.CheckForErrors();
            }
        }
    }
    ```

4. Aggiungere un riferimento privato al controllo utente. Aggiungere un costruttore che accetta il controllo utente e il nome per questo elemento ToDo. Per trovare il valore di `daysAhead` , ottiene la proprietà della pagina Opzioni.

    ```csharp
    private TodoWindowControl parent;

    public TodoItem(TodoWindowControl control, string itemName)
    {
        parent = control;
        name = itemName;
        dueDate = DateTime.Now;

        double daysAhead = 0;
        IVsPackage package = parent.parent.Package as IVsPackage;
        if (package != null)
        {
            object obj;
            package.GetAutomationObject("ToDo.General", out obj);

            ToolsOptions options = obj as ToolsOptions;
            if (options != null)
            {
                daysAhead = options.DaysAhead;
            }
        }

        dueDate = dueDate.AddDays(daysAhead);
    }
    ```

5. Poiché le istanze della `TodoItem` classe verranno archiviate nella casella di riepilogo e il controllo ListBox chiamerà la `ToString` funzione, è necessario eseguire l'overload della `ToString` funzione. Aggiungere il codice seguente a *TodoItem.cs*, dopo il costruttore e prima della fine della classe.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. In *TodoWindowControl.XAML.cs*aggiungere i metodi stub alla `TodoWindowControl` classe per i `CheckForError` metodi e `UpdateList` . Inserirli dopo ProcessDialogChar e prima della fine del file.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     Il metodo chiamerà `CheckForError` un metodo con lo stesso nome nell'oggetto padre e il metodo verificherà se si sono verificati errori e li gestirà correttamente. Il `UpdateList` metodo aggiornerà la casella di riepilogo nel controllo padre. il metodo viene chiamato quando `Name` le `DueDate` proprietà e in questa classe cambiano. Verranno implementate in un secondo momento.

## <a name="integrate-into-the-properties-window"></a>Integrazione nel Finestra Proprietà
 A questo punto, scrivere il codice che gestisce la ListBox, che verrà associata alla finestra **Proprietà** .

 È necessario modificare il gestore clic del pulsante per leggere la casella di testo, creare un TodoItem e aggiungerlo alla casella di riepilogo.

1. Sostituire la `button1_Click` funzione esistente con il codice che crea un nuovo TodoItem e lo aggiunge alla casella di riepilogo. Chiama `TrackSelection()` , che verrà definito in un secondo momento.

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. Nella visualizzazione Progettazione selezionare il controllo ListBox. Nella finestra **Proprietà** fare clic sul pulsante **gestori eventi** e individuare l'evento **SelectionChanged** . Compilare la casella di testo con **listBox_SelectionChanged**. Questa operazione aggiunge uno stub per un gestore SelectionChanged e lo assegna all'evento.

3. Implementare il metodo `TrackSelection()`. Poiché è necessario ottenere i <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> servizi, è necessario rendere <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> accessibile dal TodoWindowControl. Aggiungere il metodo seguente alla classe `TodoWindow`:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Aggiungere le direttive using seguenti a *TodoWindowControl.XAML.cs*:

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. Compilare il gestore SelectionChanged come indicato di seguito:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. A questo punto, compilare la funzione TrackSelection, che fornirà l'integrazione con la finestra **Proprietà** . Questa funzione viene chiamata quando l'utente aggiunge un elemento alla casella di riepilogo o fa clic su un elemento nella casella di riepilogo. Aggiunge il contenuto della casella di riepilogo a un oggetto SelectionContainer e passa l'oggetto SelectionContainer al gestore eventi della finestra delle **Proprietà** <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> . Il servizio TrackSelection tiene traccia degli oggetti selezionati nell'interfaccia utente (UI) e ne Visualizza le proprietà

    ```csharp
    private SelectionContainer mySelContainer;
    private System.Collections.ArrayList mySelItems;
    private IVsWindowFrame frame = null;

    private void TrackSelection()
    {
        if (frame == null)
        {
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;
            if (shell != null)
            {
                var guidPropertyBrowser = new
                Guid(ToolWindowGuids.PropertyBrowser);
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,
                ref guidPropertyBrowser, out frame);
            }
        }
        if (frame != null)
            {
                frame.Show();
            }
        if (mySelContainer == null)
        {
            mySelContainer = new SelectionContainer();
        }

        mySelItems = new System.Collections.ArrayList();

        var selected = listBox.SelectedItem as TodoItem;
        if (selected != null)
        {
            mySelItems.Add(selected);
        }

        mySelContainer.SelectedObjects = mySelItems;

        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))
                                as ITrackSelection;
        if (track != null)
        {
            track.OnSelectChange(mySelContainer);
        }
    }
    ```

     Ora che è disponibile una classe che può essere usata dalla finestra **Proprietà** , è possibile integrare la finestra **Proprietà** con la finestra degli strumenti. Quando l'utente fa clic su un elemento nella casella di riepilogo nella finestra degli strumenti, la finestra **Proprietà** deve essere aggiornata di conseguenza. Analogamente, quando l'utente modifica un elemento ToDo nella finestra **Proprietà** , l'elemento associato deve essere aggiornato.

7. A questo punto, aggiungere il resto del codice della funzione Updates in *TodoWindowControl.XAML.cs*. Deve eliminare e aggiungere nuovamente il TodoItem modificato dalla casella di riepilogo.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. Testare il codice. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale.

9. Aprire la **Tools**  >  pagina**Opzioni** strumenti. Nel riquadro sinistro dovrebbe essere visualizzata la categoria ToDo. Le categorie sono elencate in ordine alfabetico, quindi cercare in Servizi terminal.

10. Nella pagina Opzioni **todo** dovrebbe essere visualizzata la `DaysAhead` proprietà impostata su **0**. Impostarla su **2**.

11. Nel menu **Visualizza/altre finestre** aprire **TodoWindow**. Digitare **EndDate** nella casella di testo e fare clic su **Aggiungi**.

12. Nella casella di riepilogo dovrebbe essere visualizzata una data di due giorni dopo la data odierna.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Aggiungere testo alla finestra di output ed elementi al Elenco attività
 Per il **elenco attività**si crea un nuovo oggetto di tipo Task, quindi si aggiunge tale oggetto attività alla **elenco attività** chiamando il relativo `Add` metodo. Per scrivere nella finestra di **output** , chiamare il relativo `GetPane` metodo per ottenere un oggetto riquadro, quindi chiamare il `OutputString` metodo dell'oggetto riquadro.

1. In *TodoWindowControl.XAML.cs*, nel `button1_Click` metodo, aggiungere il codice per ottenere il riquadro **generale** della finestra di **output** (impostazione predefinita) e scrivervi. Il metodo dovrebbe essere simile al seguente:

    ```csharp
    private void button1_Click(object sender, EventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);

            var outputWindow = parent.GetVsService(
                typeof(SVsOutputWindow)) as IVsOutputWindow;
            IVsOutputWindowPane pane;
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;
            outputWindow.GetPane(ref guidGeneralPane, out pane);
            if (pane != null)
            {
                 pane.OutputString(string.Format(
                    "To Do item created: {0}\r\n",
                 item.ToString()));
        }
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. Per aggiungere elementi alla Elenco attività, è necessario un per aggiungere una classe annidata alla classe TodoWindowControl. La classe annidata deve derivare da <xref:Microsoft.VisualStudio.Shell.TaskProvider> . Aggiungere il codice seguente alla fine della `TodoWindowControl` classe.

    ```csharp
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]
    public class TodoWindowTaskProvider : TaskProvider
    {
        public TodoWindowTaskProvider(IServiceProvider sp)
            : base(sp)
        {
        }
    }
    ```

3. Aggiungere quindi un riferimento privato a `TodoTaskProvider` e un `CreateProvider()` metodo alla `TodoWindowControl` classe. Il codice dovrebbe essere simile al seguente:

    ```csharp
    private TodoWindowTaskProvider taskProvider;
    private void CreateProvider()
    {
        if (taskProvider == null)
        {
            taskProvider = new TodoWindowTaskProvider(parent);
            taskProvider.ProviderName = "To Do";
        }
    }
    ```

4. Aggiungere `ClearError()` , che cancella il elenco attività e `ReportError()` , che aggiunge una voce al elenco attività, alla `TodoWindowControl` classe.

    ```csharp
    private void ClearError()
    {
        CreateProvider();
        taskProvider.Tasks.Clear();
    }
    private void ReportError(string p)
    {
        CreateProvider();
        var errorTask = new Task();
        errorTask.CanDelete = false;
        errorTask.Category = TaskCategory.Comments;
        errorTask.Text = p;

        taskProvider.Tasks.Add(errorTask);

        taskProvider.Show();

        var taskList = parent.GetVsService(typeof(SVsTaskList))
            as IVsTaskList2;
        if (taskList == null)
        {
            return;
        }

        var guidProvider = typeof(TodoWindowTaskProvider).GUID;
         taskList.SetActiveProvider(ref guidProvider);
    }
    ```

5. Implementare ora il `CheckForErrors` metodo, come indicato di seguito.

    ```csharp
    public void CheckForErrors()
    {
        foreach (TodoItem item in listBox.Items)
        {
            if (item.DueDate < DateTime.Now)
            {
                ReportError("To Do Item is out of date: "
                    + item.ToString());
            }
        }
    }
    ```

## <a name="try-it-out"></a>Procedura

1. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

2. Aprire il **TodoWindow** (**visualizzare**  >  **altre**  >  **TodoWindow**di Windows).

3. Digitare un valore nella casella di testo e quindi fare clic su **Aggiungi**.

     Una data di scadenza 2 giorni dopo la data odierna viene aggiunta alla casella di riepilogo. Non viene generato alcun errore e il **elenco attività** (**visualizzazione**  >  **elenco attività**) non deve avere voci.

4. A questo punto, modificare l'impostazione nella pagina di **strumenti**  >  **Opzioni**di  >  **todo** da **2** a **0**.

5. Digitare un altro elemento nel **TodoWindow** , quindi fare di nuovo clic su **Aggiungi** . Viene attivato un errore e una voce nel **elenco attività**.

     Quando si aggiungono elementi, la data iniziale è impostata su Now più 2 giorni.

6. Scegliere **output** dal menu **Visualizza** per aprire la finestra di **output** .

     Si noti che ogni volta che si aggiunge un elemento, nel riquadro **elenco attività** viene visualizzato un messaggio.

7. Fare clic su uno degli elementi nella casella di riepilogo.

     Nella finestra **Proprietà** vengono visualizzate le due proprietà per l'elemento.

8. Modificare una delle proprietà, quindi premere **invio**.

     L'elemento viene aggiornato nella casella di riepilogo.
