---
title: Creare un'applicazione dati semplice con WPF ed Entity Framework 6 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 56c211597e99689e1ad263cfe12d7dafdf3cf5cc
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001559"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Creare un'applicazione dati semplice con WPF ed Entity Framework 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Questa procedura dettagliata viene illustrato come creare un'applicazione di base "Form over data" in Visual Studio con SQL Server Local DB, il database Northwind, Entity Framework 6 e Windows Presentation Foundation. Viene illustrato come eseguire l'associazione dati di base con una visualizzazione master-Details e include anche uno personalizzato "associazione strumento di navigazione" con i pulsanti per "Move Next", "Sposta precedente," "Sposta all'inizio," "Sposta alla fine," "Aggiornamento" ed "Elimina".  
  
 Questo articolo è incentrato sull'uso degli strumenti dati in Visual Studio e non tenta di spiegare le tecnologie sottostanti in qualsiasi livello di nidificazione. Si presuppone di avere una certa conoscenza di base con XAML, Entity Framework e SQL. In questo esempio illustra anche architettura MVVM, ovvero standard per le applicazioni WPF. Tuttavia, è possibile copiare questo codice in un'applicazione MVVM con pochissime modifiche.  
  
## <a name="install-and-connect-to-northwind"></a>Installare e connettersi a Northwind  
 Questo esempio Usa il database di esempio Northwind e SQL Server Express LocalDB. Dovrebbe funzionare con altri prodotti di database SQL anche se il provider di dati ADO.NET per il prodotto supporta Entity Framework.  
  
1.  Se hai già fatto, installare SQL Server 2014 LocalDB Express a 32 bit dal [pagina di download edizioni di SQL Server](https://www.microsoft.com/sql-server/sql-server-editions-express).  
  
2.  Installare il database di esempio Northwind, seguendo le istruzioni riportate qui: [Installare SQL Server database di esempio](../data-tools/install-sql-server-sample-databases.md).  
  
3.  [Aggiungere nuove connessioni](../data-tools/add-new-connections.md) per Northwind.  
  
## <a name="configure-the-project"></a>Configurare il progetto  
  
1.  In Visual Studio, scegliere **File &#124; nuovo progetto** e quindi creare una nuova applicazione WPF in c#.  
  
2.  Successivamente si aggiungerà il pacchetto NuGet di Entity Framework 6. In Esplora soluzioni selezionare il nodo del progetto. Nel menu principale, scegliere **progetto &#124; Gestisci pacchetti NuGet...**  
  
     ![Gestire la voce di menu pacchetti NuGet](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")  
  
3.  In Gestione pacchetti NuGet, fare clic sui **esplorare** collegamento. Entity Framework è probabile che il pacchetto superiore nell'elenco. Fare clic su **installare** nel riquadro destro e seguire le istruzioni. La finestra di Output indicherà al termine dell'installazione.  
  
     ![Pacchetto NuGet di Entity Framework](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")  
  
4.  A questo punto è possibile usare Visual Studio per creare un modello basato sul database Northwind.  
  
## <a name="create-the-model"></a>Creare il modello  
  
1. Fare clic con il pulsante destro sul nodo del progetto in Esplora soluzioni e scegliere **Aggiungi &#124; nuovo elemento**. Nel riquadro di sinistra, sotto il nodo c#, scegliere **Data** nel riquadro centrale scegliere **ADO.NET Entity Data Model**.  
  
    ![Entity Framework modello nuovo elemento di progetto](../data-tools/media/raddata-ef-new-project-item.png "raddata nuovo elemento di progetto Entity Framework")  
  
2. Chiamare il modello `Northwind_model` e scegliere OK. Verrà visualizzata la **procedura guidata Entity Data Model**. Scegli **Entity Framework Designer dal database** e quindi fare clic su **successivo**.  
  
    ![Modello EF da Database](../data-tools/media/raddata-ef-model-from-database.png "raddata modello EF da Database")  
  
3. Nella schermata successiva, scegliere di LocalDB Northwind connessione fare clic su **successivo**.  
  
4. Nella pagina successiva della procedura guidata, è scegliere quali tabelle, stored procedure e altri oggetti di database da includere nel modello di Entity Framework. Espandere il nodo dbo nella visualizzazione albero e scegliere i clienti, ordini e dettagli dell'ordine. Lasciare le impostazioni predefinite selezionate e fare clic su **fine**.  
  
    ![Scegli oggetti di database per il modello](../data-tools/media/raddata-choose-ef-objects.png "raddata Scegli oggetti di Entity Framework")  
  
5. La procedura guidata genera le classi di c# che rappresentano il modello di Entity Framework. Questi sono plain precedente le classi di c# e sono ciò che si eseguirà il metodo databind all'interfaccia utente WPF. Il file con estensione edmx vengono descritte le relazioni e altri metadati che associa le classi di oggetti nel database.  I file con estensione tt sono modelli T4 che generano il codice che operano sul modello e salvare le modifiche al database. È possibile visualizzare tutti i file in Esplora soluzioni sotto il nodo Northwind_model:  
  
    ![File del modello EF di Esplora soluzioni](../data-tools/media/raddata-solution-explorer-ef-model-files.png "raddata i file del modello EF di Esplora soluzioni")  
  
    Area di progettazione per il file con estensione edmx consente di modificare alcune proprietà e relazioni nel modello. Non si intende utilizzare la finestra di progettazione in questa procedura dettagliata.  
  
6. I file con estensione tt sono per utilizzo generico ed è necessario modificare uno di essi per lavorare con il Data Binding WPF, che richiede ObservableCollections.  In Esplora soluzioni espandere il nodo Northwind_model fino a individuare Northwind_model.tt. (Assicurarsi di essere **non** nel *. Contesto file con estensione tt che è direttamente sotto il file con estensione edmx).  
  
   -   Sostituire le due occorrenze della <xref:System.Collections.ICollection> con <xref:System.Collections.ObjectModel.ObservableCollection%601>.  
  
   -   Sostituire la prima occorrenza di <xref:System.Collections.Generic.HashSet%601> con <xref:System.Collections.ObjectModel.ObservableCollection%601> intorno alla riga 51. Non sostituire la seconda occorrenza della HashSet  
  
   -   Sostituire l'unica occorrenza di <xref:System.Collections.Generic> (intorno alla riga 334) con <xref:System.Collections.ObjectModel>.  
  
7. Premere **Ctrl + MAIUSC + B** per compilare il progetto. Al termine della compilazione, le classi del modello sono visibili per la creazione guidata origine dati.  
  
   A questo punto siamo pronti collegare questo modello per la pagina XAML in modo che sia possibile visualizzare, esplorare e modificare i dati.  
  
## <a name="databind-the-model-to-the-xaml-page"></a>Metodo DataBind il modello per la pagina XAML  
 È possibile scrivere il codice di associazione dati, ma è molto più semplice consentire a Visual Studio di eseguire questa operazione automaticamente.  
  
1.  Dal menu principale, scegliere **progetto &#124; Aggiungi nuova origine dati** per visualizzare il **configurazione guidata origine dati**. Scegli **oggetto** perché viene eseguita l'associazione per le classi del modello, non al database:  
  
     ![Configurazione guidata origine dati con l'origine dell'oggetto](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "raddata configurazione guidata origine dati con origine oggetto")  
  
2.  Selezionare dei clienti.  (Origini per gli ordini di verranno automaticamente generate dalla proprietà di navigazione ordini cliente.)  
  
     ![Aggiungere le classi di entità come origini dati](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata Add entity classi come origini dati")  
  
3.  Fare clic su **fine**  
  
4.  Passare al file MainWindow. XAML nella visualizzazione codice. Si intende mantenere semplice il XAML ai fini di questo esempio. Modificare il titolo della finestra principale con un nome più descrittivo e aumentare l'altezza e larghezza a 800 x 600 per il momento. È possibile sempre modificarlo in un secondo momento. Aggiungi ora le definizioni di tre righe alla griglia principale, una riga per i pulsanti di navigazione, uno per i dettagli del cliente, uno per la griglia che mostra gli ordini:  
  
    ```xaml  
    <Grid.RowDefinitions>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="*"/>  
           </Grid.RowDefinitions>  
    ```  
  
5.  Ora aprire MainWindow. XAML in modo che venga visualizzato nella finestra di progettazione. In questo modo la finestra Origini dati vengono visualizzati come un'opzione per il margine della finestra di Visual Studio accanto alla casella degli strumenti. Fare clic sulla scheda per aprire la finestra, oppure premere else **Maiusc + Alt + D** oppure scegliere **visualizzazione &#124; Other Windows &#124; Zdroje dat**. Si intende visualizzare ogni proprietà nella classe di clienti nella propria casella di testo singola. Prima di tutto fare clic sulla freccia nella casella combinata dei clienti e scegliere **dettagli**. Trascinare quindi il nodo nella parte centrale dell'area di progettazione in modo che conosca la finestra di progettazione che si vuole eseguirla nella riga centrale.  Se si smarrisce il, è possibile specificare la riga manualmente in seguito nel XAML. Per impostazione predefinita, i controlli vengono posizionati verticalmente in un elemento griglia ma a questo punto è possibile disporle nel modo desiderato del form.  Ad esempio, si potrebbe avere senso inserire una casella di testo nome nella parte superiore, sopra l'indirizzo. L'applicazione di esempio per questo articolo riordina i campi e li Riordina in due colonne.  
  
     ![Associazione dell'origine dati ai clienti sui singoli controlli](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "associazione all'origine dati ai clienti raddata sui singoli controlli")  
  
     Nella visualizzazione codice, è ora possibile visualizzare un nuovo `Grid` nella riga 1 (la riga intermedia) dell'elemento padre della griglia. L'elemento padre della griglia è una `DataContext` attributo che fa riferimento a cui è stato aggiunto a CollectionViewSource la `Windows.Resources` elemento. Dato tale contesto di dati, quando la prima casella di testo, ad esempio, viene associato a tale nome "Address" viene mappato al `Address` proprietà nell'oggetto `Customer` oggetto in CollectionViewSource.  
  
    ```xaml  
    <Grid DataContext="{StaticResource customerViewSource}">  
    ```  
  
6.  Quando un cliente è visibile nella parte superiore della finestra, si vuole vedere metà dello spazio relativi ordini nella parte inferiore. Vi mostreremo gli ordini in un controllo di visualizzazione griglia singolo. Data Binding master-details funzionare come previsto, è importante che viene eseguita l'associazione alla proprietà ordini nella classe di clienti, non per il nodo di ordini separato. Prestare attenzione a quanto illustrato di seguito. Trascinare la proprietà Orders della classe di clienti nella metà inferiore del form, in modo che la finestra di progettazione inserisce nella riga 2:  
  
     ![Trascinare le classi di ordini in formato griglia](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata ordini trascinare classi come griglia")  
  
7.  Visual Studio ha generato tutto il codice di associazione che si connette i controlli dell'interfaccia utente per gli eventi del modello. È necessario eseguire, per visualizzare alcuni dati, è sufficiente scrivere il codice per popolare il modello. Prima si passare per MainWindow.xaml.cs e aggiungere un membro dati alla classe MainWindow per il contesto dei dati. Questo oggetto, che è stato generato automaticamente, agisce qualcosa di simile a un controllo che tiene traccia delle modifiche e gli eventi del modello. Mentre noi siamo qui, aggiungiamo due membri che verranno utilizzate in un secondo momento per aggiungere un nuovo cliente o un nuovo ordine. Viene anche aggiunto la logica di inizializzazione del costruttore. La parte superiore della nostra classe dovrebbe essere simile al seguente:  
  
    ```csharp  
    public partial class MainWindow : Window  
       {  
           public Customer newCustomer { get; set; }  
           public Order newOrder { get; set; }  
  
           NorthwindEntities context = new NorthwindEntities();  
           CollectionViewSource custViewSource;  
           CollectionViewSource ordViewSource;  
  
           public MainWindow()  
           {  
               InitializeComponent();  
               newCustomer = new Customer();  
               newOrder = new Order();  
               custViewSource = ((CollectionViewSource)  
                   (FindResource("customerViewSource")));  
               ordViewSource = ((CollectionViewSource)  
                   (FindResource("customerOrdersViewSource")));  
               DataContext = this;  
           }  
    ```  
  
     Aggiungere un `using` direttiva Data. Entity portare il metodo di estensione Load nell'ambito:  
  
    ```csharp  
    using System.Data.Entity;  
    ```  
  
     Ora scorrere verso il basso e trovare il gestore dell'evento Window_Loaded. Si noti che Visual Studio ha aggiunto un oggetto CollectionViewSource per noi. Questo rappresenta l'oggetto NorthwindEntities selezionato quando è stato creato il modello. È possibile aggiungere codice al Window_loaded in modo che l'intero metodo il seguente aspetto:  
  
    ```csharp  
    private void Window_Loaded(object sender, RoutedEventArgs e)  
        {  
            // Load is an extension method on IQueryable,    
            // defined in the System.Data.Entity namespace.   
            // This method enumerates the results of the query,    
            // similar to ToList but without creating a list.   
            // When used with Linq to Entities this method    
            // creates entity objects and adds them to the context.   
            context.Customers.Load();  
  
            // After the data is loaded call the DbSet<T>.Local property    
            // to use the DbSet<T> as a binding source.   
            custViewSource.Source = context.Customers.Local;  
        }  
    ```  
  
8.  Premere **F5**. Si dovrebbero vedere i dettagli per il cliente prima che è stato recuperato l'oggetto CollectionViewSource e relativi ordini nella griglia dei dati. Non è grande, quindi, correggiamo che la formattazione. e creare un modo per visualizzare gli altri record ed eseguire operazioni CRUD di base.  
  
## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Modificare la progettazione della pagina e aggiungere le griglie per i nuovi clienti e ordini  
 La disposizione predefinita del prodotto da Visual Studio non è ideale per la nostra applicazione, pertanto abbiamo verranno apportate alcune modifiche manualmente nel XAML. È necessario anche alcuni "Form" (che sono effettivamente griglie) per consentire all'utente aggiungere un nuovo cliente o un nuovo ordine.    Per poter aggiungere un nuovo cliente e ordine, è necessario un set separato di caselle di testo che non sono associati a dati per il `CollectionViewSource`. Verrà controllata cui griglia viene visualizzato in qualsiasi momento impostando la proprietà Visible nei metodi del gestore.  
  
 Infine, si aggiungerà un pulsante di eliminazione a ogni riga della griglia di ordini per consentire agli utenti di eliminare un singolo ordine.  
  
 In primo luogo, aggiungere questi stili a Windows.Resources:  
  
```xaml  
<Style x:Key="Label" TargetType="{x:Type Label}" BasedOn="{x:Null}">  
    <Setter Property="HorizontalAlignment" Value="Left"/>  
    <Setter Property="VerticalAlignment" Value="Center"/>  
    <Setter Property="Margin" Value="3"/>  
    <Setter Property="Height" Value="23"/>  
</Style>  
<Style x:Key="CustTextBox" TargetType="{x:Type TextBox}" BasedOn="{x:Null}">  
    <Setter Property="HorizontalAlignment" Value="Right"/>  
    <Setter Property="VerticalAlignment" Value="Center"/>  
    <Setter Property="Margin" Value="3"/>  
    <Setter Property="Height" Value="26"/>  
    <Setter Property="Width" Value="120"/>  
</Style>  
```  
  
 Successivamente, sostituire l'intera griglia esterna con questo codice:  
  
```xaml  
<Grid >  
     <Grid.RowDefinitions>  
         <RowDefinition Height="auto"/>  
         <RowDefinition Height="auto"/>  
         <RowDefinition Height="*"/>  
     </Grid.RowDefinitions>  
     <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">  
         <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />  
         <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>  
         <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>  
         <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>  
         <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>  
         <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
         <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>  
         <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
         <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
     </StackPanel>  
     <Grid x:Name="existingCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" Margin="5" Visibility="Visible" VerticalAlignment="Top" Background="AntiqueWhite" DataContext="{StaticResource customerViewSource}">  
         <Grid.ColumnDefinitions>  
             <ColumnDefinition Width="Auto" MinWidth="233"/>  
             <ColumnDefinition Width="Auto" MinWidth="397"/>  
         </Grid.ColumnDefinitions>  
         <Grid.RowDefinitions>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
         </Grid.RowDefinitions>  
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>  
         <TextBox x:Name="customerIDTextBox"  Grid.Row="0" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>  
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>  
         <TextBox x:Name="cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"   
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>  
         <TextBox x:Name="postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>  
         <TextBox x:Name="regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
     </Grid>  
     <Grid x:Name="newCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding RelativeSource={RelativeSource FindAncestor, AncestorType={x:Type Window}}, Path=newCustomer, UpdateSourceTrigger=Explicit}" Visibility="Collapsed" Background="CornflowerBlue">  
         <Grid.ColumnDefinitions>  
             <ColumnDefinition Width="Auto" MinWidth="233"/>  
             <ColumnDefinition Width="Auto" MinWidth="397"/>  
         </Grid.ColumnDefinitions>  
         <Grid.RowDefinitions>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
         </Grid.RowDefinitions>  
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_customerIDTextBox"  Grid.Row="0"  Style="{StaticResource CustTextBox}"   
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>  
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"   
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
     </Grid>  
     <Grid x:Name="newOrderGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding Path=newOrder, Mode=TwoWay}" Visibility="Collapsed" Background="LightGreen">  
         <Grid.ColumnDefinitions>  
             <ColumnDefinition Width="Auto" MinWidth="233"/>  
             <ColumnDefinition Width="Auto" MinWidth="397"/>  
         </Grid.ColumnDefinitions>  
         <Grid.RowDefinitions>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
         </Grid.RowDefinitions>  
         <Label Content="New Order Form" FontWeight="Bold"/>  
         <Label Content="Employee ID:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_employeeIDTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding EmployeeID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Order Date:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <DatePicker x:Name="add_orderDatePicker" Grid.Row="2"  HorizontalAlignment="Right" Width="120"  
                 SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
         <Label Content="Required Date:" Grid.Row="3" Style="{StaticResource Label}"/>  
         <DatePicker x:Name="add_requiredDatePicker" Grid.Row="3" HorizontalAlignment="Right" Width="120"  
                  SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
         <Label Content="Shipped Date:"  Grid.Row="4"  Style="{StaticResource Label}"/>  
         <DatePicker x:Name="add_shippedDatePicker"  Grid.Row="4"  HorizontalAlignment="Right" Width="120"  
                 SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
         <Label Content="Ship Via:"  Grid.Row="5" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_ShipViaTextBox"  Grid.Row="5" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ShipVia, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Freight"  Grid.Row="6" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_freightTextBox" Grid.Row="6" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Freight, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
     </Grid>  
     <DataGrid x:Name="ordersDataGrid" SelectionUnit="Cell" SelectionMode="Single" AutoGenerateColumns="False" CanUserAddRows="false" IsEnabled="True" EnableRowVirtualization="True" Width="auto" ItemsSource="{Binding Source={StaticResource customerOrdersViewSource}}" Margin="10,10,10,10" Grid.Row="2" RowDetailsVisibilityMode="VisibleWhenSelected">  
         <DataGrid.Columns>  
             <DataGridTemplateColumn>  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <Button Content="Delete"  Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="customerIDColumn" Binding="{Binding CustomerID}" Header="Customer ID" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="employeeIDColumn" Binding="{Binding EmployeeID}" Header="Employee ID" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="freightColumn" Binding="{Binding Freight}" Header="Freight" Width="SizeToHeader"/>  
             <DataGridTemplateColumn x:Name="orderDateColumn" Header="Order Date" Width="SizeToHeader">  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <DatePicker SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="orderIDColumn" Binding="{Binding OrderID}" Header="Order ID" Width="SizeToHeader"/>  
             <DataGridTemplateColumn x:Name="requiredDateColumn" Header="Required Date" Width="SizeToHeader">  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <DatePicker SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="shipAddressColumn" Binding="{Binding ShipAddress}" Header="Ship Address" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipCityColumn" Binding="{Binding ShipCity}" Header="Ship City" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipCountryColumn" Binding="{Binding ShipCountry}" Header="Ship Country" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipNameColumn" Binding="{Binding ShipName}" Header="Ship Name" Width="SizeToHeader"/>  
             <DataGridTemplateColumn x:Name="shippedDateColumn" Header="Shipped Date" Width="SizeToHeader">  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <DatePicker SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="shipPostalCodeColumn" Binding="{Binding ShipPostalCode}" Header="Ship Postal Code" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipRegionColumn" Binding="{Binding ShipRegion}" Header="Ship Region" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipViaColumn" Binding="{Binding ShipVia}" Header="Ship Via" Width="SizeToHeader"/>  
         </DataGrid.Columns>  
     </DataGrid>  
 </Grid>  
```  
  
## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Aggiungere pulsanti per spostarsi, aggiungere, aggiornare ed eliminare  
 Nelle applicazioni Windows Form, ottenere un oggetto di BindingNavigator con i pulsanti per spostarsi tra le righe in un database e l'esecuzione di operazioni CRUD di base. WPF fornisce un controllo BindingNavigator ma sono abbastanza facili da verificare. È possibile farlo con pulsanti all'interno di un elemento StackPanel orizzontale nella riga inferiore della griglia della pagina e si verranno associare i pulsanti con i comandi che sono associati ai metodi nel code-behind.  
  
 Vi sono quattro parti per la logica di comando: (1) i comandi, (2) le associazioni, (3) i pulsanti e (4) i gestori comando nel code-behind.  
  
#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Aggiungere i comandi, associazioni e i pulsanti in XAML  
  
1.  In primo luogo, è possibile aggiungere i comandi nel file MainWindow. XAML all'interno dell'elemento Windows.Resources:  
  
    ```xaml  
  
     <RoutedUICommand x:Key="FirstCommand" Text="First"/>  
    <RoutedUICommand x:Key="LastCommand" Text="Last"/>  
    <RoutedUICommand x:Key="NextCommand" Text="Next"/>  
    <RoutedUICommand x:Key="PreviousCommand" Text="Previous"/>  
    <RoutedUICommand x:Key="DeleteCustomerCommand" Text="Delete Customer"/>  
    <RoutedUICommand x:Key="DeleteOrderCommand" Text="Delete Order"/>  
    <RoutedUICommand x:Key="UpdateCommand" Text="Update"/>  
    <RoutedUICommand x:Key="AddCommand" Text="Add"/>  
    <RoutedUICommand x:Key="CancelCommand" Text="Cancel"/>  
    ```  
  
2.  Un oggetto CommandBinding esegue il mapping di un evento RoutedUICommand a un metodo nel code-behind. Aggiungere questo elemento di CommandBindings dopo il Windows.Resources tag di chiusura:  
  
    ```xaml  
  
        <Window.CommandBindings>  
        <CommandBinding Command="{StaticResource FirstCommand}" Executed="FirstCommandHandler"/>  
        <CommandBinding Command="{StaticResource LastCommand}" Executed="LastCommandHandler"/>  
        <CommandBinding Command="{StaticResource NextCommand}" Executed="NextCommandHandler"/>  
        <CommandBinding Command="{StaticResource PreviousCommand}" Executed="PreviousCommandHandler"/>  
        <CommandBinding Command="{StaticResource DeleteCustomerCommand}" Executed="DeleteCustomerCommandHandler"/>  
        <CommandBinding Command="{StaticResource DeleteOrderCommand}" Executed="DeleteOrderCommandHandler"/>  
        <CommandBinding Command="{StaticResource UpdateCommand}" Executed="UpdateCommandHandler"/>  
        <CommandBinding Command="{StaticResource AddCommand}" Executed="AddCommandHandler"/>  
        <CommandBinding Command="{StaticResource CancelCommand}" Executed="CancelCommandHandler"/>  
    </Window.CommandBindings>  
    ```  
  
3.  A questo punto è possibile aggiungere StackPanel con la navigazione, aggiungere, eliminare e aggiornare i pulsanti. In primo luogo, aggiungere questo stile al Windows.Resources:  
  
    ```xaml  
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="FontSize" Value="24"/>  
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>  
        <Setter Property="Margin" Value="2,2,2,0"/>  
        <Setter Property="Width" Value="40"/>  
        <Setter Property="Height" Value="auto"/>  
    </Style>  
    ```  
  
     A questo punto è possibile incollare questo codice subito dopo il RowDefinitions per l'elemento esterno della griglia nella parte superiore della pagina XAML:  
  
    ```xaml  
    <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">  
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />  
        <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>  
        <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>  
        <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>  
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>  
        <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>  
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
        <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
    </StackPanel>  
    ```  
  
#### <a name="add-command-handlers-to-the-mainwindow-class"></a>Aggiungere gestori di comandi alla classe MainWindow  
  
1.  Il code-behind è minimo, ad eccezione di metodi di aggiunta ed eliminazione. Si noti che lo spostamento viene eseguito chiamando metodi sulla proprietà vista di CollectionViewSource. Il DeleteOrderCommandHandler illustra come eseguire un'operazione di eliminazione a catena in un ordine. È necessario innanzitutto eliminare Order_Details che esso associati. Il UpdateCommandHandler aggiunge un nuovo cliente all'insieme, altrimenti solo l'oggetto esistente viene aggiornato con tutti i valori nelle caselle di testo apportate dall'utente viene modificato.  
  
2.  Se l'oggetto CollectionViewSource per la tabella Customers è un nome diverso, sarà necessario modificare il nome in ognuno di questi metodi, aggiungere tali metodi gestore alla classe MainWindow in MainWindow.xaml.cs:  
  
    ```csharp  
       private void LastCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToLast();  
    }  
  
    private void PreviousCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToPrevious();  
    }  
  
    private void NextCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToNext();  
    }  
  
    private void FirstCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToFirst();  
    }  
  
    private void DeleteCustomerCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        // If existing window is visible, then delete the customer and all their orders.  
        // In a real application, you should add warnings and allow a user to cancel the operation.  
        var cur = custViewSource.View.CurrentItem as Customer;  
  
        var cust = (from c in context.Customers  
                    where c.CustomerID == cur.CustomerID  
                    select c).FirstOrDefault();  
  
        if (cust != null)  
        {  
            foreach (var ord in cust.Orders.ToList())  
            {  
                Delete_Order(ord);  
            }  
            context.Customers.Remove(cust);  
        }  
        context.SaveChanges();  
        custViewSource.View.Refresh();  
    }  
  
    // Commit changes from the new customer form, the new order form,  
    // or edits made to the existing customer form.  
    private void UpdateCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        if (newCustomerGrid.IsVisible)  
        {  
            // Create a new object because the old one  
            // is being tracked by EF now.  
            newCustomer = new Customer();   
            newCustomer.Address = add_addressTextBox.Text;  
            newCustomer.City = add_cityTextBox.Text;  
            newCustomer.CompanyName = add_companyNameTextBox.Text;  
            newCustomer.ContactName = add_contactNameTextBox.Text;  
            newCustomer.ContactTitle = add_contactTitleTextBox.Text;  
            newCustomer.Country = add_countryTextBox.Text;  
            newCustomer.CustomerID = add_customerIDTextBox.Text;  
            newCustomer.Fax = add_faxTextBox.Text;  
            newCustomer.Phone = add_phoneTextBox.Text;  
            newCustomer.PostalCode = add_postalCodeTextBox.Text;  
            newCustomer.Region = add_regionTextBox.Text;  
  
            // Perform very basic validation  
            if (newCustomer.CustomerID.Length == 5)  
            {  
                // Insert the new customer at correct position:  
                int len = context.Customers.Local.Count();  
                int pos = len;  
                for (int i = 0; i < len; ++i)  
                {  
                    if (String.CompareOrdinal(newCustomer.CustomerID, context.Customers.Local[i].CustomerID) < 0)  
                    {  
                        pos = i;  
                        break;  
                    }  
                }  
                context.Customers.Local.Insert(pos, newCustomer);  
                custViewSource.View.Refresh();  
                custViewSource.View.MoveCurrentTo(newCustomer);  
            }  
            else  
            {  
                MessageBox.Show("CustomerID must have 5 characters.");  
            }  
  
            newCustomerGrid.Visibility = Visibility.Collapsed;  
            existingCustomerGrid.Visibility = Visibility.Visible;  
        }  
        else if (newOrderGrid.IsVisible)  
        {  
            // Order ID is auto-generated so we don't set it here.  
            // For CustomerID, address, etc we use the values from current customer.  
            // User can modify these in the datagrid after the order is entered.  
  
            newOrder.OrderDate = add_orderDatePicker.SelectedDate;  
            newOrder.RequiredDate = add_requiredDatePicker.SelectedDate;  
            newOrder.ShippedDate = add_shippedDatePicker.SelectedDate;  
            try  
            {  
                // Exercise for the reader if you are using Northwind:  
                // Add the Northwind Shippers table to the model.  
                // Acceptable ShipperID values are 1, 2, or 3.  
                if (add_ShipViaTextBox.Text == "1" || add_ShipViaTextBox.Text == "2"  
                    || add_ShipViaTextBox.Text == "3")  
                {  
                    newOrder.ShipVia = Convert.ToInt32(add_ShipViaTextBox.Text);  
                }  
                else  
                {  
                    MessageBox.Show("Shipper ID must be 1, 2, or 3 in Northwind.");  
                    return;  
                }  
            }  
            catch  
            {  
                MessageBox.Show("Ship Via must be convertible to int");  
                return;  
            }  
            try  
            {  
                newOrder.Freight = Convert.ToDecimal(add_freightTextBox.Text);  
            }  
            catch  
            {  
                MessageBox.Show("Freight must be convertible to decimal.");  
                return;  
            }  
  
            // Add the order into the EF model  
            context.Orders.Add(newOrder);  
            ordViewSource.View.Refresh();  
        }  
  
        // Save the changes, either for a new customer, a new order  
        // or an edit in an existing customer or order  
        context.SaveChanges();  
    }  
  
    // Sets up the form so that user can enter data. Data is later  
    // saved when user clicks Commit.  
    private void AddCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        existingCustomerGrid.Visibility = Visibility.Collapsed;  
        newOrderGrid.Visibility = Visibility.Collapsed;  
        newCustomerGrid.Visibility = Visibility.Visible;  
  
        // Clear all the text boxes before adding a new customer.  
        foreach (var child in newCustomerGrid.Children)  
        {  
            var tb = child as TextBox;  
            if (tb != null)  
            {  
                tb.Text = "";  
            }  
        }  
    }  
  
    private void NewOrder_click(object sender, RoutedEventArgs e)  
    {  
        var cust = custViewSource.View.CurrentItem as Customer;  
        if (cust == null)  
        {  
            MessageBox.Show("No customer selected.");  
            return;  
        }  
  
        newOrder.CustomerID = cust.CustomerID;  
  
        // Get address and other mostly constant fields from   
        // an existing order, if one exists  
        var coll = custViewSource.Source as IEnumerable<Customer>;  
        var lastOrder = (from c in coll  
                         from ord in c.Orders  
                         select ord).LastOrDefault();  
        if (lastOrder != null)  
        {  
            newOrder.ShipAddress = lastOrder.ShipAddress;  
            newOrder.ShipCity = lastOrder.ShipCity;  
            newOrder.ShipCountry = lastOrder.ShipCountry;  
            newOrder.ShipName = lastOrder.ShipName;  
            newOrder.ShipPostalCode = lastOrder.ShipPostalCode;  
            newOrder.ShipRegion = lastOrder.ShipRegion;  
        }  
  
        existingCustomerGrid.Visibility = Visibility.Collapsed;  
        newCustomerGrid.Visibility = Visibility.Collapsed;  
        newOrderGrid.UpdateLayout();  
        newOrderGrid.Visibility = Visibility.Visible;  
    }  
  
    // Cancels any input into the new customer form  
    private void CancelCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        add_addressTextBox.Text = "";  
        add_cityTextBox.Text = "";  
        add_companyNameTextBox.Text = "";  
        add_contactNameTextBox.Text = "";  
        add_contactTitleTextBox.Text = "";  
        add_countryTextBox.Text = "";  
        add_customerIDTextBox.Text = "";  
        add_faxTextBox.Text = "";  
        add_phoneTextBox.Text = "";  
        add_postalCodeTextBox.Text = "";  
        add_regionTextBox.Text = "";  
  
        existingCustomerGrid.Visibility = Visibility.Visible;  
        newCustomerGrid.Visibility = Visibility.Collapsed;  
        newOrderGrid.Visibility = Visibility.Collapsed;  
    }  
  
    private void Delete_Order(Order order)  
    {  
        // Find the order in the EF model.  
        var ord = (from o in context.Orders.Local  
                   where o.OrderID == order.OrderID  
                   select o).FirstOrDefault();  
  
        // Delete all the order_details that have  
        // this Order as a foreign key  
        foreach (var detail in ord.Order_Details.ToList())  
        {  
            context.Order_Details.Remove(detail);  
        }  
  
        // Now it's safe to delete the order.  
        context.Orders.Remove(ord);  
        context.SaveChanges();  
  
        // Update the data grid.  
        ordViewSource.View.Refresh();  
    }  
  
    private void DeleteOrderCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        // Get the Order in the row in which the Delete button was clicked.  
        Order obj = e.Parameter as Order;  
        Delete_Order(obj);  
    }  
    ```  
  
3.  Premere **F5**. Si dovrebbero visualizzare i dati e i pulsanti di navigazione devono funzionare come previsto. Fare clic su "Commit" per aggiungere un nuovo cliente o un ordine per il modello dopo aver immesso i dati.  Fare clic su "Annulla" per eseguire il backup all'esterno di un nuovo form cliente o un nuovo ordine senza salvare le modifiche. È possibile apportare modifiche a esistenti Customers e Orders direttamente nelle caselle di testo e verranno scritto tali modifiche al modello automaticamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio data tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [documentazione di Entity Framework](https://msdn.microsoft.com/data/ee712907.aspx)
