---
title: App dati semplice con WPF e Entity Framework 6
description: In questa procedura dettagliata, vedere come creare una semplice app Forms-over-data in Visual Studio con Windows Presentation Foundation (WPF) e Entity Framework 6.
ms.custom: SEO-VS-2020
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7aad99392db33256e991e731770266c1a53dec50
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435493"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Creare un'applicazione dati semplice con WPF ed Entity Framework 6

Questa procedura dettagliata illustra come creare un'applicazione "Forms over data" di base in Visual Studio. L'app usa SQL Server database locale, il database Northwind Entity Framework 6 (non Entity Framework Core) e Windows Presentation Foundation per .NET Framework (non .NET Core). Viene illustrato come eseguire l'associazione dati di base con una visualizzazione Master-Details ed è inoltre presente uno strumento di navigazione di associazione personalizzato con pulsanti per **Sposta avanti** , **Sposta indietro** , **sposta all'inizio** , **Sposta a fine** , **Aggiorna** ed **Elimina**.

Questo articolo è incentrato sull'uso di strumenti dati in Visual Studio e non tenta di spiegare le tecnologie sottostanti in modo approfondito. Si presuppone che si disponga di una conoscenza di base di XAML, Entity Framework e SQL. In questo esempio non viene inoltre illustrata l'architettura MVC (Model-View-ViewModel), che è standard per le applicazioni WPF. Tuttavia, è possibile copiare questo codice nella propria applicazione MVVM con poche modifiche.

## <a name="install-and-connect-to-northwind"></a>Installare e connettersi a Northwind

In questo esempio vengono utilizzati SQL Server Express database locale e il database di esempio Northwind. Se il provider di dati ADO.NET per il prodotto supporta Entity Framework, dovrebbe funzionare anche con altri prodotti del database SQL.

1. Se non si dispone di SQL Server Express database locale, installarlo dalla [pagina di download SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio** , è possibile installare SQL Server Express Local DB nel contesto del carico di lavoro **Sviluppo per desktop .NET** o come componente singolo.

2. Installare il database di esempio Northwind attenendosi alla procedura seguente:

    1. In Visual Studio aprire la finestra **Esplora oggetti di SQL Server** . **Esplora oggetti di SQL Server** viene installato come parte del carico di lavoro di **elaborazione e archiviazione dei dati** nel **programma di installazione di Visual Studio**. Espandere il nodo **SQL Server** . Fare clic con il pulsante destro del mouse sull'istanza del database locale e scegliere **nuova query**.

       Si apre una finestra dell'editor di query.

    2. Copiare lo [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query, quindi scegliere il pulsante **Execute (Esegui** ).

       Dopo un breve periodo di tempo, viene completata l'esecuzione della query e viene creato il database Northwind.

3. [Aggiungere nuove connessioni](../data-tools/add-new-connections.md) per Northwind.

## <a name="configure-the-project"></a>Configurare il progetto

1. In Visual Studio creare un nuovo progetto di **app WPF** in C#.

2. Aggiungere il pacchetto NuGet per Entity Framework 6. In **Esplora soluzioni** selezionare il nodo del progetto. Nel menu principale scegliere **progetto**  >  **Gestisci pacchetti NuGet**.

     ![Voce di menu Gestisci pacchetti NuGet](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3. In **Gestione pacchetti NuGet** fare clic sul collegamento **Browse (Sfoglia** ). Entity Framework è probabilmente il primo pacchetto dell'elenco. Fare clic su **Installa** nel riquadro destro e seguire le istruzioni. La finestra di output indica quando è stata completata l'installazione.

     ![Entity Framework pacchetto NuGet](../data-tools/media/raddata_vs2015_nuget_ef.png)

4. A questo punto è possibile usare Visual Studio per creare un modello basato sul database Northwind.

## <a name="create-the-model"></a>Creare il modello

1. Fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Aggiungi**  >  **nuovo elemento**. Nel riquadro sinistro, sotto il nodo C#, scegliere **dati** e nel riquadro centrale scegliere **ADO.NET Entity Data Model**.

   ![Nuovo elemento del modello di Entity Framework](../data-tools/media/raddata-ef-new-project-item.png)

2. Chiamare il modello `Northwind_model` e scegliere **OK**. Si apre la **procedura guidata Entity Data Model** . Scegliere **progettazione EF da database** , quindi fare clic su **Avanti**.

   ![Modello EF dal database](../data-tools/media/raddata-ef-model-from-database.png)

3. Nella schermata successiva immettere o scegliere la connessione Northwind del database locale (ad esempio, (database locale) \MSSQLLocalDB), specificare il database Northwind e fare clic su **Avanti**.

4. Nella pagina successiva della procedura guidata scegliere le tabelle, le stored procedure e gli altri oggetti di database da includere nel modello di Entity Framework. Espandere il nodo dbo nella visualizzazione albero e scegliere **Customers** , **Orders** e **Order Details**. Lasciare selezionate le impostazioni predefinite e fare clic su **fine**.

    ![Scegliere gli oggetti di database per il modello](../data-tools/media/raddata-choose-ef-objects.png)

5. Tramite la procedura guidata vengono generate le classi C# che rappresentano il modello di Entity Framework. Le classi sono classi C# obsolete e sono quelle che è possibile associare all'interfaccia utente WPF. Il file con *estensione edmx* descrive le relazioni e altri metadati che associano le classi agli oggetti nel database. I file con *estensione TT* sono modelli T4 che generano il codice che opera sul modello e salva le modifiche apportate al database. È possibile visualizzare tutti questi file in **Esplora soluzioni** nel nodo Northwind_model:

      ![Esplora soluzioni i file di modello EF](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    L'area di progettazione per il file con estensione *edmx* consente di modificare alcune proprietà e relazioni nel modello. In questa procedura dettagliata non verrà usata la finestra di progettazione.

6. I file con *estensione TT* sono a scopo generale ed è necessario modificarne uno per utilizzare l'associazione dati WPF, che richiede ObservableCollections. In **Esplora soluzioni** espandere il nodo Northwind_model fino a trovare *Northwind_model. TT*. Assicurarsi che non si sia in *. File Context.tt* , che si trova direttamente sotto il file con *estensione edmx* .

   - Sostituire le due occorrenze di <xref:System.Collections.ICollection> con <xref:System.Collections.ObjectModel.ObservableCollection%601> .

   - Sostituire la prima occorrenza di <xref:System.Collections.Generic.HashSet%601> con <xref:System.Collections.ObjectModel.ObservableCollection%601> intorno alla riga 51. Non sostituire la seconda occorrenza di HashSet.

   - Sostituire l'unica occorrenza di <xref:System.Collections.Generic> (intorno alla riga 431) con <xref:System.Collections.ObjectModel> .

7. Premere **CTRL** + **MAIUSC** + **B** per compilare il progetto. Al termine della compilazione, le classi del modello sono visibili alla creazione guidata origine dati.

A questo punto si è pronti per associare questo modello alla pagina XAML in modo che sia possibile visualizzare, esplorare e modificare i dati.

## <a name="databind-the-model-to-the-xaml-page"></a>Associare il modello alla pagina XAML

È possibile scrivere codice di data binding, ma è molto più semplice consentire a Visual Studio di eseguire questa operazione.

1. Dal menu principale scegliere **progetto**  >  **Aggiungi nuova origine dati** per visualizzare la **Configurazione guidata origine dati**. Scegliere **oggetto** perché si sta associando le classi del modello, non al database:

     ![Configurazione guidata origine dati con origine oggetto](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2. Espandere il nodo per il progetto e selezionare **Customer**. (Le origini per gli ordini vengono generate automaticamente dalla proprietà di navigazione Orders nel cliente).

     ![Aggiungere classi di entità come origini dati](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3. Fare clic su **Fine**.

4. Passare a *MainWindow. XAML* nella visualizzazione codice. Il codice XAML viene mantenuto per gli scopi di questo esempio. Modificare il titolo di MainWindow in un elemento più descrittivo e aumentare l'altezza e la larghezza a 600 x 800 per il momento. È sempre possibile modificarlo in un secondo momento. Aggiungere quindi queste tre definizioni di riga alla griglia principale, una riga per i pulsanti di spostamento, una per i dettagli del cliente e una per la griglia che Mostra gli ordini:

    ```xaml
        <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5. Aprire *MainWindow. XAML* in modo che sia visualizzato nella finestra di progettazione. In questo modo la finestra **origini dati** verrà visualizzata come opzione nel margine della finestra di Visual Studio accanto alla **casella degli strumenti**. Fare clic sulla scheda per aprire la finestra. in alternativa, premere **MAIUSC** + **ALT** + **D** o scegliere **Visualizza**  >  **altre**  >  **origini dati** di Windows. Ogni proprietà della classe customers verrà visualizzata nella propria casella di testo. Per prima cosa, fare clic sulla freccia nella casella combinata **Customers** e scegliere **Details**. Trascinare quindi il nodo sulla parte centrale dell'area di progettazione in modo che la finestra di progettazione sappia che si desidera che venga posizionata nella riga intermedia. Se non si posiziona il mouse, è possibile specificare la riga manualmente in un secondo momento nel codice XAML. Per impostazione predefinita, i controlli vengono posizionati verticalmente in un elemento Grid, ma a questo punto è possibile disporli nel form. Ad esempio, potrebbe essere utile inserire la casella di testo **nome** in alto, sopra l'indirizzo. L'applicazione di esempio per questo articolo Riordina i campi e li ridispone in due colonne.

     ![Associazione all'origine dati dei clienti ai singoli controlli](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     Nella visualizzazione codice è ora possibile visualizzare un nuovo `Grid` elemento nella riga 1, ovvero la riga intermedia, della griglia padre. La griglia padre ha un `DataContext` attributo che fa riferimento a un oggetto CollectionViewSource che è stato aggiunto all' `Windows.Resources` elemento. Dato il contesto dei dati, quando la prima casella di testo viene associata a **Address** , il nome viene mappato alla `Address` proprietà nell' `Customer` oggetto corrente in CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Quando un cliente è visibile nella metà superiore della finestra, si desidera visualizzarne gli ordini nella metà inferiore. Gli ordini vengono mostrati in un singolo controllo di visualizzazione griglia. Per il corretto funzionamento dell'associazione dati master-detail, è importante associare la proprietà Orders della classe Customers, non al nodo Orders separato. Trascinare la proprietà Orders della classe Customers sulla metà inferiore del form, in modo che la finestra di progettazione lo inserisca nella riga 2:

     ![Trascina le classi Orders come griglia](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7. Visual Studio ha generato tutto il codice di binding che connette i controlli dell'interfaccia utente agli eventi nel modello. Per visualizzare alcuni dati, è sufficiente scrivere del codice per popolare il modello di. Per prima cosa, passare a *MainWindow.XAML.cs* e aggiungere un membro dati alla classe MainWindow per il contesto dati. Questo oggetto, che è stato generato automaticamente, funge da controllo che tiene traccia delle modifiche e degli eventi nel modello. Verranno inoltre aggiunti i membri dati CollectionViewSource per i clienti e gli ordini e la logica di inizializzazione del costruttore associata. La parte superiore della classe avrà un aspetto simile al seguente:

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     Aggiungere una `using` direttiva per System. Data. Entity per portare il metodo di estensione del carico nell'ambito:

     ```csharp
     using System.Data.Entity;
     ```

     Scorrere ora verso il basso e trovare il `Window_Loaded` gestore eventi. Si noti che Visual Studio ha aggiunto un oggetto CollectionViewSource. Rappresenta l'oggetto NorthwindEntities selezionato al momento della creazione del modello. Questa operazione è già stata aggiunta, quindi non è necessaria. Sostituire il codice in in `Window_Loaded` modo che il metodo sia ora simile al seguente:

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8. Premere **F5**. Verranno visualizzati i dettagli per il primo cliente recuperato in CollectionViewSource. È anche possibile visualizzare gli ordini nella griglia dei dati. La formattazione non è eccezionale, quindi è consigliabile risolverla. È anche possibile creare un modo per visualizzare gli altri record ed eseguire operazioni CRUD di base.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Modificare la progettazione della pagina e aggiungere griglie per i nuovi clienti e ordini

La disposizione predefinita prodotta da Visual Studio non è la soluzione ideale per l'applicazione, quindi il codice XAML finale verrà fornito qui per la copia nel codice. Sono necessari anche alcuni "moduli", che sono effettivamente griglie, per consentire all'utente di aggiungere un nuovo cliente o ordine. Per poter aggiungere un nuovo cliente e un ordine, è necessario un set separato di caselle di testo che non sono associate a dati a `CollectionViewSource` . Verrà controllata la griglia visualizzata dall'utente in un determinato momento impostando la proprietà Visible nei metodi del gestore. Infine, si aggiunge un pulsante Elimina a ogni riga della griglia Orders per consentire all'utente di eliminare un singolo ordine.

In primo luogo, aggiungere questi stili all' `Windows.Resources` elemento in *MainWindow. XAML* :

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
<Grid>
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
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
         <TextBox x:Name="customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
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
         <TextBox x:Name="add_customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
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
                         <Button Content="Delete" Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
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

Nelle applicazioni Windows Forms si ottiene un oggetto BindingNavigator con i pulsanti per spostarsi tra le righe di un database ed eseguire operazioni CRUD di base. WPF non fornisce un oggetto BindingNavigator, ma è abbastanza semplice crearne uno. A tale scopo, è possibile utilizzare i pulsanti all'interno di un elemento StackPanel orizzontale e associare i pulsanti ai comandi associati a metodi nel code-behind.

La logica del comando include quattro parti: (1) i comandi, (2) i binding, (3) i pulsanti e (4) i gestori di comandi nel code-behind.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Aggiungere comandi, associazioni e pulsanti in XAML

1. In primo luogo, aggiungere i comandi nel file *MainWindow. XAML* all'interno dell' `Windows.Resources` elemento:

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

2. Un oggetto CommandBinding esegue `RoutedUICommand` il mapping di un evento a un metodo nel code-behind. Aggiungere questo `CommandBindings` elemento dopo il `Windows.Resources` tag di chiusura:

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

3. A questo punto, aggiungere l'oggetto `StackPanel` con i pulsanti di spostamento, aggiunta, eliminazione e aggiornamento. In primo luogo, aggiungere questo stile a `Windows.Resources` :

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     In secondo luogo, incollare il codice immediatamente dopo `RowDefinitions` per l' `Grid` elemento esterno, verso la parte superiore della pagina XAML:

    ```xaml
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnPrev" Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext" Content="►" Command="{StaticResource NextCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnLast" Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button Name="btnAdd" Content="New Customer" Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel" Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

### <a name="add-command-handlers-to-the-mainwindow-class"></a>Aggiungere gestori di comandi alla classe MainWindow

Il code-behind è minimo ad eccezione dei metodi Add e DELETE. La navigazione viene eseguita chiamando metodi sulla proprietà di visualizzazione dell'oggetto CollectionViewSource. `DeleteOrderCommandHandler`Viene illustrato come eseguire un'eliminazione a catena in un ordine. Prima di tutto è necessario eliminare i Order_Details associati. `UpdateCommandHandler`Aggiunge un nuovo cliente o ordine alla raccolta, altrimenti aggiorna semplicemente un cliente o un ordine esistente con le modifiche apportate dall'utente nelle caselle di testo.

Aggiungere questi metodi di gestione alla classe MainWindow in *MainWindow.XAML.cs*. Se l'oggetto CollectionViewSource per la tabella Customers ha un nome diverso, è necessario modificare il nome in ognuno di questi metodi:

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>Eseguire l'applicazione

Premere **F5** per avviare il debug. Verranno visualizzati i dati relativi ai clienti e agli ordini popolati nella griglia e i pulsanti di spostamento dovrebbero funzionare come previsto. Fare clic su **commit** per aggiungere un nuovo cliente o ordine al modello dopo aver immesso i dati. Fare clic su **Annulla** per uscire da un nuovo modulo di cliente o nuovo ordine senza salvare i dati. È possibile apportare modifiche ai clienti e agli ordini esistenti direttamente nelle caselle di testo e tali modifiche vengono scritte automaticamente nel modello.

## <a name="see-also"></a>Vedere anche

- [Visual Studio data tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Documentazione di Entity Framework](/ef/)
