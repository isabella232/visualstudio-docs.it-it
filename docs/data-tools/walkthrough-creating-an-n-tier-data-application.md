---
title: "Procedura dettagliata: Creazione di un'applicazione dati a più livelli"
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 471f0e9b97293bd70457a8f41cb7efddd6acf6c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564802"
---
# <a name="walkthrough-create-an-n-tier-data-application"></a>Procedura dettagliata: Creare un'applicazione dati a più livelli
Le applicazioni dati *a più livelli* sono applicazioni con accesso ai dati e sono separate in più *livelli logici*. La separazione dei componenti dell'applicazione in livelli discreti aumenta la manutenibilità e la scalabilità dell'applicazione mediante l'adozione semplificata di nuove tecnologie che possono essere applicate a un singolo livello senza la necessità di riprogettare l'intera soluzione. L'architettura a più livelli include un livello di presentazione, un livello intermedio e un livello dati. Il livello intermedio include in genere un livello di accesso ai dati, un livello di logica di business e componenti condivisi quali l'autenticazione e la convalida. Il livello dati include un database relazionale. Le applicazioni a più livelli in genere archiviano le informazioni riservate nel livello di accesso ai dati del livello intermedio per mantenere l'isolamento dagli utenti finali che accedono al livello di presentazione. Per altre informazioni, vedere [panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md).

Per separare i vari livelli in un'applicazione a più livelli, è possibile creare progetti discreti per ogni livello da includere nell'applicazione. I dataset tipizzati contengono una proprietà `DataSet Project` che determina in quali progetti deve essere inserito il codice generato del dataset e di `TableAdapter`.

In questa procedura dettagliata è illustrato come separare il codice del dataset e di `TableAdapter` in progetti di librerie di classi discreti usando **Progettazione DataSet**. Dopo aver separato il set di dati e il codice di TableAdapter, si crea una [servizi di Windows Communication Foundation e WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) servizio effettuare chiamate nel livello di accesso ai dati. Infine, creare un'applicazione Windows Forms come livello di presentazione. Questo livello accede ai dati dal servizio dati.

Durante questa procedura dettagliata, si eseguire la procedura seguente:

- Creare una nuova soluzione a più livelli che contiene più progetti.

- Aggiungere due progetti di libreria di classi alla soluzione a più livelli.

- Creare un dataset tipizzato con la **Configurazione guidata origine dati**.

- Separare il generato [TableAdapter](create-and-configure-tableadapters.md) e il codice di set di dati in progetti discreti.

- Creare un servizio Windows Communication Foundation (WCF) per effettuare chiamate nel livello di accesso ai dati.

- Creare funzioni nel servizio per recuperare i dati dal livello di accesso ai dati.

- Creare un'applicazione Windows Form come livello di presentazione.

- Creare i controlli Windows Form associati all'origine dati.

- Scrivere il codice per popolare le tabelle dati.

![collegamento a video](../data-tools/media/playvideo.gif) per una versione video di questo argomento, vedere [Video How to: Creazione di un'applicazione dati a più livelli](http://go.microsoft.com/fwlink/?LinkId=115188).

## <a name="prerequisites"></a>Prerequisiti
Questa procedura dettagliata Usa SQL Server Express LocalDB e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express LocalDB, installarlo dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio**, è possibile installare LocalDB di SQL Server Express come parte delle **sviluppo desktop .NET** carico di lavoro, o come un singolo componente.

2. Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (**Esplora oggetti di SQL Server** viene installato come parte delle **elaborazione ed archiviazione dati** carico di lavoro in Visual Studio Installer.) Espandere la **SQL Server** nodo. Fare doppio clic sull'istanza di Local DB e selezionare **nuova Query**.

       Apre una finestra dell'editor di query.

    2. Copia il [script di Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, termina l'esecuzione di query e viene creato il database Northwind.

## <a name="create-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Creare la raccolta di soluzioni e la classe a più livelli per contenere il dataset (DataEntityTier)
 Il primo passaggio di questa procedura dettagliata prevede la creazione di una soluzione e di due progetti di libreria di classi. La prima libreria di classi contiene il set di dati (tipizzato generato `DataSet` classe e oggetti DataTable che contengono i dati dell'applicazione). Il progetto viene usato come livello di entità di dati dell'applicazione e di norma si trova nel livello intermedio. Il set di dati crea il set di dati iniziale e separa automaticamente il codice in due librerie di classi.

> [!NOTE]
> Assicurarsi di assegnare il nome corretto al progetto e alla soluzione prima di fare clic su **OK**. In tal modo sarà più semplice completare questa procedura dettagliata.

### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Per creare la soluzione a più livelli e la libreria di classi DataEntityTier

1. In Visual Studio sul **File** dal menu **New** > **progetto**.

2. Espandere la **Visual c#** oppure **Visual Basic** nel riquadro di sinistra, quindi selezionare **Windows Desktop**.

3. Nel riquadro centrale selezionare il **libreria di classi** tipo di progetto.

4. Assegnare il nome **DataEntityTier** al progetto.

5. Denominare la soluzione **NTierWalkthrough**, quindi scegliere **OK**.

     Una soluzione NTierWalkthrough che contiene il progetto DataEntityTier viene creata e aggiunta a **Esplora soluzioni**.

## <a name="create-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Creare la libreria di classi per contenere gli oggetti TableAdapter (DataAccessTier)
 Il passaggio successivo alla creazione del progetto DataEntityTier prevede la creazione di un altro progetto di libreria di classi. Questo progetto contiene gli oggetti TableAdapter generato e viene chiamato il *livello di accesso ai dati* dell'applicazione. Tale livello contiene le informazioni richieste per la connessione al database e in genere si trova nel livello intermedio.

### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>Per creare una libreria di classi separata per gli oggetti TableAdapter

1. Fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e scegliere **Aggiungi** > **Nuovo progetto**.

2. Nel **nuovo progetto** finestra di dialogo, nel riquadro centrale, seleziona **libreria di classi**.

3. Denominare il progetto **DataAccessTier** e scegliere **OK**.

     Il progetto DataAccessTier viene creato e aggiunto alla soluzione NTierWalkthrough.

## <a name="create-the-dataset"></a>Creare il set di dati
 Il passaggio successivo consiste nella creazione di un dataset tipizzato. I dataset tipizzati sono creati con la classe dataset (incluso `DataTables` classi) e il `TableAdapter` classi in un singolo progetto. Tutte le classi vengono generate in un unico file. Quando si separa il set di dati e TableAdapter in progetti diversi, è la classe di set di dati che viene spostata in altro progetto, lasciando il `TableAdapter` classi nel progetto originale. Pertanto, è possibile creare il set di dati nel progetto che alla fine conterrà gli oggetti TableAdapter (il progetto DataAccessTier). Creare il set di dati usando il **configurazione guidata origine dati**.

> [!NOTE]
> Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni su come configurare il database di esempio Northwind, vedere [come: Installare i database di esempio](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-dataset"></a>Per creare il dataset

1. Selezionare il **DataAccessTier** nelle **Esplora soluzioni**.

2. Nel **Data** dal menu **Mostra origini dati**.

   Verrà visualizzata la finestra **Origini dati**.

3. Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

4. Nel **scegliere un tipo di origine dati** pagina, selezionare **Database** e quindi selezionare **Next**.

5. Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:

     Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

     -oppure-

     Selezionare **nuova connessione** per aprire il **Aggiungi connessione** nella finestra di dialogo.

6. Se il database richiede una password, selezionare l'opzione per includere dati sensibili e quindi scegliere **successivo**.

    > [!NOTE]
    > Se è stato selezionato un file di database locale al posto della connessione a SQL Server, potrebbe venire richiesto di aggiungere il file al progetto. Scegli **Sì** per aggiungere il file di database al progetto.

7. Selezionare **successivo** nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina.

8. Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database** .

9. Selezionare le caselle di controllo per il **clienti** e **ordini** tabelle e quindi scegliere **fine**.

     NorthwindDataSet viene aggiunto al progetto DataAccessTier e viene visualizzato nella finestra **Origini dati**.

## <a name="separate-the-tableadapters-from-the-dataset"></a>Separare gli oggetti TableAdapter dal Dataset
 Dopo avere creato il dataset, separare la classe DataSet generata dagli oggetti TableAdapter. Questa operazione può essere eseguita impostando la proprietà **Progetto DataSet** sul nome del progetto nel quale archiviare la classe DataSet separata.

### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Per separare gli oggetti TableAdapter dal dataset

1. Fare doppio clic su **NorthwindDataSet.xsd** in **Esplora soluzioni** per aprire il dataset in **Progettazione DataSet**.

2. Selezionare un'area vuota della finestra di progettazione.

3. Trovare il nodo **Progetto DataSet** nella finestra **Proprietà**.

4. Nel **DataSetProject** elenco, selezionare **DataEntityTier**.

5. Scegliere **Compila soluzione** dal menu **Compila**.

   Il dataset e gli oggetti TableAdapter sono separati nei due progetti di libreria di classi. Il progetto che originalmente conteneva l'intero set di dati (`DataAccessTier`) ora contiene solo gli oggetti TableAdapter. Il progetto definito nella **DataSetProject** proprietà (`DataEntityTier`) contiene il set di dati tipizzato: *NorthwindDataSet* (o *NorthwindDataSet.Dataset.Designer.cs*).

> [!NOTE]
> Quando si separano i dataset e gli oggetti TableAdapter (impostando la proprietà **Progetto DataSet**), le classi parziali del dataset presenti nel progetto non vengono spostate automaticamente. Le classi parziali del dataset devono essere spostate manualmente nel progetto di dataset.

## <a name="create-a-new-service-application"></a>Creare una nuova applicazione di servizio
Questa procedura dettagliata viene illustrato come accedere a livello di accesso ai dati tramite un servizio WCF, quindi, creiamo una nuova applicazione di servizio WCF.

### <a name="to-create-a-new-wcf-service-application"></a>Per creare una nuova applicazione del servizio WCF

1. Fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e scegliere **Aggiungi** > **Nuovo progetto**.

2. Nel **nuovo progetto** finestra di dialogo, nel riquadro a sinistra, seleziona **WCF**. Nel riquadro centrale, selezionare **WCF Service Library**.

3. Denominare il progetto **DataService** e selezionare **OK**.

     Il progetto DataService viene creato e aggiunto alla soluzione NTierWalkthrough.

## <a name="create-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Creare i metodi nel livello di accesso ai dati per restituire i dati customers e orders
 Il servizio dati deve chiamare due metodi nel livello di accesso ai dati: `GetCustomers` e `GetOrders`. Questi metodi restituiscono Northwind `Customers` e `Orders` tabelle. Creare il `GetCustomers` e `GetOrders` metodi nel `DataAccessTier` progetto.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Per creare un metodo nel livello di accesso ai dati per restituire la tabella Customers

1. Nelle **Esplora soluzioni**, fare doppio clic su **NorthwindDataSet. xsd** per aprire il set di dati.

2. Fare doppio clic su **CustomersTableAdapter** e fare clic su **Aggiungi Query**.

3. Nella pagina **Seleziona un tipo di comando** lasciare il valore predefinito **Usa istruzioni SQL** e fare clic su **Avanti**.

4. Nella pagina **Seleziona un tipo di query** lasciare il valore predefinito **SELECT** che restituisce righe e fare clic su **Avanti**.

5. Nella pagina **Specifica un'istruzione SQL SELECT** lasciare la query predefinita e fare clic su **Avanti**.

6. Nella sezione **Restituisci un DataTable** della pagina **Scegliere i metodi per generare** digitare **GetCustomers** in **Nome metodo**.

7. Scegliere **Fine**.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Per creare un metodo nel livello di accesso ai dati per restituire la tabella Orders

1. Fare clic con il pulsante destro del mouse su **OrdersTableAdapter** e scegliere **Aggiungi query**.

2. Nella pagina **Seleziona un tipo di comando** lasciare il valore predefinito **Usa istruzioni SQL** e fare clic su **Avanti**.

3. Nella pagina **Seleziona un tipo di query** lasciare il valore predefinito **SELECT** che restituisce righe e fare clic su **Avanti**.

4. Nella pagina **Specifica un'istruzione SQL SELECT** lasciare la query predefinita e fare clic su **Avanti**.

5. Nella sezione **Restituisci un DataTable** della pagina **Scegliere i metodi** per generare digitare **GetOrders** in **Nome metodo**.

6. Scegliere **Fine**.

7. Scegliere **Compila soluzione** dal menu **Compila**.

## <a name="add-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Aggiungere un riferimento all'entità di dati e i livelli di accesso di dati al servizio dati
 Dal momento che il servizio dati richiede le informazioni dal dataset e dagli oggetti TableAdapter, è necessario aggiungere riferimenti ai progetti **DataEntityTier** e **DataAccessTier**.

### <a name="to-add-references-to-the-data-service"></a>Per aggiungere riferimenti al servizio dati

1. In **Esplora soluzioni** fare clic con il pulsante destro su **DataService** e scegliere **Aggiungi riferimento**.

2. Nella finestra di dialogo **Aggiungi riferimento** fare clic sulla scheda **Progetti**.

3. Selezionare entrambi i progetti **DataAccessTier** e **DataEntityTier**.

4. Fare clic su **OK**.

## <a name="add-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Aggiungere le funzioni per il servizio per chiamare i metodi GetCustomers e GetOrders nel livello di accesso ai dati
 Ora che il livello di accesso ai dati contiene i metodi per restituire i dati, creare i metodi nel servizio dati per chiamare i metodi nel livello di accesso ai dati.

> [!NOTE]
> Per i progetti C# è necessario aggiungere un riferimento all'assemby `System.Data.DataSetExtensions` per eseguire la compilazione del codice seguente.

### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Per creare le funzioni GetCustomers e GetOrders nel servizio dati

1. Nel progetto **DataService** fare doppio clic su **IService1.vb** o **IService1.cs**.

2. Aggiungere il codice seguente sotto il commento **Aggiungere qui le operazioni del servizio**:

    ```vb
    <OperationContract()> _
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable

    <OperationContract()> _
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable
    ```

    ```csharp
    [OperationContract]
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();

    [OperationContract]
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();
    ```

3. Nel progetto DataService fare doppio clic su **Service1.vb** o **Service1.cs**.

4. Aggiungere il codice seguente alla classe **Service1**:

    ```vb
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
        Return CustomersTableAdapter1.GetCustomers()
    End Function

    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
        Return OrdersTableAdapter1.GetOrders()
    End Function
    ```

    ```csharp
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
             CustomersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();
        return CustomersTableAdapter1.GetCustomers();
    }
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
             OrdersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();
        return OrdersTableAdapter1.GetOrders();
    }
    ```

5. Scegliere **Compila soluzione** dal menu **Compila**.

## <a name="create-a-presentation-tier-to-display-data-from-the-data-service"></a>Creare un livello di presentazione per visualizzare i dati dal servizio dati
 Ora che la soluzione contiene il servizio dati che dispone di metodi, la chiamata che i dati a livelli di accesso, creare un altro progetto che effettua chiamate nel servizio dati e presentare i dati agli utenti. In questa procedura dettagliata, creare un'applicazione Windows Form; si tratta del livello di presentazione dell'applicazione a più livelli.

### <a name="to-create-the-presentation-tier-project"></a>Per creare il progetto livello di presentazione

1. Fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e scegliere **Aggiungi** > **Nuovo progetto**.

2. Nel **nuovo progetto** finestra di dialogo, nel riquadro a sinistra, seleziona **Windows Desktop**. Nel riquadro centrale, selezionare **App di Windows. Forms**.

3. Assegnare al progetto il nome **PresentationTier** e fare clic su **OK**.

    Il progetto PresentationTier viene creato e aggiunto alla soluzione NTierWalkthrough.

## <a name="set-the-presentationtier-project-as-the-startup-project"></a>Impostare il progetto PresentationTier come progetto di avvio
Impostiamo la **PresentationTier** progetto come progetto di avvio per la soluzione, perché è l'applicazione client effettive che presenta e interagisce con i dati.

### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Impostazione del nuovo livello del progetto come progetto di avvio

- In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **PresentationTier** e scegliere **Imposta come progetto di avvio**.

## <a name="add-references-to-the-presentation-tier"></a>Aggiungere i riferimenti al livello presentazione
 Per accedere ai metodi nel servizio, l'applicazione client PresentationTier richiede un riferimento al servizio dati. È richiesto inoltre un riferimento al dataset per abilitare la condivisione dei tipi da parte del servizio WCF. Fino a quando non si abilita tipo di condivisione tramite il servizio dati, il codice aggiunto per la classe dataset parziale non è disponibile a livello di presentazione. Perché è in genere aggiungere il codice, ad esempio il codice di convalida per la riga e la colonna modifica gli eventi di una tabella di dati, è probabile che si accedere al codice dal client.

### <a name="to-add-a-reference-to-the-presentation-tier"></a>Per aggiungere un riferimento al livello di presentazione

1. Nelle **Esplora soluzioni**, fare doppio clic su **PresentationTier** e selezionare **Aggiungi riferimento**.

2. Nel **Aggiungi riferimento** finestra di dialogo, seleziona la **progetti** scheda.

3. Selezionare **DataEntityTier** e scegliere **OK**.

### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Per aggiungere il riferimento a un servizio al livello di presentazione

1. Nelle **Esplora soluzioni**, fare doppio clic su **PresentationTier** e selezionare **Aggiungi riferimento al servizio**.

2. Nel **Aggiungi riferimento al servizio** finestra di dialogo **Discover**.

3. Selezionare **Service1** e scegliere **OK**.

    > [!NOTE]
    > Se si dispone di più servizi nel computer corrente, selezionare il servizio creato in precedenza in questa procedura dettagliata (il servizio che contiene il `GetCustomers` e `GetOrders` metodi).

## <a name="add-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Aggiunta di DataGridView al form per visualizzare i dati restituiti dal servizio dati
 Dopo l'aggiunta del riferimento a un servizio dati, i dati restituiti dal servizio vengono popolati automaticamente nella finestra **Origini dati**.

### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Per aggiungere due DataGridView associati a dati al form

1. Selezionare il progetto **PresentationTier** in **Esplora soluzioni**.

2. Nella finestra **Origini dati**, espandere **NorthwindDataSet** e trovare il nodo **Customers**.

3. Trascinare il nodo **Customers** in Form1.

4. Nella finestra **Origini dati** espandere il nodo **Customers** e trovare il nodo **Orders** correlato, cioè il nodo **Orders** annidato nel nodo **Customers**.

5. Trascinare il nodo **Orders** correlato in Form1.

6. Fare doppio clic su un'area vuota del form per creare un gestore eventi `Form1_Load`.

7. Aggiungere il codice seguente al gestore eventi `Form1_Load`.

    ```vb
    Dim DataSvc As New ServiceReference1.Service1Client
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)
    ```

    ```csharp
    ServiceReference1.Service1Client DataSvc =
        new ServiceReference1.Service1Client();
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());
    ```

## <a name="increase-the-maximum-message-size-allowed-by-the-service"></a>Aumentare le dimensioni massime del messaggio consentita dal servizio
Il valore predefinito per `maxReceivedMessageSize` non è sufficientemente grande da contenere i dati recuperati dal `Customers` e `Orders` tabelle. Nei passaggi seguenti, è possibile aumentare il valore su 6553600. Si modifica il valore nel client, che aggiorna automaticamente il riferimento al servizio.

> [!NOTE]
> La dimensione predefinita più bassa è usata per limitare l'esposizione ad attacchi Denial of Service (DoS). Per altre informazioni, vedere <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Per aumentare il valore di maxReceivedMessageSize

1. In **Esplora soluzioni** fare doppio clic sul file **app.config** nel progetto **PresentationTier**.

2. Trovare l'attributo di dimensione **maxReceivedMessage** e impostare il valore su `6553600`.

## <a name="test-the-application"></a>Testare l'applicazione
Eseguire l'applicazione premendo **F5**. I dati di `Customers` e `Orders` tabelle viene recuperato dal servizio dati e visualizzato nel form.

## <a name="next-steps"></a>Passaggi successivi
 A seconda dei requisiti dell'applicazione, è possibile eseguire diverse operazioni dopo il salvataggio dei dati correlati nell'applicazione basata su Windows. È possibile ad esempio apportare i seguenti miglioramenti a questa applicazione:

- Aggiungere la convalida al dataset.

- Aggiungere al servizio altri metodi per l'aggiornamento dei dati nel database.

## <a name="see-also"></a>Vedere anche

- [Uso dei set di dati nelle applicazioni a più livelli](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)