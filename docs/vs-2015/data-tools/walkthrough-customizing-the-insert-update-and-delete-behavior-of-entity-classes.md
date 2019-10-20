---
title: 'Procedura dettagliata: personalizzazione del comportamento di inserimento, aggiornamento ed eliminazione delle classi di entità | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9901d917de2babf4992519ffe6b360454542aad1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602565"
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>Procedura dettagliata: Personalizzazione del comportamento di inserimento, aggiornamento ed eliminazione delle classi di entità
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli [strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) forniscono un'area di progettazione visiva per la creazione e la modifica di classi [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] (classi di entità) basate sugli oggetti in un database. Utilizzando [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655), è possibile utilizzare la tecnologia LINQ per accedere ai database SQL. Per altre informazioni, vedere [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).

 Per impostazione predefinita, la logica per eseguire gli aggiornamenti viene fornita dal runtime [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]. Nel runtime vengono create istruzioni Insert, Update e Delete predefinite in base allo schema della tabella (definizioni di colonna e informazioni sulla chiave primaria). Quando non si desidera usare il comportamento predefinito, è possibile configurare il comportamento di aggiornamento e definire stored procedure specifiche per eseguire i comandi di inserimento, aggiornamento ed eliminazione necessari per l'uso dei dati nel database. Questa operazione può essere eseguita anche quando non viene generato il comportamento predefinito, ad esempio quando viene eseguito il mapping delle classi di entità alle visualizzazioni. Inoltre, è possibile eseguire l'override del comportamento di aggiornamento predefinito quando il database richiede l'accesso alla tabella tramite stored procedure. Per ulteriori informazioni, vedere [personalizzazione di operazioni utilizzando stored procedure](https://msdn.microsoft.com/library/aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a).

> [!NOTE]
> In questa procedura dettagliata è richiesta la disponibilità delle stored procedure **InsertCustomer**, **UpdateCustomer** e **DeleteCustomer** per il database Northwind.

 In questa procedura dettagliata vengono forniti i passaggi da completare per eseguire l'override del comportamento in fase di esecuzione LINQ to SQL predefinito per salvare i dati in un database usando stored procedure.

 In questa procedura dettagliata si apprenderà come eseguire le attività seguenti:

- Creazione di una nuova applicazione Windows Form e aggiunta ad essa di un file [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)].

- Creazione di una classe di entità con mapping alla tabella Customers di Northwind.

- Creazione dell'origine dati di un oggetto che fa riferimento alla classe LINQ to SQL Customer.

- Creazione di un Windows Form che contiene un oggetto <xref:System.Windows.Forms.DataGridView> associato alla classe Customer.

- Implementazione della funzionalità di salvataggio per il form.

- Creazione di metodi <xref:System.Data.Linq.DataContext> mediante l'aggiunta di stored procedure a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

- Configurazione della classe Customer in modo che utilizzi stored procedure per l'esecuzione dei comandi di inserimento, aggiornamento ed eliminazione.

## <a name="prerequisites"></a>Prerequisites
 Per completare questa procedura dettagliata, è necessario disporre dei seguenti elementi:

- Accedere alla versione SQL Server del database di esempio Northwind.

- Stored procedure **InsertCustomer**, **UpdateCustomer**e **DeleteCustomer** per il database Northwind.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Creazione di un'applicazione e aggiunta di classi LINQ to SQL
 Poiché verranno usate classi [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] e verranno visualizzati i dati in un Windows Form, creare una nuova applicazione Windows Form e aggiungere un file di classi LINQ to SQL.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-a-new-windows-application-project-that-contains-linq-to-sql-classes"></a>Per creare un nuovo progetto Applicazione Windows che contenga classi LINQ to SQL

1. Creare un nuovo progetto dal menu **file** .

2. Denominare il progetto **UpdatingwithSProcsWalkthrough**.

    > [!NOTE]
    > [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] è supportato nei progetti di [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] e di C#. Pertanto, creare il nuovo progetto in uno di questi linguaggi.

3. Fare clic sul modello **applicazione Windows Forms** e fare clic su **OK**. Per ulteriori informazioni, vedere [applicazioni client](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Il progetto UpdatingwithSProcsWalkthrough viene creato e aggiunto a **Esplora soluzioni**.

4. Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

5. Fare clic sul modello **Classi LINQ to SQL** e digitare **Northwind.dbml** nella casella **Nome**.

6. Fare clic su **Aggiungi**.

     Viene aggiunto al progetto un file di classi LINQ to SQL vuoto (Northwind.dbml) e viene aperto [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Creazione della classe di entità Customer e dell'origine dati di un oggetto
 Creare [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] classi di cui è stato eseguito il mapping alle tabelle di database trascinando le tabelle da **Esplora server** /**Esplora database** nella [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Il risultato è rappresentato da classi di entità LINQ to SQL con mapping alle tabelle nel database. Dopo aver creato le classi di entità, è possibile usarle come origini dati di un oggetto analogamente alle altre classi che dispongono di proprietà pubbliche.

#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Per creare una classe di entità Customer e configurare un'origine dati con tale classe

1. In **Esplora server** /**Esplora database**individuare la tabella Customer nella versione SQL Server del database di esempio Northwind.

2. Trascinare il nodo **Customers** da **Esplora server** /**Esplora database** sull'area [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Viene creata una classe di entità denominata **Customer**, che presenta proprietà corrispondenti alle colonne della tabella Customers. La classe di entità viene denominata **Customer** (e non **Customers**) perché rappresenta un solo cliente della tabella Customers.

    > [!NOTE]
    > Questo comportamento di ridenominazione viene definito *pluralizzazione*. Può essere attivata o disattivata nella finestra di [dialogo Opzioni](../ide/reference/options-dialog-box-visual-studio.md). Per altre informazioni, vedere [procedura: attivare e disattivare la pluralità (O/R Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3. Scegliere **Compila UpdatingwithSProcsWalkthrough** dal menu **Compila** per compilare il progetto.

4. Scegliere **Mostra origini dati** dal menu **Dati**.

5. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

6. Nella pagina **Seleziona un tipo di origine dati** fare clic su **Oggetto** e quindi su **Avanti**.

7. Espandere il nodo **UpdatingwithSProcsWalkthrough** e quindi individuare e selezionare la classe **Customer**.

    > [!NOTE]
    > Se la classe **Customer** non è disponibile, chiudere la procedura guidata, compilare il progetto ed eseguire nuovamente la procedura guidata.

8. Fare clic su **Fine** per creare l'origine dati e aggiungere la classe di entità **Customer** alla finestra **Origini dati**.

## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Creazione di un controllo DataGridView per visualizzare i dati dei clienti in un Windows Form
 Creare controlli associati alle classi di entità trascinando [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] elementi dell'origine dati dalla finestra **origini dati** in un Windows Form.

#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Per aggiungere controlli associati alle classi di entità

1. Aprire Form1 nella visualizzazione Progettazione.

2. Dalla finestra **origini dati** trascinare il nodo **Customer** su Form1.

    > [!NOTE]
    > Per visualizzare la finestra **Origini dati**, scegliere **Mostra origini dati** dal menu **Dati**.

3. Aprire Form1 nell'editor del codice.

4. Aggiungere al form il seguente codice, che verrà applicato all'intero form, all'esterno di un metodo specifico ma all'interno della classe Form1:

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();

    ```

5. Creare un gestore eventi per l'evento `Form_Load` e aggiungere il seguente codice al gestore:

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

1. Aprire Form1 nella visualizzazione Progettazione.

2. Selezionare il pulsante Salva in **CustomerBindingNavigator** (il pulsante con l'icona del disco floppy).

3. Nella finestra **Proprietà** impostare la proprietà **Enabled** su **True**.

4. Fare doppio clic sul pulsante Salva per creare un gestore eventi e passare all'editor del codice.

5. Aggiungere il seguente codice nel gestore eventi del pulsante Salva:

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Override del comportamento predefinito per l'esecuzione degli aggiornamenti (comandi di inserimento, aggiornamento ed eliminazione)

#### <a name="to-override-the-default-update-behavior"></a>Per eseguire l'override del comportamento di aggiornamento predefinito

1. Aprire il file LINQ to SQL in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Fare doppio clic sul file **Northwind.dbml** in **Esplora soluzioni**.)

2. In **Esplora server** /**Esplora database**espandere il nodo **stored procedure** dei database Northwind e individuare le stored procedure **InsertCustomers**, **UpdateCustomers**e **DeleteCustomers** .

3. Trascinare tutte e tre le stored procedure in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Le stored procedure vengono aggiunte al riquadro dei metodi come metodi <xref:System.Data.Linq.DataContext>. Per altre informazioni, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Selezionare la classe di entità **Customer** nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

5. Nella finestra **Proprietà** selezionare la proprietà **Insert**.

6. Fare clic sui puntini di sospensione (...) accanto a **Usa runtime** per aprire la finestra di dialogo **Configura comportamento** .

7. Selezionare **Personalizza**.

8. Selezionare il metodo **InsertCustomers** nell'elenco **Personalizza**.

9. Fare clic su **Applica** per salvare la configurazione relativa alla classe e al comportamento selezionati.

    > [!NOTE]
    > È possibile continuare a configurare il comportamento per ogni combinazione di classe/comportamento purché si faccia clic su **Applica** dopo ogni modifica apportata. Se si modifica la classe o il comportamento prima di fare clic su **applica**, viene visualizzata una finestra di dialogo di avviso che consente di applicare le modifiche apportate.

10. Selezionare **Aggiorna** nell'elenco **Comportamento**.

11. Selezionare **Personalizza**.

12. Selezionare il metodo **UpdateCustomers** nell'elenco **Personalizza**.

     Controllare l'elenco di **Argomenti metodo** e **Proprietà classe** e notare che sono disponibili due **Argomenti metodo** e due **Proprietà classe** per alcune colonne nella tabella. In tal modo, vengono facilitati il rilevamento delle modifiche e la creazione di istruzioni che verifichino la presenza di eventuali violazioni di concorrenza.

13. Eseguire il mapping dell'argomento di metodo **Original_CustomerID** alla proprietà di classe **CustomerID (Original)** .

    > [!NOTE]
    > Per impostazione predefinita, verrà eseguito il mapping degli argomenti di metodo alle proprietà di classe quando i nomi corrispondono. Se i nomi di proprietà vengono modificati e non vi è più corrispondenza tra quelli della tabella e quelli della classe di entità, potrebbe essere necessario selezionare la proprietà di classe equivalente a cui eseguire il mapping nel caso in cui Progettazione relazionale oggetti non sia in grado di determinare il mapping corretto. Inoltre, se per gli argomenti di metodo non sono disponibili proprietà di classe valide per il mapping, è possibile impostare il valore **Proprietà classe** su **(Nessuna)** .

14. Fare clic su **Applica** per salvare la configurazione relativa alla classe e al comportamento selezionati.

15. Selezionare **Elimina** nell'elenco **Comportamento**.

16. Selezionare **Personalizza**.

17. Selezionare il metodo **DeleteCustomers** nell'elenco **Personalizza**.

18. Eseguire il mapping dell'argomento di metodo **Original_CustomerID** alla proprietà di classe **CustomerID (Original)** .

19. Fare clic su **OK**.

> [!NOTE]
> Sebbene non sia un problema per questa procedura dettagliata, è opportuno notare che [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] gestisce i valori generati dal database automaticamente per le colonne identity (incremento automatico), rowguidcol (GUID generato dal database) e timestamp durante le operazioni di inserimento e aggiornamento. I valori degli altri tipi di colonne sono costituiti da valori null non previsti. Per restituire i valori generati dal database, è necessario impostare manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> su `true` e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> su uno dei seguenti valori: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> o <xref:System.Data.Linq.Mapping.AutoSync>.

## <a name="testing-the-application"></a>Verifica dell'applicazione
 Eseguire nuovamente l'applicazione per verificare che la stored procedure **UpdateCustomers** aggiorni correttamente il record dei clienti nel database.

#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione

1. Premere F5.

2. Modificare un record nella griglia per testare il comportamento di Update.

3. Aggiungere un nuovo record per testare il comportamento di Insert.

4. Fare clic sul pulsante Salva per salvare le modifiche nel database.

5. Chiudere il form.

6. Premere F5 e verificare che il record aggiornato e quello appena inserito siano stati salvati in modo permanente.

7. Eliminare il nuovo record creato nel passaggio 3 per testare il comportamento di Delete.

8. Fare clic sul pulsante Salva per inviare le modifiche e rimuovere il record eliminato dal database.

9. Chiudere il form.

10. Premere F5 e verificare che il record eliminato sia stato rimosso dal database.

    > [!NOTE]
    > Se l'applicazione usa SQL Server Express Edition, a seconda del valore della proprietà **copia nella directory di output** del file di database, è possibile che le modifiche non vengano visualizzate quando si preme F5 nel passaggio 10.

## <a name="next-steps"></a>Passaggi successivi
 A seconda dei requisiti dell'applicazione, è possibile eseguire diverse operazioni dopo la creazione delle classi di entità [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]. È possibile apportare alcuni miglioramenti a questa applicazione, tra cui:

- Implementazione del controllo della concorrenza durante gli aggiornamenti. Per informazioni, vedere [concorrenza ottimistica: Panoramica](https://msdn.microsoft.com/library/c2e38512-d0c8-4807-b30a-cb7e30338694).

- Aggiunta di query LINQ per filtrare i dati. Per informazioni, vedere [Introduzione alle query LINQ (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).

## <a name="see-also"></a>Vedere anche
 [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [LINQ to SQL le query](https://msdn.microsoft.com/library/f4897aaa-7f44-4c20-a471-b948c2971aae) sui [metodi DataContext (o/r designer)](../data-tools/datacontext-methods-o-r-designer.md) [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (o/r designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [pavimentazione delle novità Sviluppo di applicazioni per dati in Visual Studio 2012](https://msdn.microsoft.com/3d50d68f-5f44-4915-842f-6d42fce793f1)
