---
title: Creare un'applicazione dati semplice con WPF e Entity Framework 6 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 403415eaf8a882efdd63fdb9a73b5489b91f2529
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651090"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Creare un'applicazione dati semplice con WPF ed Entity Framework 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo procedura dettagliata Mostra come creare un'applicazione "Forms over data" di base in Visual Studio con SQL Server database locale, il database Northwind, Entity Framework 6 e Windows Presentation Foundation. Viene illustrato come eseguire l'associazione dati di base con una visualizzazione Master-Details ed è presente anche un "strumento di navigazione di associazione" personalizzato con pulsanti per "Sposta avanti", "sposta indietro", "sposta in inizio", "sposta alla fine", "Aggiorna" ed "Elimina".

 Questo articolo è incentrato sull'uso di strumenti dati in Visual Studio e non tenta di spiegare le tecnologie sottostanti in modo approfondito. Si presuppone che si disponga di una conoscenza di base di XAML, Entity Framework e SQL. In questo esempio non viene inoltre illustrata l'architettura MVVM, che è standard per le applicazioni WPF. Tuttavia, è possibile copiare questo codice nella propria applicazione MVVM con pochissime modifiche.

## <a name="install-and-connect-to-northwind"></a>Installare e connettersi a Northwind
 In questo esempio vengono utilizzati SQL Server Express database locale e il database di esempio Northwind. Dovrebbe funzionare anche con altri prodotti di database SQL se il provider di dati ADO.NET per il prodotto supporta Entity Framework.

1. Se non è già stato fatto, installare SQL Server 2014 local DB Express 32 dalla [pagina di download delle edizioni SQL Server](https://www.microsoft.com/sql-server/sql-server-editions-express).

2. Installare il database di esempio Northwind seguendo le istruzioni riportate qui: [install SQL Server Sample Databases](../data-tools/install-sql-server-sample-databases.md).

3. [Aggiungere nuove connessioni](../data-tools/add-new-connections.md) per Northwind.

## <a name="configure-the-project"></a>Configurare il progetto

1. In Visual Studio scegliere **file &#124; nuovo progetto** e quindi creare una nuova C# applicazione WPF.

2. Si aggiungerà quindi il pacchetto NuGet per Entity Framework 6. In Esplora soluzioni selezionare il nodo del progetto. Nel menu principale scegliere  **&#124; progetto Gestisci pacchetti NuGet...**

     ![Voce di menu Gestisci pacchetti NuGet](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")

3. In Gestione pacchetti NuGet fare clic sul collegamento **Browse (Sfoglia** ). Entity Framework è probabilmente il primo pacchetto dell'elenco. Fare clic su **Installa** nel riquadro destro e seguire le istruzioni. La finestra di output indica quando è stata completata l'installazione.

     ![Entity Framework pacchetto NuGet](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")

4. A questo punto è possibile usare Visual Studio per creare un modello basato sul database Northwind.

## <a name="create-the-model"></a>Creare il modello

1. Fare clic con il pulsante destro del mouse sul nodo del progetto in Esplora soluzioni e scegliere  **&#124; Aggiungi nuovo elemento**. Nel riquadro sinistro, sotto il C# nodo, scegliere **dati** e nel riquadro centrale scegliere **ADO.NET Entity Data Model**.

    ![Nuovo elemento del progetto del modello di Entity Framework](../data-tools/media/raddata-ef-new-project-item.png "Nuovo elemento del progetto raddata EF")

2. Chiamare il modello `Northwind_model` e scegliere OK. Viene visualizzata la **procedura guidata Entity Data Model**. Scegliere **progettazione EF da database** , quindi fare clic su **Avanti**.

    ![Modello EF dal database](../data-tools/media/raddata-ef-model-from-database.png "Modello raddata EF dal database")

3. Nella schermata successiva scegliere la connessione Northwind del database locale e fare clic su **Avanti**.

4. Nella pagina successiva della procedura guidata è possibile scegliere quali tabelle, stored procedure e altri oggetti di database includere nel modello di Entity Framework. Espandere il nodo dbo nella visualizzazione albero e scegliere Customers, Orders e Order Details. Lasciare selezionate le impostazioni predefinite e fare clic su **fine**.

    ![Scegliere gli oggetti di database per il modello](../data-tools/media/raddata-choose-ef-objects.png "raddata scegliere oggetti EF")

5. Tramite la procedura guidata C# vengono generate le classi che rappresentano il modello di Entity Framework. Si tratta di classi C# semplici obsolete, che sono quelle che verranno restituite all'interfaccia utente WPF. Il file con estensione edmx descrive le relazioni e altri metadati che associano le classi agli oggetti nel database.  I file con estensione tt sono modelli T4 che generano il codice che funzionerà sul modello e salveranno le modifiche apportate al database. È possibile visualizzare tutti questi file in Esplora soluzioni nel nodo Northwind_model:

    ![Esplora soluzioni i file di modello EF](../data-tools/media/raddata-solution-explorer-ef-model-files.png "raddata Esplora soluzioni i file di modello EF")

    L'area di progettazione per il file con estensione edmx consente di modificare alcune proprietà e relazioni nel modello. In questa procedura dettagliata non verrà usata la finestra di progettazione.

6. I file con estensione tt sono di uso generico ed è necessario modificarne uno per lavorare con l'associazione dati WPF, che richiede ObservableCollections.  In Esplora soluzioni espandere il nodo Northwind_model fino a trovare Northwind_model. TT. Verificare che l'utente **non** sia presente nel *. File context. TT che si trova direttamente sotto il file con estensione edmx.

   - Sostituire le due occorrenze di <xref:System.Collections.ICollection> con <xref:System.Collections.ObjectModel.ObservableCollection%601>.

   - Sostituire la prima occorrenza di <xref:System.Collections.Generic.HashSet%601> con <xref:System.Collections.ObjectModel.ObservableCollection%601> alla riga 51. Non sostituire la seconda occorrenza di HashSet

   - Sostituire l'unica occorrenza di <xref:System.Collections.Generic> (intorno alla riga 334) con <xref:System.Collections.ObjectModel>.

7. Premere **CTRL + MAIUSC + B** per compilare il progetto. Al termine della compilazione, le classi del modello sono visibili alla creazione guidata origine dati.

   A questo punto è possibile associare questo modello alla pagina XAML in modo che sia possibile visualizzare, esplorare e modificare i dati.

## <a name="databind-the-model-to-the-xaml-page"></a>Associare il modello alla pagina XAML
 È possibile scrivere codice di data binding, ma è molto più semplice consentire a Visual Studio di eseguire questa operazione.

1. Dal menu principale scegliere **progetto &#124; Aggiungi nuova origine dati** per visualizzare la **Configurazione guidata origine dati**. Scegliere **oggetto** perché si sta associando le classi del modello, non al database:

     ![Configurazione guidata origine dati con origine oggetto](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "Configurazione guidata origine dati raddata con origine oggetto")

2. Selezionare Customer.  (Le origini per gli ordini verranno generate automaticamente dalla proprietà di navigazione Orders del cliente).

     ![Aggiungere classi di entità come origini dati](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata aggiungere classi di entità come origini dati")

3. Fare clic su **fine**

4. Passare a MainWindow. XAML nella visualizzazione codice. Il codice XAML verrà mantenuto molto semplice per gli scopi di questo esempio. Modificare il titolo di MainWindow in un elemento più descrittivo e aumentare l'altezza e la larghezza a 600 x 800 per il momento. È sempre possibile modificarlo in un secondo momento. Aggiungere quindi queste tre definizioni di riga alla griglia principale, una riga per i pulsanti di spostamento, una per i dettagli del cliente, una per la griglia che Mostra gli ordini:

    ```xaml
    <Grid.RowDefinitions>
               <RowDefinition Height="auto"/>
               <RowDefinition Height="auto"/>
               <RowDefinition Height="*"/>
           </Grid.RowDefinitions>
    ```

5. Aprire MainWindow. XAML in modo che venga visualizzato nella finestra di progettazione. In questo modo la finestra Origini dati verrà visualizzata come opzione nel margine della finestra di Visual Studio accanto alla casella degli strumenti. Fare clic sulla scheda per aprire la finestra. in caso contrario, premere **MAIUSC + ALT + D** o scegliere  **&#124; Visualizza &#124; altre origini dati di Windows**. Ogni proprietà della classe customers verrà visualizzata nella propria casella di testo. Fare prima clic sulla freccia nella casella combinata Customers e scegliere **Details**. Trascinare quindi il nodo sulla parte centrale dell'area di progettazione in modo che la finestra di progettazione sappia che si desidera che venga posizionata nella riga intermedia.  Se non si posiziona il mouse, è possibile specificare la riga manualmente in un secondo momento nel codice XAML. Per impostazione predefinita, i controlli vengono posizionati verticalmente in un elemento Grid, ma a questo punto è possibile disporli nel form.  Ad esempio, potrebbe essere utile inserire la casella di testo nome in alto, sopra l'indirizzo. L'applicazione di esempio per questo articolo Riordina i campi e li ridispone in due colonne.

     ![Associazione all'origine dati dei clienti ai singoli controlli](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "associazione all'origine dati dei clienti raddata ai singoli controlli")

     Nella visualizzazione codice è ora possibile visualizzare un nuovo elemento `Grid` nella riga 1, ovvero la riga intermedia, della griglia padre. La griglia padre dispone di un attributo `DataContext` che fa riferimento a un oggetto CollectionViewSource che è stato aggiunto all'elemento `Windows.Resources`. Dato il contesto dei dati, quando la prima casella di testo, ad esempio, viene associata a "Address", il nome viene mappato alla proprietà `Address` nell'oggetto `Customer` corrente in CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Quando un cliente è visibile nella metà superiore della finestra, si desidera visualizzarne gli ordini nella metà inferiore. Gli ordini verranno mostrati in un unico controllo di visualizzazione griglia. Per il corretto funzionamento dell'associazione dati master-detail, è importante associare la proprietà Orders della classe Customers, non al nodo Orders separato. Prestare attenzione all'illustrazione seguente. Trascinare la proprietà Orders della classe Customers sulla metà inferiore del form, in modo che la finestra di progettazione lo inserisca nella riga 2:

     ![Trascina le classi Orders come griglia](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata trascinare le classi Orders come griglia")

7. Visual Studio ha generato tutto il codice di binding che connette i controlli dell'interfaccia utente agli eventi nel modello. Per visualizzare alcuni dati, è sufficiente scrivere del codice per popolare il modello... Per prima cosa, passare a MainWindow.xaml.cs e aggiungere un membro dati alla classe MainWindow per il contesto dati. Questo oggetto, che è stato generato per noi, funge da controllo che tiene traccia delle modifiche e degli eventi nel modello. In questo caso, verranno aggiunti due membri che verranno usati in un secondo momento per aggiungere un nuovo cliente o un nuovo ordine. Verrà inoltre aggiunta la logica di inizializzazione del costruttore. La parte superiore della classe dovrebbe essere simile alla seguente:

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

     Aggiungere una direttiva `using` per System. Data. Entity per portare il metodo di estensione del carico nell'ambito:

    ```csharp
    using System.Data.Entity;
    ```

     Scorrere ora verso il basso e trovare il gestore dell'evento Window_Loaded. Si noti che Visual Studio ha aggiunto un oggetto CollectionViewSource per noi. Rappresenta l'oggetto NorthwindEntities selezionato al momento della creazione del modello. Aggiungere il codice a Window_loaded in modo che l'intero metodo sia ora simile al seguente:

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

8. Premere **F5**. Verranno visualizzati i dettagli per il primo cliente recuperato in CollectionViewSource e i relativi ordini nella griglia dei dati. La formattazione non è eccezionale, quindi è consigliabile risolverla. e un modo per visualizzare gli altri record e per eseguire operazioni CRUD di base.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Modificare la progettazione della pagina e aggiungere griglie per i nuovi clienti e ordini
 La disposizione predefinita prodotta da Visual Studio non è ideale per l'applicazione, quindi le modifiche verranno apportate manualmente nel codice XAML. Sono necessari anche alcuni "moduli", che sono effettivamente griglie, per consentire all'utente di aggiungere un nuovo cliente o un nuovo ordine.    Per poter aggiungere un nuovo cliente e un ordine, è necessario un set separato di caselle di testo che non sono associate a dati al `CollectionViewSource`. Verrà controllata la griglia visualizzata dall'utente in un determinato momento impostando la proprietà Visible nei metodi del gestore.

 Infine, si aggiungerà un pulsante Delete a ogni riga della griglia Orders per consentire a un utente di eliminare un singolo ordine.

 In primo luogo, aggiungere questi stili a Windows. resources:

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

 Sostituire quindi l'intera griglia esterna con il markup seguente:

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
 Nelle applicazioni Windows Forms si ottiene un oggetto BindingNavigator con i pulsanti per spostarsi tra le righe di un database ed eseguire operazioni CRUD di base. WPF non fornisce un oggetto BindingNavigator, ma è abbastanza semplice da creare. Questa operazione verrà eseguita con i pulsanti all'interno di un elemento StackPanel orizzontale nella riga inferiore della griglia della pagina e verranno associati i pulsanti ai comandi associati a metodi nel code-behind.

 La logica del comando include quattro parti: (1) i comandi, (2) i binding, (3) i pulsanti e (4) i gestori di comandi nel code-behind.

#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Aggiungere comandi, associazioni e pulsanti in XAML

1. Prima di tutto, aggiungere i comandi nel file MainWindow. XAML all'interno dell'elemento Windows. resources:

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

2. Un oggetto CommandBinding esegue il mapping di un evento RoutedUICommand a un metodo nel code-behind. Aggiungere questo elemento CommandBindings dopo il tag di chiusura Windows. resources:

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

3. A questo punto, aggiungere l'elemento StackPanel con i pulsanti di spostamento, aggiunta, eliminazione e aggiornamento. In primo luogo, aggiungere questo stile a Windows. resources:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     A questo punto, incollare il codice subito dopo RowDefinitions per l'elemento Grid esterno nella parte superiore della pagina XAML:

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

1. Il code-behind è minimo ad eccezione dei metodi Add e DELETE. Si noti che la navigazione viene eseguita chiamando metodi sulla proprietà View di CollectionViewSource. DeleteOrderCommandHandler Mostra come eseguire un'eliminazione a catena in un ordine. Prima di tutto è necessario eliminare i Order_Details associati. UpdateCommandHandler aggiunge un nuovo cliente alla raccolta. in caso contrario, aggiorna semplicemente l'oggetto esistente con qualsiasi modifica apportata dall'utente nelle caselle di testo.

2. Aggiungere questi metodi di gestione alla classe MainWindow in MainWindow.xaml.cs. se l'oggetto CollectionViewSource per la tabella Customers ha un nome diverso, sarà necessario modificare il nome in ognuno di questi metodi:

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

3. Premere **F5**. Dovrebbero essere visualizzati i dati e i pulsanti di spostamento dovrebbero funzionare come previsto. Fare clic su "commit" per aggiungere un nuovo cliente o un ordine al modello dopo aver immesso i dati.  Fare clic su "Annulla" per uscire da un nuovo cliente o da un nuovo modulo dell'ordine senza salvarlo. È possibile apportare modifiche ai clienti e agli ordini esistenti direttamente nelle caselle di testo e tali modifiche verranno scritte automaticamente nel modello.

## <a name="see-also"></a>Vedere anche
 Documentazione [di Visual Studio Data Tools per .net](../data-tools/visual-studio-data-tools-for-dotnet.md) [Entity Framework](https://msdn.microsoft.com/data/ee712907.aspx)
