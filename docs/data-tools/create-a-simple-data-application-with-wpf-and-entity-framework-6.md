---
title: App dati semplice con WPF e Entity Framework 6
description: Questa procedura dettagliata illustra come creare una semplice app forms-over-data in Visual Studio con Windows Presentation Foundation (WPF) e Entity Framework 6.
ms.custom: SEO-VS-2020
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 664752c1d984a8ae7ccce105c8fd7842e209c571795e72782e7755dbe21479c6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347726"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Creare un'applicazione dati semplice con WPF ed Entity Framework 6

Questa procedura dettagliata illustra come creare un'applicazione di base "forms over data" in Visual Studio. L'app usa SQL Server Local DB, il database Northwind, Entity Framework 6 (non Entity Framework Core) e Windows Presentation Foundation per .NET Framework (non .NET Core). Illustra come eseguire il data binding di base con una visualizzazione master-dettagli e include anche uno strumento di navigazione  associazione personalizzato con i pulsanti Sposta successivo **,** Sposta precedente **,** Sposta all'inizio **,** Sposta alla fine **,** Aggiorna ed **Elimina**.

Questo articolo è in particolare sull'uso degli strumenti per i dati in Visual Studio e non tenta di spiegare in modo approfondito le tecnologie sottostanti. Si presuppone che l'utente abbia una conoscenza di base di XAML, Entity Framework e SQL. In questo esempio non viene inoltre illustrata l'architettura Model-View-ViewModel (MVVM), che è standard per le applicazioni WPF. Tuttavia, è possibile copiare questo codice nella propria applicazione MVVM con poche modifiche.

## <a name="install-and-connect-to-northwind"></a>Installare e connettersi a Northwind

In questo esempio vengono SQL Server Express Local DB e il database di esempio Northwind. Se il provider ADO.NET per il prodotto supporta Entity Framework, dovrebbe funzionare anche con altri SQL di database.

1. Se non si dispone di SQL Server Express Local DB, installarlo dalla pagina [di download](https://www.microsoft.com/sql-server/sql-server-editions-express)SQL Server Express o tramite il Programma di installazione di Visual Studio **.** Nel **programma di installazione di Visual Studio**, è possibile installare SQL Server Express Local DB nel contesto del carico di lavoro **Sviluppo per desktop .NET** o come componente singolo.

2. Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio aprire la finestra **SQL Server Esplora oggetti** dati. (**SQL Server Esplora oggetti** viene installato come parte del carico **di** lavoro Elaborazione ed archiviazione dati **nel Programma di installazione di Visual Studio**. Espandere il **SQL Server** nodo . Fare clic con il pulsante destro del mouse sull Local DB e **scegliere Nuova query.**

       Verrà visualizzata una finestra dell'editor di query.

    2. Copiare [lo script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere **il pulsante** Esegui.

       Dopo un breve periodo di tempo, l'esecuzione della query termina e viene creato il database Northwind.

3. [Aggiungere nuove connessioni](../data-tools/add-new-connections.md) per Northwind.

## <a name="configure-the-project"></a>Configurare il progetto

1. In Visual Studio creare un nuovo progetto di **app WPF** C#.

2. Aggiungere il NuGet per Entity Framework 6. In **Esplora soluzioni** selezionare il nodo del progetto. Nel menu principale scegliere Gestisci **Project**  >  **pacchetti NuGet pacchetti**.

     ![Voce NuGet di menu Gestisci pacchetti](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3. Nel **NuGet Gestione pacchetti** fare clic sul **collegamento** Sfoglia. Entity Framework è probabilmente il primo pacchetto nell'elenco. Fare **clic** su Installa nel riquadro destro e seguire le istruzioni. La finestra Output indica al termine dell'installazione.

     ![Entity Framework NuGet pacchetto](../data-tools/media/raddata_vs2015_nuget_ef.png)

4. È ora possibile usare Visual Studio per creare un modello basato sul database Northwind.

## <a name="create-the-model"></a>Creare il modello

1. Fare clic con il pulsante destro del mouse sul nodo **del Esplora soluzioni** e **scegliere Aggiungi**  >  **nuovo elemento.** Nel riquadro sinistro, sotto il nodo C#, scegliere **Dati** e nel riquadro centrale scegliere **ADO.NET Entity Data Model**.

   ![Entity Framework nuovo elemento del modello](../data-tools/media/raddata-ef-new-project-item.png)

2. Chiamare il modello `Northwind_model` e scegliere **OK.** Verrà **visualizzata Entity Data Model guidata.** Scegliere **EF Designer dal database e** quindi fare clic su **Avanti.**

   ![Modello di EF dal database](../data-tools/media/raddata-ef-model-from-database.png)

3. Nella schermata successiva immettere o scegliere la connessione Local DB Northwind (ad esempio, (localdb)\MSSQLLocalDB), specificare il database Northwind e fare clic su **Avanti.**

4. Nella pagina successiva della procedura guidata scegliere quali tabelle, stored procedure e altri oggetti di database includere nel modello Entity Framework dati. Espandere il nodo dbo nella visualizzazione albero e scegliere **Customers,** **Orders** e **Order Details.** Lasciare selezionate le impostazioni predefinite e fare clic su **Fine.**

    ![Scegliere gli oggetti di database per il modello](../data-tools/media/raddata-choose-ef-objects.png)

5. La procedura guidata genera le classi C# che rappresentano il Entity Framework modello. Le classi sono semplici classi C# e sono ciò che viene databind all'interfaccia utente WPF. Il file *con estensione edmx* descrive le relazioni e altri metadati che associano le classi agli oggetti nel database. I *file con estensione tt* sono modelli T4 che generano il codice che opera sul modello e salva le modifiche nel database. È possibile visualizzare tutti questi file nel **Esplora soluzioni** sotto il Northwind_model seguente:

      ![Esplora soluzioni file di modello di EF](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    L'area di progettazione per il file *con estensione edmx* consente di modificare alcune proprietà e relazioni nel modello. In questa procedura dettagliata non verrà utilizzata la finestra di progettazione.

6. I *file con estensione tt* sono di uso generico ed è necessario modificarli per usare il data binding WPF, che richiede ObservableCollections. In **Esplora soluzioni** espandere il nodo Northwind_model fino a trovare *Northwind_model.tt*. Assicurarsi di non essere in *. Context.tt,* che si trova direttamente sotto il file *con estensione edmx.*

   - Sostituire le due occorrenze di <xref:System.Collections.ICollection> con <xref:System.Collections.ObjectModel.ObservableCollection%601> .

   - Sostituire la prima occorrenza di <xref:System.Collections.Generic.HashSet%601> con circa la riga <xref:System.Collections.ObjectModel.ObservableCollection%601> 51. Non sostituire la seconda occorrenza di HashSet.

   - Sostituire l'unica occorrenza <xref:System.Collections.Generic> di (intorno alla riga 431) con <xref:System.Collections.ObjectModel> .

7. Premere **CTRL** + **MAIUSC** + **B** per compilare il progetto. Al termine della compilazione, le classi del modello sono visibili alla procedura guidata delle origini dati.

A questo punto è possibile associare questo modello alla pagina XAML in modo da poter visualizzare, esplorare e modificare i dati.

## <a name="databind-the-model-to-the-xaml-page"></a>Associazione dati del modello alla pagina XAML

È possibile scrivere codice di data binding personalizzato, ma è molto più semplice Visual Studio eseguire questa operazione.

1. Dal menu principale scegliere Aggiungi **Project**  >  **dati** per visualizzare la **Configurazione guidata origine dati.** Scegliere **Oggetto** perché si sta associando alle classi del modello, non al database:

     ![Configurazione guidata origine dati con origine oggetto](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2. Espandere il nodo per il progetto e selezionare **Customer**. Le origini per gli ordini vengono generate automaticamente dalla proprietà di navigazione Orders in Customer.

     ![Aggiungere classi di entità come origini dati](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3. Fare clic su **Fine**.

4. Passare a *MainWindow.xaml* nella visualizzazione Codice. Ai fini di questo esempio, il codice XAML è semplice. Modificare il titolo di MainWindow in modo che sia più descrittivo e aumentare altezza e larghezza a 600 x 800 per il momento. È sempre possibile modificarlo in un secondo momento. Aggiungere ora queste tre definizioni di riga alla griglia principale, una riga per i pulsanti di spostamento, una per i dettagli del cliente e una per la griglia che mostra gli ordini:

    ```xaml
        <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5. Aprire ora *MainWindow.xaml* in modo da visualizzarlo nella finestra di progettazione. In questo modo **la finestra Origini** dati viene visualizzata come opzione nel margine della finestra Visual Studio accanto alla casella degli **strumenti**. Fare clic sulla scheda per aprire la finestra oppure premere MAIUSC + **ALT** + **D**   >    >  o scegliere Visualizza altre Windows dati . Ogni proprietà della classe Customers verrà visualizzata nella propria casella di testo. Per prima cosa, fare clic sulla freccia nella **casella combinata Clienti** e scegliere **Dettagli**. Trascinare quindi il nodo nella parte centrale dell'area di progettazione in modo che la finestra di progettazione sappia che deve essere inserito nella riga centrale. Se la si sposti in modo erto, puoi specificare la riga manualmente in un secondo momento nel codice XAML. Per impostazione predefinita, i controlli vengono posizionati verticalmente in un elemento della griglia, ma a questo punto è possibile disporli nel modo che si desidera nel form. Ad esempio, potrebbe essere opportuno posizionare la casella di testo **Nome** sopra l'indirizzo. L'applicazione di esempio per questo articolo riordina i campi e li riorganizza in due colonne.

     ![Associazione di origini dati dei clienti a singoli controlli](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     Nella visualizzazione codice è ora possibile visualizzare un nuovo elemento nella riga `Grid` 1 (la riga centrale) della griglia padre. L'elemento Grid padre `DataContext` ha un attributo che fa riferimento a un collectionViewSource che è stato aggiunto all'elemento `Windows.Resources` . Dato il contesto dati, quando la prima casella di testo viene associata a **Address**, tale nome viene mappato alla proprietà `Address` nell'oggetto corrente in `Customer` CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Quando un cliente è visibile nella metà superiore della finestra, si vogliono visualizzare gli ordini nella metà inferiore. Gli ordini vengono visualizzati in un singolo controllo visualizzazione griglia. Per il funzionamento previsto del data binding master-dettagli, è importante eseguire l'associazione alla proprietà Orders nella classe Customers, non al nodo Orders separato. Trascinare la proprietà Orders della classe Customers nella metà inferiore del form, in modo che la finestra di progettazione la inserisca nella riga 2:

     ![Trascinare le classi Orders come griglia](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7. Visual Studio ha generato tutto il codice di associazione che connette i controlli dell'interfaccia utente agli eventi nel modello. Per visualizzare alcuni dati, è necessario scrivere codice per popolare il modello. Passare prima di tutto a *MainWindow.xaml.cs* e aggiungere un membro dati alla classe MainWindow per il contesto dati. Questo oggetto, generato automaticamente, agisce come un controllo che tiene traccia delle modifiche e degli eventi nel modello. Si aggiungeranno anche i membri dati CollectionViewSource per clienti e ordini e la logica di inizializzazione del costruttore associata. La parte superiore della classe dovrebbe essere simile alla seguente:

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs" id="Snippet1":::

     Aggiungere una `using` direttiva per System.Data.Entity per portare il metodo di estensione Load nell'ambito:

     ```csharp
     using System.Data.Entity;
     ```

     A questo punto, scorrere verso il basso e trovare il `Window_Loaded` gestore dell'evento . Si noti Visual Studio ha aggiunto un oggetto CollectionViewSource. Rappresenta l'oggetto NorthwindEntities selezionato durante la creazione del modello. È già stato aggiunto, quindi non è necessario qui. Sostituire il codice in in modo `Window_Loaded` che il metodo sia ora simile al seguente:

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs" id="Snippet2":::


8. Premere **F5**. Verranno visualizzati i dettagli per il primo cliente recuperato in CollectionViewSource. Nella griglia dati dovrebbero essere visualizzati anche gli ordini. La formattazione non è ideale, quindi è possibile correggerlo. È anche possibile creare un modo per visualizzare gli altri record ed eseguire operazioni CRUD di base.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Modificare la progettazione della pagina e aggiungere griglie per nuovi clienti e ordini

La disposizione predefinita prodotta da Visual Studio non è ideale per l'applicazione, quindi in questo caso verrà fornito il codice XAML finale da copiare nel codice. Sono necessari anche alcuni "moduli" (che in realtà sono griglie) per consentire all'utente di aggiungere un nuovo cliente o un nuovo ordine. Per poter aggiungere un nuovo cliente e un nuovo ordine, è necessario un set separato di caselle di testo non associate a dati a `CollectionViewSource` . È possibile controllare la griglia visualizzata dall'utente in qualsiasi momento impostando la proprietà Visible nei metodi del gestore. Infine, si aggiunge un pulsante Elimina a ogni riga della griglia Orders per consentire all'utente di eliminare un singolo ordine.

Aggiungere prima di tutto questi stili `Windows.Resources` all'elemento in *MainWindow.xaml:*

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

Sostituire quindi l'intera griglia esterna con questo markup:

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

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Aggiungere pulsanti per esplorare, aggiungere, aggiornare ed eliminare

Nelle Windows Forms si ottiene un oggetto BindingNavigator con pulsanti per spostarsi tra le righe in un database ed eseguire operazioni CRUD di base. WPF non fornisce bindingNavigator, ma è abbastanza semplice crearne uno. Puoi farlo con i pulsanti all'interno di uno StackPanel orizzontale e associare i pulsanti ai comandi associati ai metodi nel code-behind.

La logica dei comandi è in quattro parti: (1) i comandi, (2) le associazioni, (3) i pulsanti e (4) i gestori di comandi nel code-behind.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Aggiungere comandi, associazioni e pulsanti in XAML

1. Aggiungere prima di tutto i comandi nel file *MainWindow.xaml* all'interno `Windows.Resources` dell'elemento :

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

2. CommandBinding esegue il mapping `RoutedUICommand` di un evento a un metodo nel code-behind. Aggiungere questo `CommandBindings` elemento dopo il tag di `Windows.Resources` chiusura:

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

3. Aggiungere ora con `StackPanel` i pulsanti di spostamento, aggiunta, eliminazione e aggiornamento. Per prima cosa, aggiungere questo stile a `Windows.Resources` :

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     In secondo momento, incollare questo codice subito dopo `RowDefinitions` per l'elemento `Grid` esterno, verso la parte superiore della pagina XAML:

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

Il code-behind è minimo, ad eccezione dei metodi di aggiunta ed eliminazione. La navigazione viene eseguita chiamando metodi sulla proprietà View di CollectionViewSource. Mostra `DeleteOrderCommandHandler` come eseguire un'eliminazione a catena in un ordine. È necessario prima eliminare i Order_Details associati. aggiunge un nuovo cliente o ordine alla raccolta oppure aggiorna semplicemente un cliente o un ordine esistente con le modifiche apportate dall'utente `UpdateCommandHandler` nelle caselle di testo.

Aggiungere questi metodi del gestore alla classe MainWindow in *MainWindow.xaml.cs.* Se collectionViewSource per la tabella Customers ha un nome diverso, devi modificare il nome in ognuno di questi metodi:

:::code language="csharp" source="../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs" id="Snippet3":::


## <a name="run-the-application"></a>Eseguire l'applicazione

Premere **F5** per avviare il debug. Nella griglia dovrebbero essere visualizzati i dati relativi a clienti e ordini e i pulsanti di spostamento dovrebbero funzionare come previsto. Fare clic **su Commit** per aggiungere un nuovo cliente o un nuovo ordine al modello dopo aver immesso i dati. Fare clic **su Annulla** per uscire da un modulo nuovo cliente o nuovo ordine senza salvare i dati. È possibile apportare modifiche ai clienti e agli ordini esistenti direttamente nelle caselle di testo e tali modifiche vengono scritte automaticamente nel modello.

## <a name="see-also"></a>Vedi anche

- [Visual Studio data tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Documentazione di Entity Framework](/ef/)
