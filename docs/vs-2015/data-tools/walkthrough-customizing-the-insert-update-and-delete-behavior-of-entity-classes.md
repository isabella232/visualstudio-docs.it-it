---
title: 'Procedura dettagliata: Personalizzazione di inserimento, aggiornamento ed eliminazione, il comportamento delle classi di entità | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4d8ef69258d9c672bb5deb01b9c2e0972d4e8303
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193544"
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>Procedura dettagliata: Personalizzazione di inserimento, aggiornamento ed eliminazione, il comportamento delle classi di entità
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Il [strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fornisce una superficie di progettazione visiva per la creazione e modifica [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] classi (classi di entità) basate sugli oggetti in un database. Usando [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655), è possibile usare la tecnologia LINQ per accedere ai database SQL. Per altre informazioni, vedere [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
 Per impostazione predefinita, la logica per eseguire gli aggiornamenti viene fornita dal runtime [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]. Nel runtime vengono create istruzioni Insert, Update e Delete predefinite in base allo schema della tabella (definizioni di colonna e informazioni sulla chiave primaria). Quando non si desidera usare il comportamento predefinito, è possibile configurare il comportamento di aggiornamento e definire stored procedure specifiche per eseguire i comandi di inserimento, aggiornamento ed eliminazione necessari per l'uso dei dati nel database. Questa operazione può essere eseguita anche quando non viene generato il comportamento predefinito, ad esempio quando viene eseguito il mapping delle classi di entità alle visualizzazioni. Inoltre, è possibile eseguire l'override del comportamento di aggiornamento predefinito quando il database richiede l'accesso alla tabella tramite stored procedure. Per altre informazioni, vedere [personalizzazione di operazioni usando Stored procedure](http://msdn.microsoft.com/library/aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a).  
  
> [!NOTE]
>  Questa procedura dettagliata richiede la disponibilità del **InsertCustomer**, **UpdateCustomer**, e **DeleteCustomer** stored procedure per il database Northwind. Per informazioni dettagliate su come creare queste stored procedure, vedere [procedura dettagliata: creazione di Stored procedure di aggiornamento per la tabella Customers di Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
 In questa procedura dettagliata vengono forniti i passaggi da completare per eseguire l'override del comportamento in fase di esecuzione LINQ to SQL predefinito per salvare i dati in un database usando stored procedure.  
  
 In questa procedura dettagliata si apprenderà come eseguire le attività seguenti:  
  
-   Creazione di una nuova applicazione Windows Form e aggiunta ad essa di un file [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)].  
  
-   Creazione di una classe di entità con mapping alla tabella Customers di Northwind.  
  
-   Creazione dell'origine dati di un oggetto che fa riferimento alla classe LINQ to SQL Customer.  
  
-   Creazione di un Windows Form che contiene un oggetto <xref:System.Windows.Forms.DataGridView> associato alla classe Customer.  
  
-   Implementazione della funzionalità di salvataggio per il form.  
  
-   Creazione di metodi <xref:System.Data.Linq.DataContext> mediante l'aggiunta di stored procedure a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
-   Configurazione della classe Customer in modo che utilizzi stored procedure per l'esecuzione dei comandi di inserimento, aggiornamento ed eliminazione.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario disporre dei seguenti elementi:  
  
-   Accedere alla versione SQL Server del database di esempio Northwind. Per altre informazioni, vedere [procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
-   Il **InsertCustomer**, **UpdateCustomer**, e **DeleteCustomer** stored procedure per il database Northwind. Per altre informazioni, vedere [procedura dettagliata: creazione di Stored procedure di aggiornamento per la tabella Customers di Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Creazione di un'applicazione e aggiunta di classi LINQ to SQL  
 Poiché verranno usate classi [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] e verranno visualizzati i dati in un Windows Form, creare una nuova applicazione Windows Form e aggiungere un file di classi LINQ to SQL.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-new-windows-application-project-that-contains-linq-to-sql-classes"></a>Per creare un nuovo progetto Applicazione Windows che contenga classi LINQ to SQL  
  
1.  Dal **File** menu, creare un nuovo progetto.  
  
2.  Denominare il progetto **UpdatingwithSProcsWalkthrough**.  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] è supportato nei progetti di [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] e di C#. Pertanto, creare il nuovo progetto in uno di questi linguaggi.  
  
3.  Scegliere il **Windows Forms Application** modello, quindi scegliere **OK**. Per altre informazioni, vedere [le applicazioni Client](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Il progetto UpdatingwithSProcsWalkthrough viene creato e aggiunto alla **Esplora soluzioni**.  
  
4.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
5.  Fare clic sui **classi LINQ to SQL** modello e il tipo **Northwind. dbml** nel **nome** casella.  
  
6.  Fare clic su **Aggiungi**.  
  
     Viene aggiunto al progetto un file di classi LINQ to SQL vuoto (Northwind.dbml) e viene aperto [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Creazione della classe di entità Customer e dell'origine dati di un oggetto  
 Creare [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] le classi che vengono eseguito il mapping alle tabelle di database trascinando le tabelle da **Esplora Server**/**Esplora Database** nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Il risultato è rappresentato da classi di entità LINQ to SQL con mapping alle tabelle nel database. Dopo aver creato le classi di entità, è possibile usarle come origini dati di un oggetto analogamente alle altre classi che dispongono di proprietà pubbliche.  
  
#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Per creare una classe di entità Customer e configurare un'origine dati con tale classe  
  
1.  Nelle **Esplora Server**/**Esplora Database**, individuare la tabella Customer nella versione SQL Server di database di esempio Northwind. Per altre informazioni, vedere [procedura: connettersi al Northwind Database](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
2.  Trascinare il **clienti** nodo dal **Esplora Server**/**Esplora Database** nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] superficie.  
  
     Una classe di entità denominata **cliente** viene creato. che presenta proprietà corrispondenti alle colonne della tabella Customers. La classe di entità è denominata **cliente** (non **clienti**) perché rappresenta un singolo cliente della tabella Customers.  
  
    > [!NOTE]
    >  Viene chiamato questo comportamento di ridenominazione *pluralizzazione*. E può essere attivato o disattivare [finestra di dialogo Opzioni](../ide/reference/options-dialog-box-visual-studio.md). Per altre informazioni, vedere [procedura: attivare e disattivare (O/R Designer) la pluralizzazione](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).  
  
3.  Nel **compilare** menu, fare clic su **Compila UpdatingwithSProcsWalkthrough** per compilare il progetto.  
  
4.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
5.  Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.  
  
6.  Fare clic su **oggetto** nel **scegliere un tipo di origine dati** e quindi fare clic su **Avanti**.  
  
7.  Espandere la **UpdatingwithSProcsWalkthrough** nodo individuare e selezionare il **cliente** classe.  
  
    > [!NOTE]
    >  Se il **cliente** classe non è disponibile, annullare la procedura guidata, compilare il progetto e rieseguire la procedura guidata.  
  
8.  Fare clic su **Finish** per creare l'origine dati e aggiungere il **cliente** classe di entità per il **Zdroje dat** finestra.  
  
## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Creazione di un controllo DataGridView per visualizzare i dati dei clienti in un Windows Form  
 Creare controlli associati alle classi di entità trascinando [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] gli elementi dall'origine dati di **Zdroje dat** finestra in un Windows Form.  
  
#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Per aggiungere controlli associati alle classi di entità  
  
1.  Aprire Form1 nella visualizzazione Progettazione.  
  
2.  Dal **Zdroje dat** finestra, trascinare le **cliente** nodo in Form1.  
  
    > [!NOTE]
    >  Per visualizzare il **Zdroje dat** finestra, fare clic su **Mostra origini dati** sul **dati** menu.  
  
3.  Aprire Form1 nell'editor del codice.  
  
4.  Aggiungere al form il seguente codice, che verrà applicato all'intero form, all'esterno di un metodo specifico ma all'interno della classe Form1:  
  
    ```vb  
    Private NorthwindDataContext1 As New NorthwindDataContext  
    ```  
  
    ```csharp  
    private NorthwindDataContext northwindDataContext1  
        = new NorthwindDataContext();  
  
    ```  
  
5.  Creare un gestore eventi per l'evento `Form_Load` e aggiungere il seguente codice al gestore:  
  
    ```vb  
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers  
    ```  
  
    ```csharp  
    customerBindingSource.DataSource  
        = northwindDataContext1.Customers;  
  
    ```  
  
## <a name="implementing-save-functionality"></a>Implementazione della funzionalità di salvataggio  
 Per impostazione predefinita, il pulsante Salva non è abilitato e la funzionalità di salvataggio non è implementata. Inoltre, quando vengono creati controlli associati a dati per le origini dati di un oggetto, non viene aggiunto codice automaticamente per salvare i dati modificati nel database. Contenuto della sezione viene illustrato come abilitare il pulsante Salva e implementare la funzionalità di salvataggio per gli oggetti [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)].  
  
#### <a name="to-implement-save-functionality"></a>Per implementare la funzionalità di salvataggio  
  
1.  Aprire Form1 nella visualizzazione Progettazione.  
  
2.  Selezionare Salva pulsante il **CustomerBindingNavigator** (il pulsante con icona del disco floppy).  
  
3.  Nel **proprietà** impostare nella finestra di **Enabled** proprietà **True**.  
  
4.  Fare doppio clic sul pulsante Salva per creare un gestore eventi e passare all'editor del codice.  
  
5.  Aggiungere il seguente codice nel gestore eventi del pulsante Salva:  
  
    ```vb  
    NorthwindDataContext1.SubmitChanges()  
    ```  
  
    ```csharp  
    northwindDataContext1.SubmitChanges();  
    ```  
  
## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Override del comportamento predefinito per l'esecuzione degli aggiornamenti (comandi di inserimento, aggiornamento ed eliminazione)  
  
#### <a name="to-override-the-default-update-behavior"></a>Per eseguire l'override del comportamento di aggiornamento predefinito  
  
1.  Aprire il file LINQ to SQL in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Fare doppio clic il **Northwind. dbml** del file in **Esplora soluzioni**.)  
  
2.  Nelle **Esplora Server**/**Esplora Database**, espandere i database Northwind **Stored Procedures** nodo e individuare il  **InsertCustomers**, **UpdateCustomers**, e **DeleteCustomers** stored procedure.  
  
3.  Trascinare tutte e tre le stored procedure in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     Le stored procedure vengono aggiunte al riquadro dei metodi come metodi <xref:System.Data.Linq.DataContext>. Per altre informazioni, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Selezionare il **cliente** classe di entità di [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
5.  Nel **delle proprietà** finestra, seleziona il **Inserisci** proprietà.  
  
6.  Fare clic sui puntini di sospensione (...) accanto a **Usa fase di esecuzione** per aprire il **Configura comportamento** nella finestra di dialogo.  
  
7.  Selezionare **personalizzare**.  
  
8.  Selezionare il **InsertCustomers** metodo le **Personalizza** elenco.  
  
9. Fare clic su **applica** per salvare la configurazione per la classe e al comportamento selezionati.  
  
    > [!NOTE]
    >  È possibile continuare a configurare il comportamento per ogni combinazione classe/comportamento purché faccia clic su **applica** dopo ogni modifica apportata. Se si modifica la classe o un comportamento prima di fare clic **applica**, una finestra di dialogo di avviso che fornisce un'opportunità per applicare eventuali modifiche verrà visualizzati.  
  
10. Selezionare **Update** nel **comportamento** elenco.  
  
11. Selezionare **personalizzare**.  
  
12. Selezionare il **UpdateCustomers** metodo le **Personalizza** elenco.  
  
     Esaminare l'elenco delle **gli argomenti del metodo** e **proprietà della classe** e notare che sono presenti due **gli argomenti del metodo** e due **proprietà della classe**per alcune colonne della tabella. In tal modo, vengono facilitati il rilevamento delle modifiche e la creazione di istruzioni che verifichino la presenza di eventuali violazioni di concorrenza.  
  
13. Mappa il **Original_CustomerID** argomento del metodo per il **CustomerID (Original)** proprietà della classe.  
  
    > [!NOTE]
    >  Per impostazione predefinita, verrà eseguito il mapping degli argomenti di metodo alle proprietà di classe quando i nomi corrispondono. Se i nomi di proprietà vengono modificati e non vi è più corrispondenza tra quelli della tabella e quelli della classe di entità, potrebbe essere necessario selezionare la proprietà di classe equivalente a cui eseguire il mapping nel caso in cui Progettazione relazionale oggetti non sia in grado di determinare il mapping corretto. Inoltre, se gli argomenti del metodo non si dispone delle proprietà di classe valido per eseguire il mapping, è possibile impostare il **proprietà della classe** valore **(nessuno)**.  
  
14. Fare clic su **applica** per salvare la configurazione per la classe e al comportamento selezionati.  
  
15. Selezionare **eliminare** nel **comportamento** elenco.  
  
16. Selezionare **personalizzare**.  
  
17. Selezionare il **DeleteCustomers** metodo le **Personalizza** elenco.  
  
18. Mappa il **Original_CustomerID** argomento del metodo per il **CustomerID (Original)** proprietà della classe.  
  
19. Fare clic su **OK**.  
  
> [!NOTE]
>  Sebbene non sia un problema per questa procedura dettagliata, è opportuno notare che [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] gestisce i valori generati dal database automaticamente per le colonne identity (incremento automatico), rowguidcol (GUID generato dal database) e timestamp durante le operazioni di inserimento e aggiornamento. I valori degli altri tipi di colonne sono costituiti da valori null non previsti. Per restituire i valori generati dal database, è necessario impostare manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> su `true` e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> su uno dei seguenti valori: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> o <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="testing-the-application"></a>Verifica dell'applicazione  
 Eseguire nuovamente l'applicazione per verificare che il **UpdateCustomers** stored procedure aggiorna correttamente il record del cliente nel database.  
  
#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione  
  
1.  Premere F5.  
  
2.  Modificare un record nella griglia per testare il comportamento di Update.  
  
3.  Aggiungere un nuovo record per testare il comportamento di Insert.  
  
4.  Fare clic sul pulsante Salva per salvare le modifiche nel database.  
  
5.  Chiudere il form.  
  
6.  Premere F5 e verificare che il record aggiornato e quello appena inserito siano stati salvati in modo permanente.  
  
7.  Eliminare il nuovo record creato nel passaggio 3 per testare il comportamento di Delete.  
  
8.  Fare clic sul pulsante Salva per inviare le modifiche e rimuovere il record eliminato dal database.  
  
9. Chiudere il form.  
  
10. Premere F5 e verificare che il record eliminato sia stato rimosso dal database.  
  
    > [!NOTE]
    >  Se l'applicazione Usa SQL Server Express Edition, in base al valore di **Copy to Output Directory** proprietà del file di database, le modifiche potrebbero non comparire quando si preme F5 nel passaggio 10. Per altre informazioni, vedere [procedura: gestire i file di dati locale in un progetto](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
## <a name="next-steps"></a>Passaggi successivi  
 A seconda dei requisiti dell'applicazione, è possibile eseguire diverse operazioni dopo la creazione delle classi di entità [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]. È possibile apportare alcuni miglioramenti a questa applicazione, tra cui:  
  
-   Implementazione del controllo della concorrenza durante gli aggiornamenti. Per informazioni, vedere [la concorrenza ottimistica: Panoramica](http://msdn.microsoft.com/library/c2e38512-d0c8-4807-b30a-cb7e30338694).  
  
-   Aggiunta di query LINQ per filtrare i dati. Per informazioni, vedere [Introduzione alle query LINQ (c#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Query LINQ to SQL](http://msdn.microsoft.com/library/f4897aaa-7f44-4c20-a471-b948c2971aae)   
 [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [PAVE quali sono le novità per lo sviluppo di applicazioni dati in Visual Studio 2012](http://msdn.microsoft.com/en-us/3d50d68f-5f44-4915-842f-6d42fce793f1)

