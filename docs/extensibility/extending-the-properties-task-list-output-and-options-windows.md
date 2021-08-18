---
title: Estendere le finestre Proprietà, Elenco attività, Output, Opzioni
description: Informazioni su come integrare le informazioni sulla finestra degli strumenti Visual Studio in una nuova pagina Opzioni e in una nuova impostazione nella pagina Proprietà.
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0d6d222ff143680ad6ae228649e695ee14268a39
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144782"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Estendere le finestre Proprietà, Elenco attività, Output e Opzioni
È possibile accedere a qualsiasi finestra degli strumenti Visual Studio. Questa procedura dettagliata illustra come integrare le  informazioni sulla finestra degli  strumenti in una nuova pagina  Opzioni e una nuova impostazione nella pagina Proprietà e come scrivere nelle finestre Elenco attività **e Output.**

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-tool-window"></a>Creare un'estensione con una finestra degli strumenti

1. Creare un progetto denominato **TodoList** usando il modello VSIX e aggiungere un modello di elemento della finestra degli strumenti personalizzato denominato **TodoWindow**.

    > [!NOTE]
    > Per altre informazioni sulla creazione di un'estensione con una finestra degli strumenti, vedere [Creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="set-up-the-tool-window"></a>Configurare la finestra degli strumenti
 Aggiungere un controllo TextBox in cui digitare un nuovo elemento ToDo, un pulsante per aggiungere il nuovo elemento all'elenco e un controllo ListBox per visualizzare gli elementi nell'elenco.

1. In *TodoWindow.xaml* eliminare i controlli Button, TextBox e StackPanel da UserControl.

    > [!NOTE]
    > In questo modo non viene **eliminato button1_Click** gestore dell'evento, che verrà riutilizzato in un passaggio successivo.

2. Dalla sezione **Tutti i controlli WPF** della Casella degli **strumenti** trascinare un **controllo Canvas** nella griglia.

3. Trascinare **un controllo TextBox**, **un controllo Button** e un **controllo ListBox** nell'area di disegno. Disporre gli elementi in modo che TextBox e Button siano sullo stesso livello e listBox riempia il resto della finestra sotto di essi, come nell'immagine seguente.

     ![Finestra degli strumenti finita](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")

4. Nel riquadro XAML trovare il pulsante e impostarne la proprietà Content su **Aggiungi**. Riconnettere il gestore eventi del pulsante al controllo Button aggiungendo un `Click="button1_Click"` attributo . Il blocco Canvas dovrebbe essere simile al seguente:

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

2. Aggiungere un riferimento pubblico a TodoWindow e fare in modo che il costruttore TodoWindowControl prenda un parametro TodoWindow. Il codice dovrebbe essere simile al seguente:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. In *TodoWindow.cs* modificare il costruttore TodoWindowControl in modo da includere il parametro TodoWindow. Il codice dovrebbe essere simile al seguente:

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
 È possibile specificare una pagina nella finestra **di dialogo** Opzioni in modo che gli utenti possano modificare le impostazioni per la finestra degli strumenti. La creazione di una pagina Opzioni richiede sia una classe che descrive le opzioni che una voce nel file *TodoListPackage.cs* o *TodoListPackage.vb.*

1. Aggiungere una classe denominata `ToolsOptions.cs`. Fare in `ToolsOptions` modo che la classe erediti da <xref:Microsoft.VisualStudio.Shell.DialogPage> .

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Aggiungere la seguente direttiva using:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. Nella pagina Opzioni di questa procedura dettagliata è disponibile una sola opzione denominata DaysAhead. Aggiungere un campo privato denominato **daysAhead** e una proprietà denominata **DaysAhead** alla `ToolsOptions` classe:

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   A questo punto è necessario rendere il progetto a conoscenza di questa pagina Opzioni.

### <a name="make-the-options-page-available-to-users"></a>Rendere disponibile la pagina Opzioni per gli utenti

1. In *TodoWindowPackage.cs* aggiungere un <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> oggetto alla classe `TodoWindowPackage` :

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. Il primo parametro per il costruttore ProvideOptionPage è il tipo della classe `ToolsOptions` , creata in precedenza. Il secondo parametro, "ToDo", è il nome della categoria nella **finestra di dialogo** Opzioni. Il terzo parametro, "Generale", è il nome  della sottocategoria della finestra di dialogo Opzioni in cui sarà disponibile la pagina Opzioni. I due parametri successivi sono ID risorsa per le stringhe. il primo è il nome della categoria e il secondo è il nome della sottocategoria. Il parametro finale determina se è possibile accedere a questa pagina usando l'automazione.

     Quando un utente apre la pagina Opzioni, dovrebbe essere simile all'immagine seguente.

     ![Pagina Opzioni](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     Si notino la **categoria ToDo** e la sottocategoria **Generale**.

## <a name="make-data-available-to-the-properties-window"></a>Rendere disponibili i dati per il Finestra Proprietà
 È possibile rendere disponibili le informazioni sull'elenco ToDo creando una classe denominata che archivia le informazioni sui singoli `TodoItem` elementi nell'elenco ToDo.

1. Aggiungere una classe denominata `TodoItem.cs`.

     Quando la finestra degli strumenti è disponibile per gli utenti, gli elementi in ListBox saranno rappresentati da TodoItems. Quando l'utente seleziona uno di questi elementi nel controllo ListBox, nella **finestra Proprietà** verranno visualizzate informazioni sull'elemento.

     Per rendere disponibili i dati nella **finestra Proprietà,** i dati vengono trasformati in proprietà pubbliche con due attributi speciali, `Description` e `Category` . `Description` è il testo visualizzato nella parte inferiore della **finestra** Proprietà. `Category`determina dove deve essere visualizzata la proprietà quando la **finestra** Proprietà viene visualizzata nella **visualizzazione Categorizzata.** Nell'immagine seguente  la finestra Proprietà si trova nella visualizzazione **Categorizzata,** la proprietà **Nome** nella categoria **Campi ToDo** è selezionata e la descrizione della proprietà **Nome** viene visualizzata nella parte inferiore della finestra.

     ![Finestra Proprietà](../extensibility/media/t5properties.png "T5Proprietà")

2. Aggiungere le direttive using seguenti al file *TodoItem.cs.*

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Aggiungere il `public` modificatore di accesso alla dichiarazione di classe.

    ```csharp
    public class TodoItem
    {
    }
    ```

     Aggiungere le due proprietà `Name` e `DueDate` . Verrà fatto il e `UpdateList()` `CheckForErrors()` versioni successive.

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

4. Aggiungere un riferimento privato al controllo utente. Aggiungere un costruttore che accetta il controllo utente e il nome per questo elemento ToDo. Per trovare il valore per `daysAhead` , ottiene la proprietà della pagina Opzioni.

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

5. Poiché le istanze della classe verranno archiviate in ListBox e ListBox chiamerà la funzione , è necessario `TodoItem` `ToString` eseguire l'overload della `ToString` funzione . Aggiungere il codice seguente a *TodoItem.cs*, dopo il costruttore e prima della fine della classe .

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. In *TodoWindowControl.xaml.cs* aggiungere metodi stub alla `TodoWindowControl` classe per i metodi e `CheckForError` `UpdateList` . Inserire i file dopo ProcessDialogChar e prima della fine del file.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     Il metodo chiamerà un metodo con lo stesso nome nell'oggetto padre e questo metodo verifica se si sono verificati errori e `CheckForError` li gestisce correttamente. Il `UpdateList` metodo aggiornerà ListBox nel controllo padre. Il metodo viene chiamato quando le `Name` proprietà e in questa classe `DueDate` cambiano. Verranno implementati in un secondo momento.

## <a name="integrate-into-the-properties-window"></a>Eseguire l'integrazione nel Finestra Proprietà
 Scrivere ora il codice che gestisce ListBox, che verrà associato alla **finestra** Proprietà.

 È necessario modificare il gestore del clic del pulsante per leggere TextBox, creare un Oggetto TodoItem e aggiungerlo a ListBox.

1. Sostituire la funzione `button1_Click` esistente con il codice che crea un nuovo Oggetto TodoItem e lo aggiunge a ListBox. Chiama `TrackSelection()` , che verrà definito in un secondo momento.

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

2. Nella visualizzazione Progettazione selezionare il controllo ListBox. Nella finestra **Proprietà** fare clic sul **pulsante Gestori** eventi e trovare **l'evento SelectionChanged.** Compilare la casella di testo **con listBox_SelectionChanged**. Questa operazione aggiunge uno stub per un gestore SelectionChanged e lo assegna all'evento .

3. Implementare il metodo `TrackSelection()`. Poiché è necessario ottenere i servizi, è necessario rendere accessibile l'oggetto <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> da TodoWindowControl. Aggiungere il metodo seguente alla classe `TodoWindow`:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Aggiungere le direttive using seguenti a *TodoWindowControl.xaml.cs*:

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

6. A questo punto, compilare la funzione TrackSelection, che fornirà l'integrazione con la **finestra** Proprietà. Questa funzione viene chiamata quando l'utente aggiunge un elemento a ListBox o fa clic su un elemento in ListBox. Aggiunge il contenuto di ListBox a un controllo SelectionContainer e passa SelectionContainer **al** gestore eventi della <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> finestra Proprietà. Il servizio TrackSelection tiene traccia degli oggetti selezionati nell'interfaccia utente e visualizza le relative proprietà

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

     Ora che si dispone di una classe **che** può essere utilizzata dalla finestra Proprietà, è possibile integrare la **finestra** Proprietà con la finestra degli strumenti. Quando l'utente fa clic su un elemento in ListBox nella finestra degli strumenti, la **finestra Proprietà** deve essere aggiornata di conseguenza. Analogamente, quando l'utente modifica un elemento ToDo nella finestra **Proprietà,** l'elemento associato deve essere aggiornato.

7. Aggiungere ora il resto del codice della funzione UpdateList in *TodoWindowControl.xaml.cs.* Deve eliminare e aggiungere nuovamente l'elemento TodoItem modificato da ListBox.

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

9. Aprire la **pagina**  >  **Opzioni** degli strumenti. Nel riquadro sinistro dovrebbe essere visualizzata la categoria ToDo. Le categorie sono elencate in ordine alfabetico, quindi cercare sotto le T.

10. Nella pagina **Delle opzioni Todo** dovrebbe essere visualizzata la proprietà `DaysAhead` impostata su **0.** Modificarlo in **2**.

11. Nel menu **Visualizza/Altro Windows** aprire **TodoWindow**. Digitare **EndDate** nella casella di testo e fare clic su **Aggiungi**.

12. Nella casella di riepilogo dovrebbe essere visualizzata una data due giorni dopo la data odierna.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Aggiungere testo alla finestra Output e gli elementi alla Elenco attività
 Per la **Elenco attività**, creare un nuovo oggetto di tipo Task e quindi aggiungerlo al Elenco attività **chiamando** il relativo metodo `Add` . Per scrivere nella finestra **Output,** chiamare il relativo metodo per ottenere un oggetto riquadro e quindi chiamare il `GetPane` metodo `OutputString` dell'oggetto riquadro.

1. In *TodoWindowControl.xaml.cs* aggiungere il codice per ottenere il riquadro Generale della finestra `button1_Click` **Output** (impostazione predefinita) e scriverlo.  Il metodo dovrebbe essere simile al seguente:

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

2. Per aggiungere elementi alla classe Elenco attività, è necessario un oggetto per aggiungere una classe annidata alla classe TodoWindowControl. La classe annidata deve derivare da <xref:Microsoft.VisualStudio.Shell.TaskProvider> . Aggiungere il codice seguente alla fine della `TodoWindowControl` classe .

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

3. Aggiungere quindi un riferimento privato `TodoTaskProvider` a e un metodo alla classe `CreateProvider()` `TodoWindowControl` . Il codice dovrebbe essere simile al seguente:

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

4. Aggiungere , che cancella i Elenco attività e , che aggiunge una voce al `ClearError()` `ReportError()` Elenco attività, alla `TodoWindowControl` classe .

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

5. Implementare ora `CheckForErrors` il metodo , come indicato di seguito.

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

## <a name="try-it-out"></a>Provare questa operazione

1. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.

2. Aprire **TodoWindow** (**Visualizza**  >  **altre Windows**  >  **TodoWindow**).

3. Digitare qualcosa nella casella di testo e quindi fare clic su **Aggiungi**.

     Alla casella di riepilogo viene aggiunta una data di scadenza di 2 giorni dopo la data odierna. Non vengono generati errori e il **Elenco attività** (**View** Elenco attività ) non deve  >  contenere voci.

4. Modificare ora l'impostazione nella **pagina ToDo** delle opzioni  >    >   degli strumenti **da 2** a **0.**

5. Digitare altro in **TodoWindow** e quindi fare di nuovo clic **su Aggiungi.** In questo modo viene attivato un errore e anche una voce **nel Elenco attività**.

     Quando si aggiungono elementi, la data iniziale viene impostata su ora più 2 giorni.

6. Scegliere **Output** dal menu Visualizza **per** aprire la **finestra Output.**

     Si noti che ogni volta che si aggiunge un elemento, viene visualizzato un messaggio nel **Elenco attività.**

7. Fare clic su uno degli elementi in ListBox.

     Nella **finestra Proprietà** vengono visualizzate le due proprietà per l'elemento.

8. Modificare una delle proprietà e quindi premere **INVIO.**

     L'elemento viene aggiornato in ListBox.
