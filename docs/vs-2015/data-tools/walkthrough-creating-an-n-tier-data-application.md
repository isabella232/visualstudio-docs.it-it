---
title: "Procedura dettagliata: creazione di un'applicazione dati a più livelli | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: 51
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bd77006eda03b716e3c54c0b5b52ac633a383377
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299589"
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>Procedura dettagliata: creazione di un'applicazione dati a più livelli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le applicazioni dati a più livelli * sono applicazioni che accedono ai dati e sono separate in più livelli logici o *livelli*. La separazione dei componenti dell'applicazione in livelli discreti aumenta la manutenibilità e la scalabilità dell'applicazione mediante l'adozione semplificata di nuove tecnologie che possono essere applicate a un singolo livello senza la necessità di riprogettare l'intera soluzione. L'architettura a più livelli include un livello di presentazione, un livello intermedio e un livello dati. Il livello intermedio include in genere un livello di accesso ai dati, un livello di logica di business e componenti condivisi quali l'autenticazione e la convalida. Il livello dati include un database relazionale. Le applicazioni a più livelli in genere archiviano le informazioni riservate nel livello di accesso ai dati del livello intermedio per mantenere l'isolamento dagli utenti finali che accedono al livello di presentazione. Per altre informazioni, vedere [Panoramica delle applicazioni dati](../data-tools/n-tier-data-applications-overview.md)a più livelli.

 Per separare i vari livelli in un'applicazione a più livelli, è possibile creare progetti discreti per ogni livello da includere nell'applicazione. I dataset tipizzati contengono una proprietà `DataSet Project` che determina in quali progetti deve essere inserito il codice generato del dataset e di `TableAdapter`.

 In questa procedura dettagliata è illustrato come separare il codice del dataset e di `TableAdapter` in progetti di librerie di classi discreti usando **Progettazione DataSet**. Dopo aver separato il set di dati e il codice TableAdapter, si creerà un [Windows Communication Foundation servizi e WCF Data Services nel servizio di Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) per effettuare chiamate al livello di accesso ai dati. Infine, si creerà un'applicazione Windows Form come livello di presentazione. Questo livello accede ai dati dal servizio dati.

 Durante questa procedura dettagliata, verranno eseguiti i passaggi seguenti:

- Creare una nuova soluzione a più livelli che contiene più progetti.

- Aggiungere due progetti di libreria di classi alla soluzione a più livelli.

- Creare un dataset tipizzato con la **Configurazione guidata origine dati**.

- Separare gli [oggetti TableAdapter](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) e il codice del set di dati generati in progetti distinti.

- Creare un servizio Windows Communication Foundation (WCF) per effettuare chiamate nel livello di accesso ai dati.

- Creare funzioni nel servizio per recuperare i dati dal livello di accesso ai dati.

- Creare un'applicazione Windows Form come livello di presentazione.

- Creare i controlli Windows Form associati all'origine dati.

- Scrivere il codice per popolare le tabelle dati.

  ![collegamento al video](../data-tools/media/playvideo.gif "PlayVideo") Per una versione video di questo argomento, vedere [procedura: creazione di un'applicazione dati a più livelli](https://go.microsoft.com/fwlink/?LinkId=115188).

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario:

- Accedere al database di esempio Northwind.

## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Creazione della soluzione a più livelli e della libreria di classi per contenere il dataset (DataEntityTier)
 Il primo passaggio di questa procedura dettagliata prevede la creazione di una soluzione e di due progetti di libreria di classi. La prima libreria di classi conterrà il dataset (la classe DataSet tipizzato e gli oggetti DataTable generati che conterranno i dati dell'applicazione). Il progetto viene usato come livello di entità di dati dell'applicazione e di norma si trova nel livello intermedio. Il Progettazione DataSet viene utilizzato per creare il set di dati iniziale e separare automaticamente il codice nelle due librerie di classi.

> [!NOTE]
> Assicurarsi di assegnare il nome corretto al progetto e alla soluzione prima di fare clic su **OK**. In tal modo sarà più semplice completare questa procedura dettagliata.

#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Per creare la soluzione a più livelli e la libreria di classi DataEntityTier

1. Creare un nuovo progetto dal menu **file** .

    > [!NOTE]
    > Il **Progettazione DataSet** è supportato nei progetti [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] C# e. Creare il nuovo progetto in uno di questi linguaggi

2. Nel riquadro **Tipi progetto** della finestra di dialogo **nuovo progetto** fare clic su **Windows**.

3. Fare clic sul modello **libreria di classi** .

4. Assegnare il nome **DataEntityTier** al progetto.

5. Assegnare alla soluzione il nome **NTierWalkthrough**.

6. fare clic su **OK**.

     Una soluzione NTierWalkthrough che contiene il progetto DataEntityTier viene creata e aggiunta a **Esplora soluzioni**.

## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Creazione della libreria di classi per contenere gli oggetti TableAdapter (DataAccessTier)
 Il passaggio successivo alla creazione del progetto DataEntityTier prevede la creazione di un altro progetto di libreria di classi. Questo progetto conterrà i `TableAdapter`generati e viene chiamato livello di *accesso ai dati* dell'applicazione. Tale livello contiene le informazioni richieste per la connessione al database e in genere si trova nel livello intermedio.

#### <a name="to-create-the-new-class-library-for-the-tableadapters"></a>Per creare la nuova libreria di classi per gli oggetti TableAdapter

1. Dal menu **file** aggiungere un nuovo progetto alla soluzione NTierWalkthrough.

2. Nel riquadro **modelli** della finestra di dialogo **nuovo progetto** fare clic su **libreria di classi**.

3. Denominare il progetto **DataAccessTier** e fare clic su **OK**.

     Il progetto DataAccessTier viene creato e aggiunto alla soluzione NTierWalkthrough.

## <a name="creating-the-dataset"></a>Creazione del set di dati
 Il passaggio successivo consiste nella creazione di un dataset tipizzato. I dataset tipizzati sono creati con la classe DataSet (comprese le classi DataTable) e le classi `TableAdapter`, in un singolo progetto. Tutte le classi vengono generate in un unico file. Quando si separano il set di dati e `TableAdapter`in progetti diversi, si tratta della classe DataSet spostata nell'altro progetto, lasciando le classi `TableAdapter` nel progetto originale. Di conseguenza, è necessario creare il dataset nel progetto che alla fine conterrà gli oggetti `TableAdapter` (il progetto DataAccessTier). Il set di dati verrà creato tramite la **Configurazione guidata origine dati**.

> [!NOTE]
> Per creare la connessione, è necessario avere accesso al database di esempio Northwind.

#### <a name="to-create-the-dataset"></a>Per creare il dataset

1. Fare clic su DataAccessTier in **Esplora soluzioni**.

2. Scegliere **Mostra origini dati** dal menu **Dati**.

3. Nella finestra **origini dati** fare clic su **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

4. Nella pagina **scegliere un tipo di origine dati** fare clic su **database** e quindi su **Avanti**.

5. Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:

     Se disponibile nell'elenco a discesa, scegliere la connessione dati al database di esempio Northwind.

     -oppure-

     Fare clic su **nuova connessione** per aprire la finestra di dialogo **Aggiungi connessione** .

6. Se il database richiede una password, selezionare l'opzione che consente di includere dati riservati, quindi fare clic su **Avanti**.

    > [!NOTE]
    > Se è stato selezionato un file di database locale al posto della connessione a SQL Server, potrebbe venire richiesto di aggiungere il file al progetto. Fare clic su **Sì** per aggiungere il file di database al progetto.

7. Fare clic su **Avanti** nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** .

8. Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database** .

9. Fare clic sulle caselle di controllo per le tabelle **Customers** e **Orders** , quindi fare clic su **fine**.

     NorthwindDataSet viene aggiunto al progetto DataAccessTier e viene visualizzato nella finestra **Origini dati**.

## <a name="separating-the-tableadapters-from-the-dataset"></a>Separazione degli oggetti TableAdapter dal dataset
 Dopo avere creato il dataset, separare la classe DataSet generata dagli oggetti TableAdapter. Questa operazione può essere eseguita impostando la proprietà **Progetto DataSet** sul nome del progetto nel quale archiviare la classe DataSet separata.

#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Per separare gli oggetti TableAdapter dal dataset

1. Fare doppio clic su **NorthwindDataSet.xsd** in **Esplora soluzioni** per aprire il dataset in **Progettazione DataSet**.

2. Fare clic su un'area vuota della finestra di progettazione.

3. Trovare il nodo **Progetto DataSet** nella finestra **Proprietà**.

4. Nell'elenco **progetto DataSet** fare clic su **DataEntityTier**.

5. Scegliere **Compila soluzione** dal menu **Compila**.

   Il dataset e gli oggetti TableAdapter sono separati nei due progetti di libreria di classi. Il progetto che originalmente conteneva l'intero dataset (DataAccessTier) ora contiene solo gli oggetti TableAdapter. Il progetto designato nella proprietà del **progetto DataSet** (DataEntityTier) contiene il DataSet tipizzato: NorthwindDataSet. DataSet. designer. vb (o NorthwindDataSet.DataSet.designer.cs).

> [!NOTE]
> Quando si separano i dataset e gli oggetti TableAdapter (impostando la proprietà **Progetto DataSet**), le classi parziali del dataset presenti nel progetto non vengono spostate automaticamente. Le classi parziali del dataset devono essere spostate manualmente nel progetto di dataset.

## <a name="creating-a-new-service-application"></a>Creazione di una nuova applicazione di servizio
 Dal momento che questa procedura dettagliata spiega come accedere al livello di accesso ai dati con un servizio WCF, è necessario creare una nuova applicazione del servizio WCF.

#### <a name="to-create-a-new-wcf-service-application"></a>Per creare una nuova applicazione del servizio WCF

1. Dal menu **file** aggiungere un nuovo progetto alla soluzione NTierWalkthrough.

2. Nel riquadro **Tipi progetto** della finestra di dialogo **nuovo progetto** fare clic su **WCF**. Nel riquadro **modelli** fare clic su **libreria del servizio WCF**.

3. Assegnare al progetto il nome **DataService** e fare clic su **OK**.

     Il progetto DataService viene creato e aggiunto alla soluzione NTierWalkthrough.

## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Creazione di metodi nel livello di accesso ai dati per restituire i dati dei clienti e degli ordini
 Il servizio dati deve chiamare due metodi nel livello di accesso ai dati: GetCustomers e GetOrders. Questi metodi restituiscono le tabelle Customers e Orders di Northwind. Creare i metodi GetCustomers e GetOrders nel progetto DataAccessTier.

#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Per creare un metodo nel livello di accesso ai dati per restituire la tabella Customers

1. In **Esplora soluzioni**fare doppio clic su NorthwindDataSet. xsd per aprire il set di dati nel Progettazione DataSet.

2. Fare clic con il pulsante destro del mouse su CustomersTableAdapter e scegliere **Aggiungi query** per modificare il TableAdapter.

3. Nella pagina **Seleziona un tipo di comando** lasciare il valore predefinito **Usa istruzioni SQL** e fare clic su **Avanti**.

4. Nella pagina **Seleziona un tipo di query** lasciare il valore predefinito **SELECT** che restituisce righe e fare clic su **Avanti**.

5. Nella pagina **Specifica un'istruzione SQL SELECT** lasciare la query predefinita e fare clic su **Avanti**.

6. Nella sezione **Restituisci un DataTable** della pagina **Scegliere i metodi per generare** digitare **GetCustomers** in **Nome metodo**.

7. Fare clic su **Fine**.

#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Per creare un metodo nel livello di accesso ai dati per restituire la tabella Orders

1. Fare clic con il pulsante destro del mouse su OrdersTableAdapter e scegliere **Aggiungi query**.

2. Nella pagina **Seleziona un tipo di comando** lasciare il valore predefinito **Usa istruzioni SQL** e fare clic su **Avanti**.

3. Nella pagina **Seleziona un tipo di query** lasciare il valore predefinito **SELECT** che restituisce righe e fare clic su **Avanti**.

4. Nella pagina **Specifica un'istruzione SQL SELECT** lasciare la query predefinita e fare clic su **Avanti**.

5. Nella sezione **Restituisci un DataTable** della pagina **Scegliere i metodi** per generare digitare **GetOrders** in **Nome metodo**.

6. Fare clic su **Fine**.

7. Scegliere **Compila soluzione** dal menu **Compila**.

## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Aggiunta di un riferimento ai livelli di entità di dati e di accesso ai dati nel servizio dati
 Dal momento che il servizio dati richiede le informazioni dal dataset e dagli oggetti TableAdapter, è necessario aggiungere riferimenti ai progetti DataEntityTier e DataAccessTier.

#### <a name="to-add-references-to-the-data-service"></a>Per aggiungere riferimenti al servizio dati

1. Fare clic con il pulsante destro del mouse su DataService in **Esplora soluzioni** e scegliere **Aggiungi riferimento**.

2. Nella finestra di dialogo **Aggiungi riferimento** fare clic sulla scheda **Progetti**.

3. Selezionare entrambi i progetti **DataAccessTier** e **DataEntityTier**.

4. fare clic su **OK**.

## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Aggiunta di funzioni al servizio per chiamare i metodi GetCustomers e GetOrders nel livello di accesso ai dati
 Ora che il livello di accesso ai dati contiene i metodi per restituire i dati, creare i metodi nel servizio dati per chiamare i metodi nel livello di accesso ai dati.

> [!NOTE]
> Per i progetti C# è necessario aggiungere un riferimento all'assemby `System.Data.DataSetExtensions` per eseguire la compilazione del codice seguente.

#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Per creare le funzioni GetCustomers e GetOrders nel servizio dati

1. Nel progetto **DataService** fare doppio clic su IService1. vb o IService1.cs.

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

3. Nel progetto DataService fare doppio clic su Service1.vb o Service1.cs.

4. Aggiungere il codice seguente alla classe Service1:

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

## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>Creazione di un livello di presentazione per visualizzare i dati dal servizio dati
 Ora che la soluzione contiene il servizio dati con i metodi che effettuano chiamate nel livello di accesso ai dati, creare un altro progetto che effettuerà le chiamate nel servizio dati e presenterà i dati agli utenti. In questa procedura dettagliata, creare un'applicazione Windows Form; si tratta del livello di presentazione dell'applicazione a più livelli.

#### <a name="to-create-the-presentation-tier-project"></a>Per creare il progetto livello di presentazione

1. Dal menu **file** aggiungere un nuovo progetto alla soluzione NTierWalkthrough.

2. Nel riquadro **Tipi progetto** della finestra di dialogo **nuovo progetto** fare clic su **Windows**. Nel riquadro **Modelli** scegliere **Applicazione Windows Form**.

3. Assegnare al progetto il nome **PresentationTier** e fare clic su **OK**.

4. Il progetto PresentationTier viene creato e aggiunto alla soluzione NTierWalkthrough.

## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>Impostazione del progetto PresentationTier come progetto di avvio
 Dal momento che il livello di presentazione è in realtà l'applicazione client usata per presentare i dati e interagire con essi, è necessario impostare il progetto PresentationTier come progetto di avvio.

#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Impostazione del nuovo livello del progetto come progetto di avvio

- In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **PresentationTier** e scegliere **Imposta come progetto di avvio**.

## <a name="adding-references-to-the-presentation-tier"></a>Aggiunta di riferimenti al livello di presentazione
 Per accedere ai metodi nel servizio, l'applicazione client PresentationTier richiede un riferimento al servizio dati. È richiesto inoltre un riferimento al dataset per abilitare la condivisione dei tipi da parte del servizio WCF. Se non si abilita la condivisione dei tipi con il servizio dati, il codice aggiunto alla classe DataSet parziale non sarà disponibile per il livello di presentazione. Dal momento che di norma si aggiunge codice, ad esempio il codice per la convalida, agli eventi di modifica di righe e colonne di una tabella dati, probabilmente sarà necessario accedere al codice dal client.

#### <a name="to-add-a-reference-to-the-presentation-tier"></a>Per aggiungere un riferimento al livello di presentazione

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su PresentationTier e scegliere **Aggiungi riferimento**.

2. Nella finestra di dialogo **Aggiungi riferimento** fare clic sulla scheda **progetti** .

3. Selezionare **DataEntityTier** e fare clic su **OK**.

#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Per aggiungere il riferimento a un servizio al livello di presentazione

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su PresentationTier e fare clic su **Aggiungi riferimento al servizio**.

2. Nella finestra di dialogo **Aggiungi riferimento al servizio** fare clic su **Individua**.

3. Selezionare **Service1** e fare clic su **OK**.

    > [!NOTE]
    > Se sono presenti più servizi nel computer in uso, selezionare il servizio creato in precedenza in questa procedura dettagliata, ossia quello contenente i metodi GetCustomers e GetOrders.

## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Aggiunta di DataGridView al form per visualizzare i dati restituiti dal servizio dati
 Dopo l'aggiunta del riferimento a un servizio dati, i dati restituiti dal servizio vengono popolati automaticamente nella finestra **Origini dati**.

#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Per aggiungere due DataGridView associati a dati al form

1. In **Esplora soluzioni**selezionare il progetto PresentationTier.

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

## <a name="increasing-the-maximum-message-size-allowed-by-the-service"></a>Aumento della dimensione massima dei messaggi consentita dal servizio
 Dal momento che il servizio restituisce i dati dalle tabelle Customers e Orders, il valore predefinito per maxReceivedMessageSize non è sufficiente per contenere i dati e deve essere aumentato. Per questa procedura dettagliata si imposterà il valore su 6553600. Il valore verrà cambiato nel client e il riferimento al servizio verrà aggiornato automaticamente.

> [!NOTE]
> La dimensione predefinita più bassa è usata per limitare l'esposizione ad attacchi Denial of Service (DoS). Per altre informazioni, vedere <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Per aumentare il valore di maxReceivedMessageSize

1. In **Esplora soluzioni**fare doppio clic sul file app. config nel progetto PresentationTier.

2. Trovare l'attributo di dimensione **maxReceivedMessage** e impostare il valore su `6553600`.

## <a name="testing-the-application"></a>Test dell'applicazione
 Eseguire l'applicazione. I dati vengono recuperati dal servizio dati e visualizzati nel form.

#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione

1. Premere F5.

2. I dati delle tabelle Customers e Orders vengono recuperati dal servizio dati e visualizzati nel form.

## <a name="next-steps"></a>Passaggi successivi
 A seconda dei requisiti dell'applicazione, è possibile eseguire diverse operazioni dopo il salvataggio dei dati correlati nell'applicazione basata su Windows. È possibile ad esempio apportare i seguenti miglioramenti a questa applicazione:

- Aggiungere la convalida al dataset. Per informazioni, vedere [procedura dettagliata: aggiunta della convalida a un'applicazione dati a più livelli](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265).

- Aggiungere al servizio altri metodi per l'aggiornamento dei dati nel database.

## <a name="see-also"></a>Vedere anche
 [Usare i set di dati nelle applicazioni a più livelli](../data-tools/work-with-datasets-in-n-tier-applications.md) l' [aggiornamento gerarchico](../data-tools/hierarchical-update.md) per [l'accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
