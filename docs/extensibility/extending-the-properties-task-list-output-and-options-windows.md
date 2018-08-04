---
title: Estensione di proprietà, elenco attività, Output e opzioni Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad9cd6c3356d38184b24a7e2ecfa06ca954bfbb0
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499877"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Estendere le finestre delle proprietà, elenco attività, Output e opzioni
È possibile accedere a qualsiasi finestra degli strumenti in Visual Studio. Questa procedura dettagliata illustra come integrare informazioni sulla finestra degli strumenti in una nuova **opzioni** pagina e una nuova impostazione sul **proprietà** pagina, nonché come scrivere il **elenco attività** e **Output** windows.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-an-extension-with-a-tool-window"></a>Creare un'estensione con una finestra degli strumenti  
  
1.  Creare un progetto denominato **TodoList** usando il modello di progetto VSIX e aggiungere un modello di elemento di finestra degli strumenti personalizzata denominato **TodoWindow**.  
  
    > [!NOTE]
    >  Per altre informazioni sulla creazione di un'estensione con una finestra degli strumenti, vedere [creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="set-up-the-tool-window"></a>Configurare la finestra degli strumenti  
 Aggiungere una casella di testo in cui è possibile digitare un nuovo elemento ToDo, un pulsante per aggiungere il nuovo elemento all'elenco e una casella di riepilogo per visualizzare gli elementi nell'elenco.  
  
1.  Nelle *TodoWindow.xaml*, eliminare i controlli Button, TextBox e StackPanel da UserControl.  
  
    > [!NOTE]
    >  Questa operazione non elimina il **button1_Click** gestore eventi, che verrà riutilizzata in un passaggio successivo.  
  
2.  Dal **tutti i controlli WPF** sezione del **della casella degli strumenti**, trascinare un' **Canvas** controllo alla griglia.  
  
3.  Trascinare un **casella di testo**, un **pulsante**e un **ListBox** all'area di disegno. Disporre gli elementi in modo che la casella di testo e il pulsante sono allo stesso livello e la casella di riepilogo riempie il resto della finestra di sotto di essi, come illustrato nell'immagine seguente.  
  
     ![Finestra degli strumenti completato](../extensibility/media/t5-toolwindow.png "T5 ToolWindow")  
  
4.  Nel riquadro di XAML, trovare il pulsante e impostarne la proprietà Content **Add**. Riconnettere il gestore eventi del pulsante per il controllo pulsante mediante l'aggiunta di un `Click="button1_Click"` attributo. Il blocco di area di disegno sarà simile al seguente:  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
### <a name="customize-the-constructor"></a>Personalizzare il costruttore  
  
1.  Nel *TodoWindowControl.xaml.cs* file, aggiungere la seguente istruzione using:  
  
    ```csharp  
    using System;  
    ```  
  
2.  Aggiungere un riferimento pubblico per il TodoWindow e dispone del costruttore TodoWindowControl accettano un parametro TodoWindow. Il codice dovrebbe essere simile al seguente:  
  
    ```csharp  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3.  Nelle *TodoWindow.cs*, modificare il costruttore TodoWindowControl per includere il parametro TodoWindow. Il codice dovrebbe essere simile al seguente:  
  
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
 È possibile fornire una pagina nel **opzioni** finestra di dialogo in modo che gli utenti possono modificare le impostazioni della finestra degli strumenti. Creazione di una pagina di opzioni richiede sia una classe che descrive le opzioni e una voce nella *TodoListPackage.cs* oppure *TodoListPackage.vb* file.  
  
1.  Aggiungere una classe denominata `ToolsOptions.cs`. Verificare i `ToolsOptions` classe ereditare da <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```csharp  
    class ToolsOptions : DialogPage  
    {  
    }  
    ```  
  
2.  Aggiungere la seguente istruzione using:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
3.  La pagina di opzioni in questa procedura dettagliata fornisce solo un'opzione denominata DaysAhead. Aggiungere un campo privato denominato **daysAhead** e una proprietà denominata **DaysAhead** per il `ToolsOptions` classe:  
  
    ```csharp  
    private double daysAhead;  
  
    public double DaysAhead  
    {  
        get { return daysAhead; }  
        set { daysAhead = value; }  
    }  
    ```  
  
 A questo punto è necessario apportare consapevoli di questa pagina di opzioni del progetto.  
  
### <a name="make-the-options-page-available-to-users"></a>Rendere disponibile la pagina di opzioni agli utenti  
  
1.  Nelle *TodoWindowPackage.cs*, aggiungere un <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> per il `TodoWindowPackage` classe:  
  
    ```csharp  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2.  Il primo parametro del costruttore ProvideOptionPage è il tipo della classe `ToolsOptions`, creato in precedenza. Il secondo parametro, "ToDo", è il nome della categoria nel **opzioni** nella finestra di dialogo. Il terzo parametro, "Generale", è il nome della sottocategoria del **opzioni** finestra di dialogo in cui sarà disponibile la pagina di opzioni. I due parametri successivi sono ID di risorsa per le stringhe; il primo è il nome della categoria e il secondo è il nome della sottocategoria. L'ultimo parametro determina se questa pagina è accessibile tramite l'automazione.  
  
     Quando un utente apre la pagina delle opzioni, che dovrebbe essere simile l'immagine seguente.  
  
     ![Pagina delle opzioni](../extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     Si noti che la categoria **ToDo** e la sottocategoria **generali**.  
  
## <a name="make-data-available-to-the-properties-window"></a>Rendere disponibile la finestra delle proprietà dei dati  
 È possibile rendere disponibili informazioni relative all'elenco ToDo creando una classe denominata `TodoItem` che archivia informazioni sugli elementi singoli nell'elenco ToDo.  
  
1.  Aggiungere una classe denominata `TodoItem.cs`.  
  
     Quando la finestra degli strumenti è disponibile per gli utenti, gli elementi nella casella di riepilogo saranno rappresentati da elementi TodoItems. Quando l'utente seleziona uno di questi elementi nella casella di riepilogo, il **proprietà** finestra visualizzerà informazioni sull'elemento.  
  
     Per rendere i dati disponibili nel **delle proprietà** finestra, si trasformano i dati in proprietà pubbliche che dispongono di due attributi speciali, `Description` e `Category`. `Description` è il testo visualizzato in fondo il **proprietà** finestra. `Category` Determina dove la proprietà deve essere visualizzata quando la **proprietà** finestra viene visualizzata nel **Categorized** visualizzazione. Nell'immagine seguente, il **le proprietà** finestra è in **Categorized** visualizzazione, il **nome** proprietà nel **ToDo Fields** categoria è opzione è selezionata e la descrizione del **nome** proprietà viene visualizzata nella parte inferiore della finestra.  
  
     ![Finestra delle proprietà](../extensibility/media/t5properties.png "T5Properties")  
  
2.  Aggiungere quanto segue usando istruzioni il *TodoItem.cs* file.  
  
    ```csharp  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Aggiungere il `public` modificatore di accesso per la dichiarazione di classe.  
  
    ```csharp  
    public class TodoItem  
    {  
    }  
    ```  
  
     Aggiungere le due proprietà, `Name` e `DueDate`. Faremo la `UpdateList()` e `CheckForErrors()` in un secondo momento.  
  
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
  
4.  Aggiungere un riferimento al controllo utente privato. Aggiungere un costruttore che accetta il controllo utente e il nome per questo elemento ToDo. Per trovare il valore per `daysAhead`, ottiene la proprietà di pagina di opzioni.  
  
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
  
5.  Perché le istanze del `TodoItem` classe verrà archiviata nella casella di riepilogo e chiamerà la casella di riepilogo il `ToString` funzione, è necessario eseguire l'overload di `ToString` (funzione). Aggiungere il codice seguente a *TodoItem.cs*, dopo il costruttore e prima della fine della classe.  
  
    ```csharp  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6.  Nelle *TodoWindowControl.xaml.cs*, aggiungere i metodi stub per il `TodoWindowControl` classe per il `CheckForError` e `UpdateList` metodi. Inserirli dopo il ProcessDialogChar e prima della fine del file.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     Il `CheckForError` metodo verrà chiamato un metodo che ha lo stesso nome nell'oggetto padre, e tale metodo controllerà se tutti gli errori si sono verificati e gestiscono in modo corretto. Il `UpdateList` metodo aggiornerà la casella di riepilogo nel controllo padre; il metodo viene chiamato quando il `Name` e `DueDate` proprietà in questa modifica di classe. Vengono implementati in un secondo momento.  
  
## <a name="integrate-into-the-properties-window"></a>Integrare la finestra proprietà  
 Scrivere ora il codice che gestisce la casella di riepilogo che sarà associato ai **proprietà** finestra.  
  
 È necessario modificare il pulsante di fare clic sul gestore di leggere la casella di testo, creare un elemento TodoItem e lo aggiunge alla casella di riepilogo.  
  
1.  Sostituire il `button1_Click` funzione con il codice che crea un nuovo elemento TodoItem e lo aggiunge alla casella di riepilogo. Chiama `TrackSelection()`, che saranno definiti successivamente.  
  
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
  
2.  Nella visualizzazione Progettazione selezionare il controllo ListBox. Nel **delle proprietà** finestra fare clic sulla **gestori eventi** pulsante e trovare il **SelectionChanged** evento. Nella casella di testo con riempimento **listBox_SelectionChanged**. Questa operazione aggiunge uno stub per un gestore di evento SelectionChanged e lo assegna all'evento.  
  
3.  Implementare il metodo `TrackSelection()`. Poiché è necessario ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> services, è necessario apportare la <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> il TodoWindowControl possono accedervi. Aggiungere il metodo seguente per il `TodoWindow` classe:  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4.  Aggiungere le seguenti istruzioni using riportate *TodoWindowControl.xaml.cs*:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Compilare il gestore dell'evento SelectionChanged come indicato di seguito:  
  
    ```  
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)  
    {  
        TrackSelection();  
    }  
    ```  
  
6.  A questo punto, compilare la funzione TrackSelection, che fornirà l'integrazione con il **proprietà** finestra. Questa funzione viene chiamata quando l'utente aggiunge un elemento alla casella di riepilogo o fa clic su un elemento nella casella di riepilogo. Aggiunge il contenuto della casella di riepilogo per un SelectionContainer e passa SelectionContainer per il **delle proprietà** della finestra <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> gestore dell'evento. Il servizio TrackSelection tiene traccia degli oggetti selezionati nell'interfaccia utente (UI) e le relative proprietà  
  
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
  
     Dopo aver creato una classe che il **delle proprietà** finestra è possibile usare, è possibile integrare il **proprietà** finestra con la finestra degli strumenti. Quando l'utente fa clic su un elemento nella casella di riepilogo nella finestra degli strumenti, il **proprietà** finestra deve essere aggiornata di conseguenza. Analogamente, quando l'utente modifica un elemento ToDo nel **proprietà** finestra, l'elemento associato deve essere aggiornato.  
  
7.  A questo punto, aggiungere il resto del codice funzione UpdateList *TodoWindowControl.xaml.cs*. Dovrebbe eliminare e aggiungere nuovamente l'elemento TodoItem modificata dalla casella di riepilogo.  
  
    ```csharp  
    public void UpdateList(TodoItem item)  
    {  
        var index = listBox.SelectedIndex;  
        listBox.Items.RemoveAt(index);  
        listBox.Items.Insert(index, item);  
        listBox.SelectedItem = index;  
    }  
    ```  
  
8.  Testare il codice. Compilare il progetto e avviare il debug. L'istanza sperimentale dovrebbe essere visualizzato.  
  
9. Aprire il **degli strumenti** > **opzioni** pagina. Verrà visualizzata la categoria di attività nel riquadro sinistro. Le categorie sono elencate in ordine alfabetico, quindi cercare in di Servizi terminal.  
  
10. Nel **Todo** pagina delle opzioni, dovrebbe vedere il `DaysAhead` impostata su **0**. Modificarlo in base ai **2**.  
  
11. Nel **Vista / Windows altri** menu, aprire **TodoWindow**. Tipo di **EndDate** nella casella di testo e fare clic su **Add**.  
  
12. Nella casella di riepilogo dovrebbe essere una data di due giorni successiva alla data odierna.  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Aggiungere il testo della finestra di Output e gli elementi all'elenco attività  
 Per il **elenco attività**, si crea un nuovo oggetto di tipo attività e quindi aggiungere tale oggetto attività per il **elenco attività** chiamando relativo `Add` (metodo). Per scrivere il **Output** finestra, si chiama relativo `GetPane` metodo per ottenere un oggetto di tipo riquadro, quindi chiamare il `OutputString` metodo dell'oggetto riquadro.  
  
1.  In *TodoWindowControl.xaml.cs*, nel `button1_Click` metodo, aggiungere codice per ottenere il **generali** riquadro del **Output** finestra (ovvero l'impostazione predefinita) e la scrittura. Il metodo dovrebbe essere simile al seguente:  
  
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
  
2.  Per aggiungere elementi all'elenco attività, è necessario un per aggiungere una classe nidificata alla classe TodoWindowControl. La classe annidata deve derivare da <xref:Microsoft.VisualStudio.Shell.TaskProvider>. Aggiungere il codice seguente alla fine del `TodoWindowControl` classe.  
  
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
  
3.  Successivamente aggiungere un riferimento a private `TodoTaskProvider` e una `CreateProvider()` metodo per il `TodoWindowControl` classe. Il codice dovrebbe essere simile al seguente:  
  
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
  
4.  Aggiungere `ClearError()`, che svuota l'elenco di attività, e `ReportError()`, che aggiunge una voce all'elenco di attività, al `TodoWindowControl` classe.  
  
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
  
5.  A questo punto implementare i `CheckForErrors` (metodo), come indicato di seguito.  
  
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
  
## <a name="try-it-out"></a>Provalo  
  
1.  Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.  
  
2.  Aprire il **TodoWindow** (**View** > **altri Windows** > **TodoWindow**).  
  
3.  Digitare un valore nella casella di testo e quindi fare clic su **Add**.  
  
     Data scadenza a 2 giorni dopo la data odierna viene aggiunto alla casella di riepilogo. Non vengono generati errori e il **elenco attività** (**View** > **elenco attività**) dovrebbe non presentano alcuna voce.  
  
4.  Modificare ora l'impostazione sul **Tools** > **opzioni** > **ToDo** pagina da **2** a **0**.  
  
5.  Digitare un valore diverso nel **TodoWindow** e quindi fare clic su **Add** nuovamente. Questo modo viene attivato un errore e anche una voce nella **elenco attività**.  
  
     Quando si aggiungono elementi, la data iniziale è impostata al momento più 2 giorni.  
  
6.  Nel **vista** menu, fare clic su **Output** per aprire il **Output** finestra.  
  
     Si noti che ogni volta che si aggiunge un elemento, viene visualizzato un messaggio nel **elenco attività** riquadro.  
  
7.  Fare clic su uno degli elementi nella casella di riepilogo.  
  
     Il **proprietà** finestra vengono visualizzate le due proprietà per l'elemento.  
  
8.  Modificare una delle proprietà e quindi premere **invio**.  
  
     L'elemento viene aggiornato nella ListBox.