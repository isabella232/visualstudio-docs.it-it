---
title: Creare un'applicazione dati semplice con WPF ed Entity Framework 6
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5993256b41a07c4861ef2def58dc14d7fd849313
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305611"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Creare un'applicazione dati semplice con WPF ed Entity Framework 6

Questa procedura dettagliata illustra come creare un'applicazione di base "Form over data" in Visual Studio. L'app Usa LocalDB di SQL Server, il database Northwind, Entity Framework 6 e Windows Presentation Foundation. Viene illustrato come eseguire l'associazione dati di base con una visualizzazione master-Details e include anche un navigatore Binding personalizzato con i pulsanti per **Sposta successivo**, **Move Previous**, **spostarne iniziano**, **Sposta alla fine**, **Update** e **Elimina**.

Questo articolo è incentrato sull'uso degli strumenti dati in Visual Studio e non tenta di spiegare le tecnologie sottostanti in qualsiasi livello di nidificazione. Si presuppone di avere una certa conoscenza di base con XAML, Entity Framework e SQL. In questo esempio illustra anche architettura Model-View-ViewModel (MVVM), che è standard per le applicazioni WPF. Tuttavia, è possibile copiare questo codice in un'applicazione MVVM con poche modifiche.

## <a name="install-and-connect-to-northwind"></a>Installare e connettersi a Northwind

Questo esempio Usa il database di esempio Northwind e SQL Server Express LocalDB. Se il provider di dati ADO.NET per il prodotto supporta Entity Framework, dovrebbe funzionare altrettanto bene con altri prodotti di database SQL.

1.  Se non si dispone di SQL Server Express LocalDB, installarlo dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio**, è possibile installare LocalDB di SQL Server Express come parte delle **sviluppo desktop .NET** carico di lavoro o come un singolo componente.

2.  Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (**Esplora oggetti di SQL Server** viene installato come parte del **elaborazione ed archiviazione dati** carico di lavoro nel **Visual Studio Installer**.) Espandere la **SQL Server** nodo. Fare doppio clic sull'istanza di Local DB e selezionare **nuova Query**.

       Apre una finestra dell'editor di query.

    2. Copia il [script di Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, termina l'esecuzione di query e viene creato il database Northwind.

3.  [Aggiungere nuove connessioni](../data-tools/add-new-connections.md) per Northwind.

## <a name="configure-the-project"></a>Configurare il progetto

1.  In Visual Studio, scegliere **File** > **New** > **progetto** e quindi creare un nuovo C# applicazione WPF.

2.  Successivamente, aggiungere il pacchetto NuGet di Entity Framework 6. Nelle **Esplora soluzioni**, selezionare il nodo del progetto. Nel menu principale, scegliere **Project** > **Gestisci pacchetti NuGet**.

     ![Gestire la voce di menu pacchetti NuGet](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3.  Nel **Gestisci pacchetti NuGet**, fare clic sui **Sfoglia** collegamento. Entity Framework è probabile che il pacchetto superiore nell'elenco. Fare clic su **installare** nel riquadro destro e seguire le istruzioni. La finestra di Output indica al termine dell'installazione.

     ![Pacchetto NuGet di Entity Framework](../data-tools/media/raddata_vs2015_nuget_ef.png)

4.  A questo punto è possibile usare Visual Studio per creare un modello basato sul database Northwind.

## <a name="create-the-model"></a>Creare il modello

1. Pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Add** > **nuovo elemento**. Nel riquadro sinistro, sotto il C# nodo, scegliere **Data** nel riquadro centrale, scegliere **ADO.NET Entity Data Model**.

   ![Entity Framework modello nuovo elemento di progetto](../data-tools/media/raddata-ef-new-project-item.png)

2. Chiamare il modello `Northwind_model` e scegliere **OK**. Verrà aperta la **Procedura guidata Entity Data Model**. Scegli **Entity Framework Designer dal database** e quindi fare clic su **successivo**.

   ![Modello EF da Database](../data-tools/media/raddata-ef-model-from-database.png)

3. Nella schermata successiva, scegliere di LocalDB Northwind connessione fare clic su **successivo**.

4. Nella pagina successiva della procedura guidata, scegliere quali tabelle, stored procedure e altri oggetti di database da includere nel modello di Entity Framework. Espandere il nodo dbo nella visualizzazione albero e scegliere **clienti**, **ordini**, e **Order Details**. Lasciare le impostazioni predefinite selezionate e fare clic su **fine**.

    ![Scegli oggetti di database per il modello](../data-tools/media/raddata-choose-ef-objects.png)

5. La procedura guidata genera il C# le classi che rappresentano il modello di Entity Framework. Le classi sono plain old C# classi e sono ciò databind all'interfaccia utente WPF. Il *edmx* file descrive le relazioni e altri metadati che associa le classi di oggetti nel database. Il *tt* file sono modelli T4 che generano il codice che opera sul modello e salvare le modifiche al database. È possibile visualizzare tutti i file in **Esplora soluzioni** sotto il nodo Northwind_model:

      ![File del modello EF di Esplora soluzioni](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    Area di progettazione per il *edmx* file consente di modificare alcune proprietà e relazioni nel modello. Non si intende utilizzare la finestra di progettazione in questa procedura dettagliata.

6. Il *tt* file sono di uso generale ed è necessario modificare uno di essi per lavorare con il Data Binding WPF, che richiede ObservableCollections. Nelle **Esplora soluzioni**, espandere il nodo Northwind_model fino a individuare *Northwind_model.tt*. (Assicurarsi che non si lavora nel *. Context.tt* file, che è direttamente sotto la *edmx* file.)

   -   Sostituire le due occorrenze della <xref:System.Collections.ICollection> con <xref:System.Collections.ObjectModel.ObservableCollection%601>.

   -   Sostituire la prima occorrenza di <xref:System.Collections.Generic.HashSet%601> con <xref:System.Collections.ObjectModel.ObservableCollection%601> intorno alla riga 51. Non sostituire la seconda occorrenza della HashSet.

   -   Sostituire l'unica occorrenza di <xref:System.Collections.Generic> (intorno alla riga 431) con <xref:System.Collections.ObjectModel>.

7. Premere **Ctrl**+**MAIUSC**+**B** per compilare il progetto. Al termine della compilazione, le classi del modello sono visibili per la creazione guidata origine dati.

A questo punto si è pronti per associare questo modello per la pagina XAML in modo che si può visualizzare, esplorare e modificare i dati.

## <a name="databind-the-model-to-the-xaml-page"></a>Metodo DataBind il modello per la pagina XAML

È possibile scrivere il codice di associazione dati, ma è molto più semplice consentire a Visual Studio di eseguire questa operazione automaticamente.

1.  Dal menu principale, scegliere **Project** > **Aggiungi nuova origine dati** per visualizzare la **configurazione guidata origine dati**. Scegli **oggetto** poiché si sta associando alle classi di modello, non al database:

     ![Configurazione guidata origine dati con origine oggetto](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2.  Selezionare **cliente**. (Origini per gli ordini vengono generate automaticamente dalla proprietà di navigazione ordini cliente).

     ![Aggiungere le classi di entità come origini dati](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3.  Scegliere **Fine**.

4.  Passare a *MainWindow. XAML* nella visualizzazione codice. È molto il XAML semplice ai fini di questo esempio. Modificare il titolo della finestra principale con un nome più descrittivo e aumentare l'altezza e larghezza a 800 x 600 per il momento. È possibile sempre modificarlo in un secondo momento. Aggiungi ora le definizioni di tre righe alla griglia principale, una riga per i pulsanti di navigazione, uno per i dettagli del cliente e uno per la griglia che mostra gli ordini:

    ```xaml
    <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5.  A questo punto aprire *MainWindow. XAML* in modo che si sta visualizzando, nella finestra di progettazione. In questo modo, il **Zdroje dat** che venga visualizzata come opzione di Visual Studio margine della finestra accanto alla finestra la **della casella degli strumenti**. Fare clic sulla scheda per aprire la finestra, oppure premere else **Shift**+**Alt**+**1!d** oppure scegliere **visualizzazione**  >  **Altri Windows** > **Zdroje dat**. Si intende visualizzare ogni proprietà nella classe di clienti nella propria casella di testo singola. In primo luogo, fare clic sulla freccia nel **clienti** combinata casella e scegliere **dettagli**. Quindi, trascinare il nodo nella parte centrale dell'area di progettazione in modo che la finestra di progettazione che consente di passare nelle righe intermedie da informare. Se si smarrisce il, è possibile specificare la riga manualmente in seguito nel XAML. Per impostazione predefinita, i controlli vengono posizionati verticalmente in un elemento griglia ma a questo punto, è possibile disporle nel modo desiderato del form. Ad esempio, potrebbe avere senso inserire il **nome** casella di testo nella parte superiore, sopra l'indirizzo. L'applicazione di esempio per questo articolo riordina i campi e li Riordina in due colonne.

     ![Associazione dell'origine dati ai clienti sui singoli controlli](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     Nella visualizzazione codice, è ora possibile visualizzare un nuovo `Grid` nella riga 1 (la riga intermedia) dell'elemento padre della griglia. L'elemento padre della griglia è una `DataContext` attributo che fa riferimento a CollectionViewSource che è stato aggiunto al `Windows.Resources` elemento. Dato tale contesto di dati, quando la prima casella di testo viene associato a **indirizzo**, viene eseguito il mapping di tale nome per il `Address` proprietà nell'oggetto `Customer` oggetto in CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6.  Quando un cliente è visibile nella parte superiore della finestra, si desidera vedere metà dello spazio relativi ordini nella parte inferiore. Mostrare gli ordini in un controllo di visualizzazione griglia singolo. Data Binding master-details funzionare come previsto, è importante eseguire l'associazione alla proprietà ordini nella classe di clienti, non per il nodo di ordini separato. Trascinare la proprietà Orders della classe di clienti nella metà inferiore del form, in modo che la finestra di progettazione inserisce nella riga 2:

     ![Trascinare le classi di ordini in formato griglia](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7.  Visual Studio ha generato tutto il codice di associazione che si connette i controlli dell'interfaccia utente per gli eventi del modello. È necessario eseguire, per visualizzare alcuni dati, è sufficiente scrivere il codice per popolare il modello. Innanzitutto, passare al *MainWindow.xaml.cs* e aggiungere un membro dati alla classe MainWindow per il contesto dei dati. Questo oggetto, che è stato generato automaticamente, agisce qualcosa di simile a un controllo che tiene traccia delle modifiche e gli eventi del modello. Inoltre, si aggiungerà la logica di inizializzazione del costruttore. La parte superiore della classe dovrebbe essere simile al seguente:

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     Aggiungere un `using` direttiva Data. Entity portare il metodo di estensione Load nell'ambito:

     ```csharp
     using System.Data.Entity;
     ```

     A questo punto, scorrere verso il basso e trovare il `Window_Loaded` gestore dell'evento. Si noti che Visual Studio ha aggiunto un oggetto CollectionViewSource. Rappresenta l'oggetto NorthwindEntities selezionato al momento della creazione del modello. È possibile aggiungere codice al `Window_Loaded` in modo che l'intero metodo il seguente aspetto:

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8.  Premere **F5**. È consigliabile vedere i dettagli per il cliente prima che è stato recuperato in CollectionViewSource. Si dovrebbe anche relativi ordini nella griglia dei dati. Non è grande, quindi, correggiamo che la formattazione. È anche possibile creare un modo per visualizzare gli altri record ed eseguire operazioni CRUD di base.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Modificare la progettazione della pagina e aggiungere le griglie per i nuovi clienti e ordini

La disposizione predefinita del prodotto da Visual Studio non è ideale per l'applicazione, quindi verranno apportate alcune modifiche manualmente nel XAML. È necessario anche alcuni "Form" (che sono effettivamente griglie) per consentire all'utente aggiungere un nuovo cliente o un ordine. Per poter aggiungere un nuovo cliente e ordine, è necessario un set separato di caselle di testo che non sono associati a dati per il `CollectionViewSource`. Si sarà controllare quali griglia viene visualizzato in qualsiasi momento impostando la proprietà Visible nei metodi del gestore. Infine, si aggiunge un pulsante di eliminazione a ogni riga della griglia di ordini per consentire all'utente di eliminare un singolo ordine.

In primo luogo, aggiungere questi stili per il `Windows.Resources` nell'elemento *MainWindow. XAML*:

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
         <Label Content="Contact Title:" Grid.Row="3" Style="{StaticResource Label}"/>
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
         <Label Content="Contact Title:" Grid.Row="3" Style="{StaticResource Label}"/>
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

Nelle applicazioni Windows Form, ottenere un oggetto di BindingNavigator con i pulsanti per spostarsi tra le righe in un database e l'esecuzione di operazioni CRUD di base. WPF non è incluso un controllo BindingNavigator, ma è abbastanza semplice per crearne uno. È che fare con i pulsanti all'interno di un elemento StackPanel orizzontali e associare i pulsanti con i comandi che sono associati ai metodi nel code-behind.

Esistono quattro parti per la logica di comando: (1) i comandi, (2) le associazioni, (3) i pulsanti e (4) i gestori comando nel code-behind.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Aggiungere i comandi, associazioni e i pulsanti in XAML

1.  In primo luogo, aggiungere i comandi nel *MainWindow. XAML* all'interno del file di `Windows.Resources` elemento:

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

2.  Esegue il mapping di un oggetto CommandBinding un `RoutedUICommand` eventi a un metodo nel code-behind. Aggiungere quanto segue `CommandBindings` elemento dopo il `Windows.Resources` tag di chiusura:

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

3.  A questo punto, aggiungere il `StackPanel` con la navigazione, aggiungere, eliminare e aggiornare i pulsanti. In primo luogo, aggiungere questo stile `Windows.Resources`:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     In secondo luogo, incollare questo codice subito dopo il `RowDefinitions` per l'outer `Grid` elemento, nella parte superiore della pagina XAML:

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

Il code-behind è minimo, ad eccezione di metodi di aggiunta ed eliminazione. Navigazione viene eseguita chiamando metodi sulla proprietà vista di CollectionViewSource. Il `DeleteOrderCommandHandler` illustra come eseguire un'operazione di eliminazione a catena in un ordine. È necessario innanzitutto eliminare Order_Details che esso associati. Il `UpdateCommandHandler` aggiunge un nuovo cliente o un ordine all'insieme, altrimenti aggiorni un cliente esistente o un ordine in base alle modifiche che l'utente ha effettuato nelle caselle di testo.

Aggiungere questi metodi del gestore alla classe MainWindow *MainWindow.xaml.cs*. Se l'oggetto CollectionViewSource per la tabella Customers ha un nome diverso, è necessario modificare il nome in ognuno di questi metodi:

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>Esecuzione dell'applicazione

Premere **F5** per avviare il debug. Si noterà dei clienti e i dati degli ordini popolati nella griglia e i pulsanti di navigazione devono funzionare come previsto. Fare clic su **Commit** per aggiungere un nuovo cliente o un ordine per il modello dopo aver immesso i dati. Fare clic su **annullare** per eseguire il backup all'esterno di un nuovo cliente o un nuovo modulo d'ordine senza salvare i dati. È possibile apportare modifiche agli ordini direttamente nelle caselle di testo e i clienti esistenti e tali modifiche vengono registrate automaticamente al modello.

## <a name="see-also"></a>Vedere anche

- [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Documentazione di Entity Framework](/ef/)