---
title: Personalizzare il comportamento di inserimento/aggiornamento/eliminazione
description: In questa procedura dettagliata personalizzare il comportamento di inserimento, aggiornamento ed eliminazione delle classi di entità usando LINQ (Language-Integrated Query) in strumenti SQL in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cac9f27263fc7d316d308f1f8d906751f419f104
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2020
ms.locfileid: "94997927"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>Procedura dettagliata: personalizzare il comportamento di inserimento, aggiornamento ed eliminazione delle classi di entità

Gli [strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) forniscono un'area di progettazione visiva per la creazione e la modifica di classi LINQ to SQL (classi di entità) basate sugli oggetti in un database. Utilizzando [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index), è possibile utilizzare la tecnologia LINQ per accedere ai database SQL. Per altre informazioni, vedere [LINQ (Language Integrated Query)](/dotnet/csharp/linq/).

Per impostazione predefinita, la logica per eseguire gli aggiornamenti viene fornita dalla LINQ to SQL Runtime. Il runtime crea `Insert` istruzioni, `Update` e predefinite `Delete` in base allo schema della tabella, ovvero le definizioni delle colonne e le informazioni sulla chiave primaria. Quando non si vuole usare il comportamento predefinito, è possibile configurare il comportamento di aggiornamento e definire stored procedure specifiche per eseguire i comandi di inserimento, aggiornamento ed eliminazione necessari per l'uso dei dati nel database. Questa operazione può essere eseguita anche quando non viene generato il comportamento predefinito, ad esempio quando viene eseguito il mapping delle classi di entità alle visualizzazioni. Inoltre, è possibile eseguire l'override del comportamento di aggiornamento predefinito quando il database richiede l'accesso alla tabella tramite stored procedure. Per ulteriori informazioni, vedere [personalizzazione di operazioni utilizzando stored procedure](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).

> [!NOTE]
> In questa procedura dettagliata è richiesta la disponibilità delle stored procedure **InsertCustomer**, **UpdateCustomer** e **DeleteCustomer** per il database Northwind.

In questa procedura dettagliata vengono illustrati i passaggi da seguire per eseguire l'override del comportamento predefinito del LINQ to SQL Runtime per il salvataggio dei dati in un database di tramite stored procedure.

Durante questa procedura dettagliata si apprenderà come eseguire le attività seguenti:

- Creare una nuova Windows Forms Application e aggiungervi un file di LINQ to SQL.

- Creare una classe di entità di cui è stato eseguito il mapping alla `Customers` tabella Northwind.

- Creare un'origine dati oggetto che fa riferimento alla `Customer` classe LINQ to SQL.

- Creare un Windows Form che contiene un oggetto <xref:System.Windows.Forms.DataGridView> associato alla `Customer` classe.

- Implementazione della funzionalità di salvataggio per il form.

- Creare <xref:System.Data.Linq.DataContext> metodi mediante l'aggiunta di stored procedure a **Progettazione relazionale di O/R**.

- Configurare la `Customer` classe per l'utilizzo di stored procedure per l'esecuzione di inserimenti, aggiornamenti ed eliminazioni.

## <a name="prerequisites"></a>Prerequisiti

In questa procedura dettagliata vengono utilizzati SQL Server Express database locale e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express database locale, installarlo dalla [pagina di download SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio** è possibile installare SQL Server Express database locale come parte del carico di lavoro di **elaborazione e archiviazione dei dati** oppure come singolo componente.

2. Installare il database di esempio Northwind attenendosi alla procedura seguente:

    1. In Visual Studio aprire la finestra **Esplora oggetti di SQL Server** . **Esplora oggetti di SQL Server** viene installato come parte del carico di lavoro di **elaborazione e archiviazione dei dati** nel **programma di installazione di Visual Studio**. Espandere il nodo **SQL Server** . Fare clic con il pulsante destro del mouse sull'istanza del database locale e scegliere **nuova query**.

       Si apre una finestra dell'editor di query.

    2. Copiare lo [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query, quindi scegliere il pulsante **Execute (Esegui** ).

       Dopo un breve periodo di tempo, viene completata l'esecuzione della query e viene creato il database Northwind.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Creazione di un'applicazione e aggiunta di classi LINQ to SQL

Poiché si utilizzano classi LINQ to SQL e si visualizzano i dati in un Windows Form, creare una nuova Windows Forms Application e aggiungere un file di classi LINQ to SQL.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>Per creare un nuovo progetto di applicazione Windows Forms che contiene LINQ to SQL classi

1. Nel menu **File** in Visual Studio selezionare **Nuovo** > **Progetto**.

2. Espandere **Visual C#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **desktop di Windows**.

3. Nel riquadro centrale selezionare il tipo di progetto **App Windows Forms** .

4. Denominare il progetto **UpdatingWithSProcsWalkthrough**, quindi scegliere **OK**.

     Il progetto **UpdatingwithSProcsWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.

4. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

5. Fare clic sul modello **Classi LINQ to SQL** e digitare **Northwind.dbml** nella casella **Nome**.

6. Scegliere **Aggiungi**.

     Al progetto viene aggiunto un file di classi di LINQ to SQL vuoto (**Northwind. dbml**) e viene aperto **Progettazione relazionale O** .

## <a name="create-the-customer-entity-class-and-object-data-source"></a>Creare la classe di entità Customer e l'origine dati dell'oggetto

Creare LINQ to SQL classi di cui è stato eseguito il mapping alle tabelle di database trascinando le tabelle da **Esplora server** o **Esplora database** in **Progettazione relazionale** o. Il risultato è rappresentato da classi di entità LINQ to SQL con mapping alle tabelle nel database. Dopo aver creato le classi di entità, è possibile usarle come origini dati di un oggetto analogamente alle altre classi che dispongono di proprietà pubbliche.

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Per creare una classe di entità Customer e configurare un'origine dati con tale classe

1. In **Esplora server** o **Esplora database** individuare la tabella **Customer** nella versione SQL Server del database di esempio Northwind.

2. Trascinare il nodo **Customers** da **Esplora server** o **Esplora database** nell'area **o/R Designer* .

     Viene creata una classe di entità denominata **Customer**, che presenta proprietà corrispondenti alle colonne della tabella Customers. La classe di entità viene denominata **Customer** (e non **Customers**) perché rappresenta un solo cliente della tabella Customers.

    > [!NOTE]
    > Questo comportamento di ridenominazione viene definito *pluralizzazione*. Può essere attivata o disattivata nella finestra di [dialogo Opzioni](../ide/reference/options-dialog-box-visual-studio.md). Per altre informazioni, vedere [procedura: attivare e disattivare la pluralità (O/R Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3. Scegliere **Compila UpdatingwithSProcsWalkthrough** dal menu **Compila** per compilare il progetto.

4. Per aprire la finestra **origini dati** , scegliere **Mostra origini dati** dal menu **dati** .

5. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

6. Nella pagina **Seleziona un tipo di origine dati** fare clic su **Oggetto** e quindi su **Avanti**.

7. Espandere il nodo **UpdatingwithSProcsWalkthrough** e quindi individuare e selezionare la classe **Customer**.

    > [!NOTE]
    > Se la classe **Customer** non è disponibile, chiudere la procedura guidata, compilare il progetto ed eseguire nuovamente la procedura guidata.
8. Fare clic su **Fine** per creare l'origine dati e aggiungere la classe di entità **Customer** alla finestra **Origini dati**.

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Creare un DataGridView per visualizzare i dati del cliente in un Windows Form

Creare controlli associati alle classi di entità trascinando LINQ to SQL elementi dell'origine dati dalla finestra **origini dati** in un Windows Form.

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Per aggiungere controlli associati alle classi di entità

1. Aprire **Form1** nella visualizzazione progettazione.

2. Trascinare il nodo **Customer** dalla finestra **Origini dati** in **Form1**.

    > [!NOTE]
    > Per visualizzare la finestra **Origini dati**, scegliere **Mostra origini dati** dal menu **Dati**.

3. Aprire **Form1** nell'editor del codice.

4. Aggiungere il codice seguente al form, globale al modulo, al di fuori di qualsiasi metodo specifico, ma all'interno della `Form1` classe:

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

## <a name="implement-save-functionality"></a>Implementare la funzionalità di salvataggio

Per impostazione predefinita, il pulsante Salva non è abilitato e la funzionalità di salvataggio non è implementata. Inoltre, quando vengono creati controlli associati a dati per le origini dati di un oggetto, non viene aggiunto codice automaticamente per salvare i dati modificati nel database. In questa sezione viene illustrato come abilitare il pulsante Salva e implementare la funzionalità di salvataggio per gli oggetti LINQ to SQL.

### <a name="to-implement-save-functionality"></a>Per implementare la funzionalità di salvataggio

1. Aprire **Form1** nella visualizzazione progettazione.

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

## <a name="override-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Eseguire l'override del comportamento predefinito per l'esecuzione di aggiornamenti (inserimenti, aggiornamenti ed eliminazioni)

### <a name="to-override-the-default-update-behavior"></a>Per eseguire l'override del comportamento di aggiornamento predefinito

1. Aprire il file di LINQ to SQL in **Progettazione relazionale di O/R**. (Fare doppio clic sul file **Northwind.dbml** in **Esplora soluzioni**.)

2. In **Esplora server** o **Esplora database** espandere il nodo **Stored procedure** dei database Northwind e individuare le stored procedure **InsertCustomers**, **UpdateCustomers** e **DeleteCustomers**.

3. Trascinare tutte e tre le stored procedure nella **finestra di progettazione di O/R**.

     Le stored procedure vengono aggiunte al riquadro dei metodi come metodi <xref:System.Data.Linq.DataContext>. Per altre informazioni, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Selezionare la classe di entità **Customer** in **O/R Designer**.

5. Nella finestra **Proprietà** selezionare la proprietà **Insert**.

6. Fare clic sui puntini di sospensione (**...**) accanto a **Usa fase di esecuzione** per aprire la finestra di dialogo **Configura comportamento**.

7. Selezionare **Personalizza**.

8. Selezionare il metodo **InsertCustomers** nell'elenco **Personalizza**.

9. Fare clic su **Applica** per salvare la configurazione relativa alla classe e al comportamento selezionati.

    > [!NOTE]
    > È possibile continuare a configurare il comportamento per ogni combinazione di classe/comportamento purché si faccia clic su **Applica** dopo ogni modifica apportata. Se si modifica la classe o il comportamento prima di fare clic su **applica**, viene visualizzata una finestra di dialogo di avviso che offre la possibilità di applicare le modifiche.

10. Selezionare **Aggiorna** nell'elenco **Comportamento**.

11. Selezionare **Personalizza**.

12. Selezionare il metodo **UpdateCustomers** nell'elenco **Personalizza**.

     Controllare l'elenco di **Argomenti metodo** e **Proprietà classe** e notare che sono disponibili due **Argomenti metodo** e due **Proprietà classe** per alcune colonne nella tabella. In tal modo, vengono facilitati il rilevamento delle modifiche e la creazione di istruzioni che verifichino la presenza di eventuali violazioni di concorrenza.

13. Eseguire il mapping dell'argomento di metodo **Original_CustomerID** alla proprietà di classe **CustomerID (Original)**.

    > [!NOTE]
    > Per impostazione predefinita, verrà eseguito il mapping degli argomenti di metodo alle proprietà di classe quando i nomi corrispondono. Se i nomi di proprietà vengono modificati e non vi è più corrispondenza tra quelli della tabella e quelli della classe di entità, potrebbe essere necessario selezionare la proprietà di classe equivalente di cui eseguire il mapping nel caso in cui **Object Relational Designer** non sia in grado di determinare il mapping corretto. Inoltre, se per gli argomenti di metodo non sono disponibili proprietà di classe valide per il mapping, è possibile impostare il valore **Proprietà classe** su **(Nessuna)**.

14. Fare clic su **Applica** per salvare la configurazione relativa alla classe e al comportamento selezionati.

15. Selezionare **Elimina** nell'elenco **Comportamento**.

16. Selezionare **Personalizza**.

17. Selezionare il metodo **DeleteCustomers** nell'elenco **Personalizza**.

18. Eseguire il mapping dell'argomento di metodo **Original_CustomerID** alla proprietà di classe **CustomerID (Original)**.

19. Fare clic su **OK**.

> [!NOTE]
> Sebbene non sia un problema per questa particolare procedura dettagliata, vale la pena notare che LINQ to SQL gestisce automaticamente i valori generati dal database per le colonne Identity (incremento automatico), ROWGUIDCOL (GUID generato dal database) e timestamp durante gli inserimenti e gli aggiornamenti. I valori degli altri tipi di colonne sono costituiti da valori null non previsti. Per restituire i valori generati dal database, è necessario impostare manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> su `true` e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> su uno degli elementi seguenti: [AutoSync. always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync. OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)o [AutoSync. OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="test-the-application"></a>Test dell'applicazione

Eseguire nuovamente l'applicazione per verificare che la stored procedure **UpdateCustomers** aggiorni correttamente il record dei clienti nel database.

1. Premere **F5**.

2. Modificare un record nella griglia per testare il comportamento di aggiornamento.

3. Aggiungere un nuovo record per testare il comportamento di inserimento.

4. Fare clic sul pulsante Salva per salvare le modifiche nel database.

5. Chiudere il form.

6. Premere **F5** e verificare che il record aggiornato e il record appena inserito siano salvati in permanenza.

7. Eliminare il nuovo record creato nel passaggio 3 per testare il comportamento di eliminazione.

8. Fare clic sul pulsante Salva per inviare le modifiche e rimuovere il record eliminato dal database.

9. Chiudere il form.

10. Premere **F5** e verificare che il record eliminato sia stato rimosso dal database.

    > [!NOTE]
    > Se l'applicazione usa SQL Server Express Edition, a seconda del valore della proprietà **Copia nella directory di output** del file di database, è possibile che le modifiche non vengano visualizzate quando si preme **F5** nel passaggio 10.

## <a name="next-steps"></a>Passaggi successivi

A seconda dei requisiti dell'applicazione, è possibile eseguire diverse operazioni dopo avere creato LINQ to SQL classi di entità. È possibile apportare alcuni miglioramenti a questa applicazione, tra cui:

- Implementazione del controllo della concorrenza durante gli aggiornamenti. Per informazioni, vedere [concorrenza ottimistica: Panoramica](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).

- Aggiunta di query LINQ per filtrare i dati. Per informazioni, vedere [Introduzione alle query LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="see-also"></a>Vedi anche

- [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metodi DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Query di LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)
