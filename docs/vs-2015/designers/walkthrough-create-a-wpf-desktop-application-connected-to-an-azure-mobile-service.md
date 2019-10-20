---
title: "Procedura dettagliata: Creare un'applicazione desktop WPF connessa a un servizio mobile di Azure | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 8d42620f-553b-4b04-a38b-f6b306d73a50
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 624fffb9c86a7ad874f27797dfd5251c8585870f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664031"
---
# <a name="walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service"></a>Procedura dettagliata: Creare un'applicazione desktop WPF connessa a un servizio mobile di Azure
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile usare Windows Presentation Foundation (WPF) per creare rapidamente un'applicazione desktop moderna che usa un servizio mobile di Azure per archiviare e fornire i dati.

## <a name="Requirements"></a> Prerequisiti
 Per completare questa procedura dettagliata, sono necessari gli elementi seguenti:

- Visual Studio 2015: qualsiasi versione che supporta lo sviluppo WPF.

- Un account Microsoft Azure attivo.

  - È possibile iscriversi per un account di prova gratuito [qui](https://azure.microsoft.com/pricing/free-trial/).

  - È possibile attivare i [benefici per sottoscrittori MSDN](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/?WT.mc_id=A261C142F). La sottoscrizione MSDN offre ogni mese dei crediti che è possibile usare per i servizi di Azure a pagamento.

## <a name="create-a-project-and-add-references"></a>Creare un progetto e aggiungere i riferimenti
 Il primo passaggio consiste nel creare un progetto WPF e aggiungere un pacchetto NuGet che consente di connettersi ai servizi mobili di Azure.

#### <a name="to-create-the-project"></a>Per creare il progetto

1. Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.

2. Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Visual C#** o **Visual Basic** e scegliere il nodo **Windows** , quindi espandere il nodo **Windows** e scegliere il nodo **Desktop classico** .

3. Nell'elenco dei modelli scegliere il modello **Applicazione WPF** .

4. Nella finestra di dialogo **Nome** immettere `WPFQuickStart`, quindi scegliere il pulsante **OK** .

     Il progetto viene creato, i file del progetto vengono aggiunti a **Esplora soluzioni**e viene visualizzata la finestra di progettazione per la finestra dell'applicazione predefinita denominata **MainWindow.xaml** .

#### <a name="to-add-a-reference-to-the-windows-azure-mobile-services-sdk"></a>Per aggiungere un riferimento a Servizi mobili di Windows Azure SDK

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo **Riferimenti** e scegliere **Gestisci pacchetti NuGet**.

2. Nella finestra di dialogo **Gestione pacchetti NuGet**scegliere il campo **Cerca** e immettere `mobileservices`.

3. Nel riquadro sinistro scegliere **WindowsAzure.MobileServices**, quindi nel riquadro destro scegliere il pulsante **Installa** .

    > [!NOTE]
    > Se viene visualizzata la finestra **Anteprima** , esaminare le modifiche proposte, quindi scegliere il pulsante **OK** .

4. Nella finestra di dialogo di **accettazione della licenza** esaminare le condizioni di licenza e quindi accettarle scegliendo il pulsante **Accetto** .

     In **Esplora soluzioni**verranno aggiunti i riferimenti necessari.

    > [!NOTE]
    > Se non si accettano le condizioni di licenza, scegliere il pulsante **Non accetto** . Non sarà possibile completare il resto della procedura dettagliata.

## <a name="create-the-user-interface"></a>Creare l'interfaccia utente
 Il passaggio successivo consiste nel creare l'interfaccia utente per l'applicazione. Verrà creato prima di tutto un controllo utente riutilizzabile che visualizza un layout affiancato standard a due riquadri. Il controllo utente verrà quindi aggiunto alla finestra principale dell'applicazione e verranno aggiunti anche i controlli per immettere e visualizzare i dati, infine verrà scritto il codice per definire l'interazione con il back-end del servizio mobile.

#### <a name="to-add-a-user-control"></a>Per aggiungere un controllo utente

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo **WPFQuickStart** e scegliere **Aggiungi**, **Nuova cartella**.

2. Denominare la cartella `Common`.

3. Aprire il menu di scelta rapida per la cartella **Common** e scegliere **Aggiungi**, **Controllo utente**.

4. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere il campo Nome e immettere `QuickStartTask`, quindi scegliere il pulsante **Aggiungi** .

     Il controllo utente verrà aggiunto al progetto e il file **QuickStartTask.xaml** verrà aperto nella finestra di progettazione.

5. Nel riquadro inferiore della finestra di progettazione selezionare i tag `<Grid>` e `</Grid>` e sostituirli con il codice XAML seguente:

    ```xaml
    <Grid VerticalAlignment="Top">
            <StackPanel Orientation="Horizontal">
                <Border BorderThickness="0,0,1,0" BorderBrush="DarkGray" Margin="0,10" MinWidth="70">
                    <TextBlock Text="{Binding Number}" FontSize="45" Foreground="DarkGray" Margin="20,0"/>
                </Border>
                <StackPanel>
                    <TextBlock Text="{Binding Title}" Margin="10,10,0,0" FontSize="16" FontWeight="Bold" />
                    <TextBlock Text="{Binding Description}" Margin="10,0,0,0" TextWrapping="Wrap" MaxWidth="500" />
                </StackPanel>
            </StackPanel>
        </Grid>
    ```

     Questo codice XAML crea un layout riutilizzabile con i segnaposto per i campi numero, titolo e descrizione. In fase di esecuzione i segnaposti possono essere sostituiti con un testo come illustrato nella figura seguente.

     ![Controllo utente QuickStartTask](../designers/media/wpfquickstart1.PNG "WPFQuickStart1")

6. In **Esplora soluzioni**espandere il nodo **QuickStartTask.xaml** e aprire il file **QuickStartTask.xaml.cs** o **QuickStartTask.xaml.vb** .

7. Nell'editor del codice sostituire lo spazio dei nomi `namespace WPFQuickStart.Common` (C#) o il metodo `Public Class QuickStartTask` (VB) con il codice seguente:

    ```csharp
    namespace WPFQuickStart.Common
    {
        /// <summary>
        /// Interaction logic for QuickStartTask.xaml
        /// </summary>
        public partial class QuickStartTask : UserControl
        {
            public QuickStartTask()
            {
                this.InitializeComponent();
                this.DataContext = this;
            }

            public int Number
            {
                get { return (int)GetValue(NumberProperty); }
                set { SetValue(NumberProperty, value); }
            }

            // Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...
            public static readonly DependencyProperty NumberProperty =
                DependencyProperty.Register("Number", typeof(int), typeof(QuickStartTask), new PropertyMetadata(0));

            public string Title
            {
                get { return (string)GetValue(TitleProperty); }
                set { SetValue(TitleProperty, value); }
            }

            // Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...
            public static readonly DependencyProperty TitleProperty =
                DependencyProperty.Register("Title", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));

            public string Description
            {
                get { return (string)GetValue(DescriptionProperty); }
                set { SetValue(DescriptionProperty, value); }
            }

            // Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...
            public static readonly DependencyProperty DescriptionProperty =
                DependencyProperty.Register("Description", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));
        }
    }
    ```

    ```vb
    Partial Public Class QuickStartTask
            Inherits UserControl

            Public Sub New()
                Me.InitializeComponent()
                Me.DataContext = Me
            End Sub

            Public Property Number() As Integer
                Get
                    Return CInt(Fix(GetValue(NumberProperty)))
                End Get
                Set(ByVal value As Integer)
                    SetValue(NumberProperty, value)
                End Set
            End Property

            ' Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...
            Public Shared ReadOnly NumberProperty As DependencyProperty = DependencyProperty.Register("Number", GetType(Integer), GetType(QuickStartTask), New PropertyMetadata(0))

            Public Property Title() As String
                Get
                    Return CStr(GetValue(TitleProperty))
                End Get
                Set(ByVal value As String)
                    SetValue(TitleProperty, value)
                End Set
            End Property

            ' Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...
            Public Shared ReadOnly TitleProperty As DependencyProperty = DependencyProperty.Register("Title", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))

            Public Property Description() As String
                Get
                    Return CStr(GetValue(DescriptionProperty))
                End Get
                Set(ByVal value As String)
                    SetValue(DescriptionProperty, value)
                End Set
            End Property

            ' Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...
            Public Shared ReadOnly DescriptionProperty As DependencyProperty = DependencyProperty.Register("Description", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))
        End Class
    ```

     Questo codice usa le proprietà di dipendenza per impostare i valori per i campi numero, titolo e descrizione in fase di esecuzione.

8. Nella barra dei menu scegliere **Compila**, **Compila WPFQuickStart** per compilare il controllo utente.

#### <a name="to-create-and-modify-the-main-window"></a>Per creare e modificare la finestra principale

1. In **Esplora soluzioni**aprire il file **MainWindow.xaml** .

2. **Importante**: questo passaggio è solo per C#. Se si usa Visual Basic, andare al passaggio successivo. Nel riquadro inferiore della finestra di progettazione trovare la riga `xmlns:local=”clr-namespace:WPFQuickStart”` e sostituirla con il codice XAML seguente:

    ```xaml
    xmlns:local=”clr-namespace:WPFQuickStart.Common”
    ```

3. Nella finestra di dialogo **Proprietà** espandere il nodo della categoria **Common** e scegliere la proprietà **Title** , quindi immettere `WPF Todo List` e premere **INVIO** .

     L'elemento **Title** nella finestra XAML viene modificato per corrispondere al nuovo valore. È possibile modificare le proprietà XAML nella finestra XAML o **Proprietà** e le modifiche risulteranno sincronizzate.

4. Nella finestra XAML impostare il valore dell'elemento **Height** su `768`e il valore della proprietà **Width** su `1280`.

     Questi elementi corrispondono alle proprietà **Height** e **Width** della categoria **Layout** nella finestra **Proprietà** .

5. Selezionare i tag `<Grid>` e `</Grid>` e sostituirli con il codice XAML seguente:

    ```xaml
    <Grid>

            <Grid Margin="50,50,10,10">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="*" />
                </Grid.ColumnDefinitions>
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="*" />
                </Grid.RowDefinitions>

                <Grid Grid.Row="0" Grid.ColumnSpan="2" Margin="0,0,0,20">
                    <StackPanel>
                        <TextBlock Foreground="#0094ff" FontFamily="Segoe UI Light" Margin="0,0,0,6">MICROSOFT AZURE MOBILE SERVICES</TextBlock>
                        <TextBlock Foreground="Gray" FontFamily="Segoe UI Light" FontSize="45" ><Run Text="My Todo List"/></TextBlock>
                    </StackPanel>
                </Grid>

                <Grid Grid.Row="1">
                    <StackPanel>

                        <local:QuickStartTask Number="1" Title="Insert a TodoItem" Description="Enter some text below and click Save to insert a new todo item into the list." />

                        <StackPanel Orientation="Horizontal" Margin="72,0,0,0">
                            <TextBox x:Name="TodoInput" Margin="5" MinWidth="300"/>
                            <Button x:Name="ButtonSave" Click="ButtonSave_Click" Content="Save"/>
                        </StackPanel>

                    </StackPanel>
                </Grid>

                <Grid Grid.Row="1" Grid.Column="1">
                    <Grid.RowDefinitions>
                        <RowDefinition Height="Auto" />
                        <RowDefinition />
                    </Grid.RowDefinitions>
                    <StackPanel>
                        <local:QuickStartTask Number="2" Title="Query and Update Data" Description="Click the Refresh button to load the unfinished TodoItems from the Azure Mobile Service. Select the checkbox to mark a ToDo item as complete and update the list." />
                        <Button Margin="72,0,0,0" Name="ButtonRefresh" Click="ButtonRefresh_Click">Refresh</Button>
                    </StackPanel>

                    <ListView Name="ListItems" Margin="62,10,0,0" Grid.Row="1">
                        <ListView.ItemTemplate>
                            <DataTemplate>
                                <StackPanel Orientation="Horizontal">
                                    <CheckBox Name="CheckBoxComplete" IsChecked="{Binding Complete, Mode=TwoWay}" Checked="CheckBoxComplete_Checked" Content="{Binding Text}" Margin="10,5" VerticalAlignment="Center"/>
                                </StackPanel>
                            </DataTemplate>
                        </ListView.ItemTemplate>
                    </ListView>

                </Grid>

            </Grid>
        </Grid>
    ```

     Le modifiche si riflettono nella finestra di progettazione. Anche in questo caso l'interfaccia utente potrebbe essere stata definita aggiungendo i controlli dalla finestra **Casella degli strumenti** e impostando le proprietà nella finestra **Proprietà** . Tutto ciò che può essere eseguito nella finestra di progettazione può essere eseguito nel codice XAML e viceversa.

     A questo punto, la progettazione dovrebbe essere simile alla figura seguente.

     ![MainWindow nella finestra di progettazione](../designers/media/wpfquickstart2.PNG "WPFQuickStart2")

    > [!NOTE]
    > Seguendo le procedure successive è possibile che vengano visualizzati alcuni errori nell' **Elenco errori** se è aperto. Non c'è però da preoccuparsi perché tali errori non verranno più visualizzati al termine delle procedure rimanenti.

6. In **Esplora soluzioni**espandere il nodo **MainWindow.xaml** e aprire il file **MainWindow.xaml.cs** o **MainWindow.xaml.vb** .

7. Nell'editor del codice aggiungere le direttive `using` o `Imports` seguenti all'inizio del file:

    ```csharp
    using Microsoft.WindowsAzure.MobileServices;
    using Newtonsoft.Json;
    ```

    ```vb
    Imports Microsoft.WindowsAzure.MobileServices
    Imports Newtonsoft.Json
    ```

8. Sostituire tutto il codice nello spazio dei nomi **WPFQuickStart** (C#) o nella classe **Class MainWindow** (VB) con il codice seguente:

    ```csharp
    namespace WPFQuickStart
    {
        /// <summary>
        /// Interaction logic for MainWindow.xaml
        /// </summary>
        public class TodoItem
        {
            public string Id { get; set; }

            [JsonProperty(PropertyName = "text")]
            public string Text { get; set; }

            [JsonProperty(PropertyName = "complete")]
            public bool Complete { get; set; }
        }

        public partial class MainWindow : Window
        {
            private MobileServiceCollection<TodoItem, TodoItem> items;
            private IMobileServiceTable<TodoItem> todoTable = App.MobileService.GetTable<TodoItem>();

            public MainWindow()
            {
                InitializeComponent();
            }

            private async void InsertTodoItem(TodoItem todoItem)
            {
                // This code inserts a new TodoItem into the database. When the operation completes
                // and Mobile Services has assigned an Id, the item is added to the CollectionView
                await todoTable.InsertAsync(todoItem);
                items.Add(todoItem);
            }

            private async void RefreshTodoItems()
            {
                try
                {
                    // This code refreshes the entries in the list view by querying the TodoItem table.
                    // The query excludes completed TodoItems
                    items = await todoTable
                        .Where(todoItem => todoItem.Complete == false)
                        .ToCollectionAsync();
                    ListItems.ItemsSource = items;
                }
                catch (MobileServiceInvalidOperationException e)
                {
                    MessageBox.Show(e.Message, "Error loading items");
                }
            }

            private async void UpdateCheckedTodoItem(TodoItem item)
            {
                // This code takes a freshly completed TodoItem and updates the database. When the MobileService
                // responds, the item is removed from the list
                await todoTable.UpdateAsync(item);
                items.Remove(item);
            }

            private void ButtonRefresh_Click(object sender, RoutedEventArgs e)
            {
                RefreshTodoItems();
            }

            private void ButtonSave_Click(object sender, RoutedEventArgs e)
            {
                var todoItem = new TodoItem { Text = TodoInput.Text };
                InsertTodoItem(todoItem);
                TodoInput.Text = "";
            }

            private void CheckBoxComplete_Checked(object sender, RoutedEventArgs e)
            {
                CheckBox cb = (CheckBox)sender;
                TodoItem item = cb.DataContext as TodoItem;
                UpdateCheckedTodoItem(item);
            }

            protected override void OnActivated(EventArgs e)
            {
                RefreshTodoItems();
            }
        }

    }
    ```

    ```vb
    Public Class TodoItem
        Public Property Id() As String

        <JsonProperty(PropertyName:="text")>
        Public Property Text() As String

        <JsonProperty(PropertyName:="complete")>
        Public Property Complete() As Boolean
    End Class

    Partial Public Class MainWindow
        Inherits Window

        Private items As MobileServiceCollection(Of TodoItem, TodoItem)
        Private todoTable As IMobileServiceTable(Of TodoItem) = Application.MobileService.GetTable(Of TodoItem)()

        Public Sub New()
            InitializeComponent()
        End Sub

        Private Async Sub InsertTodoItem(ByVal todoItem As TodoItem)
            ' This code inserts a new TodoItem into the database. When the operation completes
            ' and Mobile Services has assigned an Id, the item is added to the CollectionView
            Await todoTable.InsertAsync(todoItem)
            items.Add(todoItem)
        End Sub

        Private Async Sub RefreshTodoItems()
            Dim exception As MobileServiceInvalidOperationException = Nothing
            Try
                ' This code refreshes the entries in the list view by querying the TodoItem table.
                ' The query excludes completed TodoItems
                items = Await todoTable.Where(Function(todoItem) todoItem.Complete = False).ToCollectionAsync()
            Catch e As MobileServiceInvalidOperationException
                exception = e
            End Try

            If exception IsNot Nothing Then
                MessageBox.Show(exception.Message, "Error loading items")
            Else
                ListItems.ItemsSource = items
            End If
        End Sub

        Private Async Sub UpdateCheckedTodoItem(ByVal item As TodoItem)
            ' This code takes a freshly completed TodoItem and updates the database. When the MobileService
            ' responds, the item is removed from the list
            Await todoTable.UpdateAsync(item)
            items.Remove(item)
        End Sub

        Private Sub ButtonRefresh_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
            RefreshTodoItems()
        End Sub

        Private Sub ButtonSave_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
            Dim todoItem = New TodoItem With {.Text = TodoInput.Text}
            InsertTodoItem(todoItem)
            TodoInput.Text = ""
        End Sub

        Private Sub CheckBoxComplete_Checked(ByVal sender As Object, ByVal e As RoutedEventArgs)
            Dim cb As CheckBox = DirectCast(sender, CheckBox)
            Dim item As TodoItem = TryCast(cb.DataContext, TodoItem)
            UpdateCheckedTodoItem(item)
        End Sub

        Protected Overrides Sub OnActivated(ByVal e As EventArgs)
            RefreshTodoItems()
        End Sub
    End Class
    ```

     Questo codice definisce l'interazione tra l'interfaccia utente e il database nel servizio mobile usando i metodi asincroni.

## <a name="create-the-azure-mobile-service"></a>Creare il servizio mobile di Azure
 Il passaggio finale consiste nel creare un servizio mobile in Microsoft Azure, aggiungere una tabella per archiviare i dati e quindi fare riferimento all'istanza del servizio dall'applicazione.

#### <a name="to-create-a-mobile-service"></a>Per creare un servizio mobile

1. Aprire un Web browser e accedere al portale di Microsoft Azure, quindi scegliere la scheda **SERVIZI MOBILI** .

2. Scegliere il pulsante **NUOVO** e nella finestra di dialogo popup scegliere **CALCOLO**, **SERVIZIO MOBILE, CREA**.

3. Nella finestra di dialogo **NUOVO SERVIZIO MOBILE** scegliere la casella di testo **URL** e immettere `wpfquickstart01`.

    > [!NOTE]
    > Potrebbe essere necessario modificare la parte numerica dell'URL. Microsoft Azure richiede un URL univoco per ogni servizio mobile.

     In questo modo l'URL per il servizio verrà impostato su `https://wpfquickstart01.azure-mobile.net/`.

4. Nell'elenco **DATABASE** scegliere un'opzione di database. Poiché si tratta di un'applicazione che probabilmente non sarà molto usata, è possibile scegliere l'opzione **Crea un database SQL 20 MB gratuito** o scegliere il database gratuito già associato alla sottoscrizione.

5. Nell'elenco **AREA** scegliere il data center in cui si vuole distribuire il servizio mobile e quindi scegliere il pulsante **Avanti** (freccia destra).

    > [!NOTE]
    > Per questo servizio verrà usata l'impostazione predefinita di **BACK-END** , **JavaScript**.

6. Se si sta creando un nuovo database, nell'elenco **SERVER** della pagina **Specifica impostazioni di database** scegliere **Nuovo server di database SQL**, immettere un **NOME DI ACCESSO SQL** e una **PASSWORD**, quindi scegliere il pulsante **Completa** (segno di spunta).

7. Se si sceglie un database esistente, nella pagina **Impostazioni database** immettere una **PASSWORD DI ACCESSO** e quindi scegliere il pulsante **Completa** (segno di spunta).

     Avrà inizio il processo di creazione del servizio mobile. Una volta completato il processo, lo stato verrà modificato in **Pronto** e sarà possibile procedere con il passaggio successivo.

8. Nel portale selezionare il servizio mobile appena creato, quindi scegliere il pulsante **GESTISCI CHIAVI** .

9. Nella finestra di dialogo **Gestisci chiavi di accesso** copiare la **CHIAVE APPLICAZIONE**.

     Tale chiave verrà usata nella procedura successiva.

#### <a name="to-create-a-table"></a>Per creare una tabella

1. Nel portale di Microsoft Azure scegliere la freccia destra accanto al nome del servizio mobile e nella barra dei menu scegliere **DATI**, quindi scegliere il collegamento **AGGIUNGI UNA TABELLA** .

2. Nella finestra di dialogo **NOME TABELLA** della finestra di dialogo **Crea nuova tabella** immettere `TodoItem`, quindi scegliere il pulsante **Completa** (segno di spunta).

     Attendere la creazione della tabella e quindi continuare con la procedura finale.

#### <a name="to-add-a-declaration-for-the-mobile-service"></a>Per aggiungere una dichiarazione per il servizio mobile

1. Tornare a Visual Studio. In **Esplora soluzioni**espandere il nodo **App.xaml** (C#) o **Application.xaml** (Visual Basic) e aprire il file **App.xaml.cs** o **App.xaml.vb** .

2. Nell'editor del codice aggiungere le direttive `using` o **Imports** seguenti all'inizio del file:

    ```csharp
    using Microsoft.WindowsAzure.MobileServices;
    ```

    ```vb
    Imports Microsoft.WindowsAzure.MobileServices
    ```

3. Aggiungere la dichiarazione seguente alla classe, sostituendo *YOUR-SERVICE_HERE* con il nome dell'URL per il servizio e sostituendo *YOUR-KEY-HERE* con la chiave dell'applicazione copiata nella procedura precedente:

    ```csharp
    public static MobileServiceClient MobileService = new MobileServiceClient(
                 "https://YOUR-SERVICE-HERE.azure-mobile.net/",
                 "YOUR-KEY-HERE"
             );
    ```

    ```vb
    Public Shared MobileService As New MobileServiceClient("https://YOUR-SERVICE-HERE.azure-mobile.net/", "YOUR-KEY-HERE")
    ```

     Questo codice consente all'applicazione di accedere al servizio mobile in esecuzione in Microsoft Azure.

## <a name="test-the-application"></a>Testare l'applicazione
 La procedura è stata completata. È stata creata un'applicazione desktop WPF con accesso a un servizio mobile di Azure. A questo punto è possibile eseguire l'applicazione e provarla.

#### <a name="to-run-the-application"></a>Per eseguire l'applicazione

1. Nella barra dei menu scegliere **Debug**, **Avvia debug** (o premere F5).

2. Nella finestra di dialogo **Insert a TodoItem** immettere `Do something`, quindi scegliere il pulsante **Salva** .

3. INVIO `Do something else`, quindi scegliere il pulsante **Salva** .

     Verranno aggiunte due voci per l'elenco **Query and Update Data** , come illustrato nella figura seguente.

     ![Gli elementi todo vengono aggiunti all'elenco.](../designers/media/wpfquickstart3.PNG "WPFQuickStart3")

4. Selezionare la casella di controllo per la voce **Do something else** nell'elenco.

     In questo modo viene chiamato il metodo **UpdateCheckedTodoItem** e viene rimosso l'elemento sia dall'elenco che dal database.

## <a name="next-steps"></a>Passaggi successivi
 È stato completato un esempio abbastanza generico di un'applicazione desktop WPF con un back-end di Azure. Naturalmente, è probabile che un'applicazione reale sia molto più complessa, ma si applicano gli stessi concetti di base. Vedere [WPF in .NET Framework](https://msdn.microsoft.com/library/ms754130\(v=vs.100\).aspx).

 È possibile rendere più interessante l'interfaccia utente mediante l'aggiunta di colore, forme, elementi grafici e persino animazioni. Vedere [Progettazione di XAML in Visual Studio e Blend per Visual Studio](../designers/designing-xaml-in-visual-studio.md).

 È possibile connettersi ai database SQL esistenti o ad altre origini dei dati mediante i servizi mobili di Azure. Vedere la [documentazione dei servizi mobili](https://azure.microsoft.com/services/app-service/mobile/).

## <a name="see-also"></a>Vedere anche
 [Procedura dettagliata: la prima applicazione desktop WPF](../designers/walkthrough-my-first-wpf-desktop-application2.md) [Crea applicazioni desktop moderne con Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)
