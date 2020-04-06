---
title: Estendere le finestre Proprietà, Elenco attività, Output, Opzioni
ms.date: 11/04/2016
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
ms.openlocfilehash: db14068c97ff6868f5fb73c9ddd790020e99e7c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711627"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Estendere le finestre Proprietà, Elenco attività, Output e Opzioni
È possibile accedere a qualsiasi finestra degli strumenti in Visual Studio.You can access any tool window in Visual Studio. In questa procedura dettagliata viene illustrato come integrare le informazioni sulla finestra degli strumenti in una nuova pagina **Opzioni** e una nuova impostazione nella pagina **Proprietà,** nonché come scrivere nelle finestre **Elenco attività** e **Output.**

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-tool-window"></a>Creare un'estensione con una finestra degli strumentiCreate an extension with a tool window

1. Creare un progetto denominato **TodoList** utilizzando il modello VSIX e aggiungere un modello di elemento della finestra degli strumenti personalizzato denominato **TodoWindow**.

    > [!NOTE]
    > Per ulteriori informazioni sulla creazione di un'estensione con una finestra degli strumenti, consultate [Creare un'estensione con una finestra degli strumenti.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="set-up-the-tool-window"></a>Impostare la finestra degli strumenti
 Aggiungere un TextBox in cui digitare un nuovo toDo elemento, un Button per aggiungere il nuovo elemento all'elenco e un ListBox per visualizzare gli elementi nell'elenco.

1. In *TodoWindow.xaml*eliminare i controlli Button, TextBox e StackPanel da UserControl.

    > [!NOTE]
    > In questo modo non viene eliminato il gestore eventi **button1_Click,** che verrà riutilizzato in un passaggio successivo.

2. Dalla sezione **Tutti i controlli WPF** della Casella degli **strumenti**trascinare un controllo **Canvas** nella griglia.

3. Trascinare un **controllo TextBox**, un **Button**e un **controllo ListBox** nell'area di disegno. Disporre gli elementi in modo che il TextBox e il Button si trovano sullo stesso livello e il ListBox riempie il resto della finestra sotto di essi, come nell'immagine seguente.

     ![Finestra degli strumenti finita](../extensibility/media/t5-toolwindow.png "Finestra degli strumenti T5")

4. Nel riquadro XAML individuare il pulsante e impostarne la proprietà Content su **Add**. Riconnettere il gestore eventi del `Click="button1_Click"` pulsante al controllo Button aggiungendo un attributo. Il blocco Canvas dovrebbe essere simile al seguente:The Canvas block should look like this:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Personalizzare il costruttore

1. Nel file *TodoWindowControl.xaml.cs* aggiungere la direttiva using seguente:

    ```csharp
    using System;
    ```

2. Aggiungere un riferimento pubblico a TodoWindow e fare in modo che il costruttore TodoWindowControl accetta un parametro TodoWindow. Il codice dovrebbe essere simile al seguente:The code should look like this:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. In *TodoWindow.cs*, modificare il costruttore TodoWindowControl per includere il parametro TodoWindow . Il codice dovrebbe essere simile al seguente:The code should look like this:

    ```csharp
    public TodoWindow() : base(null)
    {
        this.Caption = "TodoWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;

         this.Content = new TodoWindowControl(this);
    }
    ```

## <a name="create-an-options-page"></a>Creare una pagina Opzioni
 È possibile fornire una pagina nella finestra di dialogo **Opzioni** in modo che gli utenti possano modificare le impostazioni per la finestra degli strumenti. La creazione di una pagina Opzioni richiede sia una classe che descrive le opzioni che una voce nel file *TodoListPackage.cs* o *TodoListPackage.vb.*

1. Aggiungere una classe denominata `ToolsOptions.cs`. Fare `ToolsOptions` in modo <xref:Microsoft.VisualStudio.Shell.DialogPage>che la classe erediti da .

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Aggiungere la seguente direttiva using:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. La pagina Opzioni di questa procedura dettagliata fornisce una sola opzione denominata DaysAhead.The Options page in this walkthrough provides only one option named DaysAhead. Aggiungere alla `ToolsOptions` classe un campo privato denominato **daysAhead** e una proprietà **denominata DaysAhead:**

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   A questo punto è necessario rendere il progetto a conoscenza di questa pagina Opzioni.

### <a name="make-the-options-page-available-to-users"></a>Rendere la pagina Opzioni disponibile per gli utenti

1. In *TodoWindowPackage.cs*aggiungere <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> a `TodoWindowPackage` alla classe :

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. Il primo parametro per il ProvideOptionPage `ToolsOptions`costruttore è il tipo della classe , che è stato creato in precedenza. Il secondo parametro, "ToDo", è il nome della categoria nella finestra di dialogo **Opzioni.** Il terzo parametro, "Generale", è il nome della sottocategoria della finestra di dialogo **Opzioni** in cui sarà disponibile la pagina Opzioni. I due parametri successivi sono gli IDENTIFICATORi di risorsa per le stringhe; il primo è il nome della categoria e il secondo è il nome della sottocategoria. Il parametro finale determina se è possibile accedere a questa pagina tramite automazione.

     Quando un utente apre la pagina Opzioni, dovrebbe essere simile all'immagine seguente.

     ![Pagina Opzioni](../extensibility/media/t5optionspage.gif "Pagina T5OptionsPagina")

     Si noti la categoria **ToDo** e la sottocategoria **Generale**.

## <a name="make-data-available-to-the-properties-window"></a>Rendere i dati disponibili per la finestra Proprietà
 È possibile rendere disponibili le informazioni dell'elenco ToDo creando una classe denominata `TodoItem` che archivia le informazioni sui singoli elementi nell'elenco Da fare.

1. Aggiungere una classe denominata `TodoItem.cs`.

     Quando la finestra degli strumenti è disponibile per gli utenti, gli elementi nel ListBox verranno rappresentati da TodoItems.When the tool window is available to users, the items in the ListBox will be represented by TodoItems. Quando l'utente seleziona uno di questi elementi nel ListBox, il **proprietà** finestra visualizzerà informazioni sull'elemento.

     Per rendere disponibili i dati nella finestra **Proprietà,** trasformare i dati `Description` `Category`in proprietà pubbliche con due attributi speciali e . `Description`è il testo visualizzato nella parte inferiore della finestra **Proprietà.** `Category`determina dove deve essere visualizzata la proprietà quando la finestra **Proprietà** viene visualizzata nella vista **Categorizzato.** Nell'immagine seguente la finestra **Proprietà** è in visualizzazione **Categorizzata,** la proprietà **Name** nella categoria **Campi ToDo** è selezionata e la descrizione della proprietà **Name** viene visualizzata nella parte inferiore della finestra.

     ![Finestra Proprietà](../extensibility/media/t5properties.png "Proprietà T5")

2. Aggiungere le direttive using seguenti al file *TodoItem.cs.*

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Aggiungere `public` il modificatore di accesso alla dichiarazione di classe.

    ```csharp
    public class TodoItem
    {
    }
    ```

     Aggiungere le due `Name` `DueDate`proprietà e . Faremo il `UpdateList()` e `CheckForErrors()` più tardi.

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

4. Aggiungere un riferimento privato al controllo utente. Aggiungere un costruttore che accetta il controllo utente e il nome per questo elemento ToDo.Add a constructor that takes the user control and the name for this ToDo item. Per trovare il `daysAhead`valore di , ottiene la proprietà della pagina Opzioni.

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

5. Poiché le `TodoItem` istanze della classe verranno archiviate in `ToString` ListBox e `ToString` ListBox chiamerà la funzione, è necessario eseguire l'overload della funzione. Aggiungere il codice riportato di seguito a *TodoItem.cs*, dopo il costruttore e prima della fine della classe .

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. In *TodoWindowControl.xaml.cs*, aggiungere metodi `TodoWindowControl` stub `CheckForError` `UpdateList` alla classe per i metodi e . Inserirli dopo il ProcessDialogChar e prima della fine del file.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     Il `CheckForError` metodo chiamerà un metodo che ha lo stesso nome nell'oggetto padre e tale metodo controllerà se si sono verificati errori e li gestirà correttamente. Il `UpdateList` metodo aggiornerà il ListBox nel controllo padre; il metodo viene `Name` chiamato `DueDate` quando le proprietà e in questa classe vengono modificate. Saranno implementati in un secondo momento.

## <a name="integrate-into-the-properties-window"></a>Integrazione nella finestra Proprietà
 A questo punto scrivere il codice che gestisce il ListBox, che sarà legato al **proprietà** finestra.

 È necessario modificare il gestore di clic del pulsante per leggere il TextBox, creare un TodoIteme aggiunge al ListBox.You must change the button click handler to read the TextBox, create a TodoItem, and adds it to the ListBox.

1. Sostituire la `button1_Click` funzione esistente con il codice che crea un nuovo TodoItem e lo aggiunge al ListBox. Chiama `TrackSelection()`, che verrà definito in un secondo momento.

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

2. Nella visualizzazione Progettazione selezionare il controllo ListBox. Nella finestra **Proprietà** fare clic sul pulsante **Gestori eventi** e individuare l'evento **SelectionChanged.** Compilare la casella di testo con **listBox_SelectionChanged**. In questo modo viene aggiunto uno stub per un gestore SelectionChanged e lo si assegna all'evento.

3. Implementare il metodo `TrackSelection()`. Poiché è necessario <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> ottenere i servizi, <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> è necessario rendere accessibile dal TodoWindowControl. Aggiungere il metodo seguente alla classe `TodoWindow`:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Aggiungere le seguenti direttive using a *TodoWindowControl.xaml.cs*:

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. Compilare il gestore SelectionChanged come segue:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. A questo punto, compilare la funzione TrackSelection, che fornirà l'integrazione con la finestra Proprietà.Now, fill in the TrackSelection function, which will provide integration with the **Properties** window. Questa funzione viene chiamata quando l'utente aggiunge un elemento per il ListBox o fa clic su un elemento nel ListBox.This function is called when the user adds an item to the ListBox or clicks an item in the ListBox. Aggiunge il contenuto di ListBox a un SelectionContainer e passa il <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> SelectionContainer per il gestore eventi della finestra **proprietà.** Il servizio TrackSelection tiene traccia degli oggetti selezionati nell'interfaccia utente e visualizza le relative proprietà

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

     Ora che si dispone di una classe che è possibile utilizzare la finestra **Proprietà,** è possibile integrare la finestra **Proprietà** con la finestra degli strumenti. Quando l'utente fa clic su un elemento nel ListBox nella finestra degli strumenti, il **proprietà** finestra deve essere aggiornata di conseguenza. Analogamente, quando l'utente modifica un ToDo elemento nel **proprietà** finestra, l'elemento associato deve essere aggiornato.

7. A questo punto, aggiungere il resto del codice della funzione UpdateList in *TodoWindowControl.xaml.cs*. Dovrebbe eliminare e aggiungere nuovamente l'oggetto TodoItem modificato dal ListBox.

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

9. Aprire la pagina**Opzioni** **degli strumenti.** >  La categoria ToDo dovrebbe essere visualizzata nel riquadro sinistro. Le categorie sono elencate in ordine alfabetico, quindi guarda sotto le T.

10. Nella pagina **Opzioni Todo** dovrebbe `DaysAhead` essere visualizzata la proprietà impostata su **0**. Cambiarlo in **2**.

11. Nel menu **Visualizza/ Altre finestre** aprire **TodoWindow**. Digitare **EndDate** nella casella di testo e fare clic su **Aggiungi**.

12. Nella casella di riepilogo dovrebbe essere visualizzata una data due giorni dopo rispetto alla presente.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Aggiungere testo alla finestra Output ed elementi all'Elenco attività
 Per **l'Elenco attività**, si crea un nuovo oggetto di tipo Task e `Add` quindi aggiungere tale oggetto task all'Elenco **attività** chiamando il relativo metodo . Per scrivere nella finestra **di output,** chiamare il relativo `GetPane` metodo `OutputString` per ottenere un oggetto pane e quindi chiamare il metodo dell'oggetto pane.

1. In *TodoWindowControl.xaml.cs*, `button1_Click` nel metodo aggiungere il codice per ottenere il riquadro **Generale** della finestra **Output** (impostazione predefinita) e scrivere in esso. Il metodo dovrebbe essere simile al seguente:

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

2. Per aggiungere elementi all'Elenco attività, è necessario aggiungere una classe annidata alla classe TodoWindowControl. La classe annidata <xref:Microsoft.VisualStudio.Shell.TaskProvider>deve derivare da . Aggiungere il codice seguente alla `TodoWindowControl` fine della classe.

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

3. Aggiungere quindi un `TodoTaskProvider` riferimento `CreateProvider()` privato e `TodoWindowControl` un metodo alla classe. Il codice dovrebbe essere simile al seguente:The code should look like this:

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

4. Aggiungere `ClearError()`, che cancella l'Elenco attività, e `ReportError()`, che aggiunge `TodoWindowControl` una voce all'Elenco attività, alla classe .

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

5. Implementare `CheckForErrors` ora il metodo, come indicato di seguito.

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

## <a name="try-it-out"></a>Provare il servizio

1. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

2. Aprire **TodoWindow** (**Visualizza** > **altre finestre** > **TodoWindow**).

3. Digitare un nome nella casella di testo e quindi fare clic su **Aggiungi**.

     Una data di scadenza 2 giorni dopo la data odierna viene aggiunta alla casella di riepilogo. Non vengono generati errori e l'Elenco **attività** (**Visualizza** > **elenco attività**) non deve avere voci.

4. Ora modificare l'impostazione nella pagina**Opzioni** >  **degli strumenti** > **Da fare** **a** **0**.

5. Digitare un'altra posizione nella **finestra da fare e** quindi fare di nuovo clic su **Aggiungi.** Questo attiva un errore e anche una voce **nell'Elenco attività**.

     Quando si aggiungono elementi, la data iniziale è impostata su ora più 2 giorni.

6. Scegliere **Output** dal menu **Visualizza** per aprire la finestra **Output.**

     Si noti che ogni volta che si aggiunge un elemento, viene visualizzato un messaggio nel riquadro **Elenco attività.**

7. Fare clic su uno degli elementi nel controllo ListBox.

     Nella finestra **Proprietà** vengono visualizzate le due proprietà dell'elemento.

8. Modificare una delle proprietà e quindi premere **INVIO**.

     L'elemento viene aggiornato nel ListBox.
