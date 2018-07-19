---
title: 'Procedura dettagliata: Personalizzazione di inserimento, aggiornamento ed eliminazione, il comportamento delle classi di entità'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fb01ef51c0a44047e2caf2f23634ebe741cd2dcb
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174978"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>Procedura dettagliata: Personalizzare l'insert, update e il comportamento di eliminazione delle classi di entità

Il [gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fornisce una superficie di progettazione visiva per la creazione e modifica di LINQ alle classi di SQL (classi di entità) basate sugli oggetti in un database. Usando [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index), è possibile usare la tecnologia LINQ per accedere ai database SQL. Per altre informazioni, vedere [LINQ (Language-Integrated query)](/dotnet/csharp/linq/).

Per impostazione predefinita, la logica per eseguire aggiornamenti avviene tramite il runtime LINQ to SQL. Il runtime crea predefinito `Insert`, `Update`, e `Delete` istruzioni basati sullo schema della tabella (definizioni di colonna e informazioni sulla chiave primarie). Quando non si desidera utilizzare il comportamento predefinito, è possibile configurare il comportamento di aggiornamento e definire stored procedure specifiche per l'esecuzione di comandi di inserimento, aggiornamenti ed eliminazioni necessarie per lavorare con i dati nel database. Questa operazione può essere eseguita anche quando non viene generato il comportamento predefinito, ad esempio quando viene eseguito il mapping delle classi di entità alle visualizzazioni. Inoltre, è possibile eseguire l'override del comportamento di aggiornamento predefinito quando il database richiede l'accesso alla tabella tramite stored procedure. Per altre informazioni, vedere [personalizzazione di operazioni utilizzando stored procedure](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).

> [!NOTE]
> Questa procedura dettagliata richiede la disponibilità del **InsertCustomer**, **UpdateCustomer**, e **DeleteCustomer** stored procedure per il database Northwind.

In questa procedura dettagliata vengono forniti i passaggi da completare per eseguire l'override del comportamento in fase di esecuzione LINQ to SQL predefinito per salvare i dati in un database usando stored procedure.

Durante questa procedura dettagliata si apprenderà come eseguire le attività seguenti:

-   Creare una nuova applicazione Windows Form e aggiungere il file SQL ad esso un LINQ.

-   Creare una classe di entità che viene eseguito il mapping di Northwind `Customers` tabella.

-   Creare un'origine dati di oggetto che fa riferimento a LINQ to SQL `Customer` classe.

-   Creare un modulo di Windows che contiene un <xref:System.Windows.Forms.DataGridView> associato ai `Customer` classe.

-   Implementazione della funzionalità di salvataggio per il form.

-   Creare <xref:System.Data.Linq.DataContext> metodi mediante l'aggiunta di stored procedure per il **O/R Designer**.

-   Configurare il `Customer` classe usare stored procedure per eseguire operazioni di inserimento, aggiornamento ed Elimina.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata Usa SQL Server Express LocalDB e il database di esempio Northwind.

1.  Se non si dispone di SQL Server Express LocalDB, installarlo dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio**, è possibile installare LocalDB di SQL Server Express come parte delle **elaborazione ed archiviazione dati** carico di lavoro, o come un singolo componente.

2.  Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (**Esplora oggetti di SQL Server** installa come parte delle **elaborazione ed archiviazione dati** carico di lavoro nel **programma di installazione di Visual Studio**.) Espandere la **SQL Server** nodo. Fare doppio clic sull'istanza di Local DB e selezionare **nuova Query**.

       Apre una finestra dell'editor di query.

    2. Copia il [script di Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, termina l'esecuzione di query e viene creato il database Northwind.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Creazione di un'applicazione e l'aggiunta di LINQ alle classi di SQL

Poiché vengono utilizzate con LINQ alle classi di SQL e visualizzare i dati in un modulo di Windows, creare una nuova applicazione Windows Form e aggiungere un LINQ al file di classi di SQL.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>Per creare un nuovo progetto Windows Forms Application contenente LINQ alle classi di SQL

1. In Visual Studio sul **File** dal menu **New** > **progetto**.

2. Espandere la **Visual c#** oppure **Visual Basic** nel riquadro di sinistra, quindi selezionare **Windows Desktop**.

3. Nel riquadro centrale selezionare il **App di Windows. Forms** tipo di progetto.

4. Denominare il progetto **UpdatingWithSProcsWalkthrough**, quindi scegliere **OK**.

     Il **UpdatingWithSProcsWalkthrough** progetto viene creato e aggiunto alla **Esplora soluzioni**.

4.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

5.  Fare clic sui **classi LINQ to SQL** modello e il tipo **Northwind. dbml** nel **nome** casella.

6.  Fare clic su **Aggiungi**.

     Un file LINQ to vuoto classi SQL (**Northwind. dbml**) viene aggiunto al progetto e il **O/R Designer** apre.

## <a name="create-the-customer-entity-class-and-object-data-source"></a>Creare l'origine di dati dei clienti classe e oggetto dell'entità

Creare classi SQL che vengono eseguito il mapping alle tabelle di database trascinando le tabelle da LINQ to **Esplora Server** oppure **Esplora Database** nel **O/R Designer**. Il risultato è rappresentato da classi di entità LINQ to SQL con mapping alle tabelle nel database. Dopo aver creato le classi di entità, è possibile usarle come origini dati di un oggetto analogamente alle altre classi che dispongono di proprietà pubbliche.

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Per creare una classe di entità Customer e configurare un'origine dati con tale classe

1.  Nella **Esplora Server** oppure **Esplora Database**, individuare il **cliente** tabella nella versione SQL Server di database di esempio Northwind.

2.  Trascinare il **clienti** nodo dal **Esplora Server** o **Esplora Database** nel **O/R Designer* superficie.

     Una classe di entità denominata **cliente** viene creato. che presenta proprietà corrispondenti alle colonne della tabella Customers. La classe di entità è denominata **cliente** (non **clienti**) perché rappresenta un singolo cliente della tabella Customers.

    > [!NOTE]
    > Viene chiamato questo comportamento di ridenominazione *pluralizzazione*. E può essere attivato o disattivare [finestra di dialogo Opzioni](../ide/reference/options-dialog-box-visual-studio.md). Per altre informazioni, vedere [procedura: attivare e disattivare (O/R Designer) la pluralizzazione](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3.  Nel **compilare** menu, fare clic su **Compila UpdatingwithSProcsWalkthrough** per compilare il progetto.

4.  Scegliere **Mostra origini dati** dal menu **Dati**.

5.  Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

6.  Fare clic su **oggetto** nel **scegliere un tipo di origine dati** e quindi fare clic su **Avanti**.

7.  Espandere la **UpdatingwithSProcsWalkthrough** nodo individuare e selezionare il **cliente** classe.

    > [!NOTE]
    > Se il **cliente** classe non è disponibile, annullare la procedura guidata, compilare il progetto e rieseguire la procedura guidata.
8.  Fare clic su **Finish** per creare l'origine dati e aggiungere il **cliente** classe di entità per il **Zdroje dat** finestra.

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Creare un controllo DataGridView per visualizzare i dati del cliente in un Windows Form

Creare controlli associati alle classi di entità trascinando gli elementi di origine dati SQL da LINQ il **Zdroje dat** finestra in un Windows Form.

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Per aggiungere controlli associati alle classi di entità

1.  Aprire **Form1** nella visualizzazione progettazione.

2.  Dal **Zdroje dat** finestra, trascinare il **Customer** nodo nello **Form1**.

    > [!NOTE]
    > Per visualizzare il **Zdroje dat** finestra, fare clic su **Mostra origini dati** sul **dati** menu.

3.  Aprire **Form1** nell'Editor del codice.

4.  Aggiungere il codice seguente al form, all'intero form, all'esterno di un metodo specifico, ma all'interno di `Form1` classe:

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

## <a name="implement-save-functionality"></a>Implementare la funzionalità di salvataggio

Per impostazione predefinita, il pulsante Salva non è abilitato e la funzionalità di salvataggio non è implementata. Inoltre, quando vengono creati controlli associati a dati per le origini dati di un oggetto, non viene aggiunto codice automaticamente per salvare i dati modificati nel database. Questa sezione viene illustrato come abilitare il salvataggio sul pulsante e implementare la funzionalità di salvataggio per LINQ agli oggetti SQL.

### <a name="to-implement-save-functionality"></a>Per implementare la funzionalità di salvataggio

1.  Aprire **Form1** nella visualizzazione progettazione.

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

## <a name="override-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Eseguire l'override del comportamento predefinito per l'esecuzione di aggiornamenti (gli inserimenti, aggiornamenti ed eliminazioni)

### <a name="to-override-the-default-update-behavior"></a>Per eseguire l'override del comportamento di aggiornamento predefinito

1.  Aprire il file LINQ to SQL nel **O/R Designer**. (Fare doppio clic il **Northwind. dbml** del file in **Esplora soluzioni**.)

2.  Nelle **Esplora Server** oppure **Esplora Database**, espandere i database Northwind **Stored procedure** nodo e individuare il **InsertCustomers**, **UpdateCustomers**, e **DeleteCustomers** stored procedure.

3.  Trascinare tutte le tre stored procedure nel **O/R Designer**.

     Le stored procedure vengono aggiunte al riquadro dei metodi come metodi <xref:System.Data.Linq.DataContext>. Per altre informazioni, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4.  Selezionare il **cliente** classe di entità la **O/R Designer**.

5.  Nel **delle proprietà** finestra, seleziona il **Inserisci** proprietà.

6.  Fare clic sui puntini di sospensione (**...** ) accanto a **Usa fase di esecuzione** per aprire la **Configura comportamento** nella finestra di dialogo.

7.  Selezionare **personalizzare**.

8.  Selezionare il **InsertCustomers** metodo le **Personalizza** elenco.

9. Fare clic su **applica** per salvare la configurazione per la classe e al comportamento selezionati.

    > [!NOTE]
    > È possibile continuare a configurare il comportamento per ogni combinazione classe/comportamento purché faccia clic su **applica** dopo ogni modifica apportata. Se si modifica la classe o un comportamento prima di fare clic **applica**, offrendo la possibilità di applicare le modifiche viene visualizzata una finestra di dialogo avviso.

10. Selezionare **Update** nel **comportamento** elenco.

11. Selezionare **personalizzare**.

12. Selezionare il **UpdateCustomers** metodo le **Personalizza** elenco.

     Esaminare l'elenco delle **gli argomenti del metodo** e **proprietà della classe** e notare che sono presenti due **gli argomenti del metodo** e due **proprietà della classe**per alcune colonne della tabella. In tal modo, vengono facilitati il rilevamento delle modifiche e la creazione di istruzioni che verifichino la presenza di eventuali violazioni di concorrenza.

13. Mappa il **Original_CustomerID** argomento del metodo per il **CustomerID (Original)** proprietà della classe.

    > [!NOTE]
    > Per impostazione predefinita, verrà eseguito il mapping degli argomenti di metodo alle proprietà di classe quando i nomi corrispondono. Se i nomi delle proprietà vengono modificati e non è più corrispondenza tra la tabella e la classe di entità, è necessario selezionare la proprietà di classe equivalente a eseguire il mapping se il **O/R Designer** non è possibile determinare il mapping corretto. Inoltre, se gli argomenti del metodo non si dispone delle proprietà di classe valido per eseguire il mapping, è possibile impostare il **proprietà della classe** valore **(nessuno)**.

14. Fare clic su **applica** per salvare la configurazione per la classe e al comportamento selezionati.

15. Selezionare **eliminare** nel **comportamento** elenco.

16. Selezionare **personalizzare**.

17. Selezionare il **DeleteCustomers** metodo le **Personalizza** elenco.

18. Mappa il **Original_CustomerID** argomento del metodo per il **CustomerID (Original)** proprietà della classe.

19. Fare clic su **OK**.

> [!NOTE]
> Sebbene non sia un problema per questa procedura dettagliata, vale la pena notare che LINQ to SQL gestisce i valori generati dal database automaticamente per identity (incremento automatico), rowguidcol (GUID generato dal database) e le colonne timestamp durante gli inserimenti e aggiornamenti. I valori degli altri tipi di colonne sono costituiti da valori null non previsti. Per restituire i valori generati dal database, è necessario impostare manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> al `true` e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> a una delle operazioni seguenti: [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>), o [AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="test-the-application"></a>Testare l'applicazione

Eseguire nuovamente l'applicazione per verificare che il **UpdateCustomers** stored procedure aggiorna correttamente il record del cliente nel database.

1.  Premere **F5**.

2.  Modificare un record nella griglia per testare il comportamento di aggiornamento.

3.  Aggiungere un nuovo record per testare il comportamento di inserimento.

4.  Fare clic sul pulsante Salva per salvare le modifiche nel database.

5.  Chiudere il form.

6.  Premere **F5** e verificare che il record aggiornato e il record appena inserito persistente.

7.  Eliminare il nuovo record creato nel passaggio 3 per testare il comportamento di eliminazione.

8.  Fare clic su Salva per inviare le modifiche e rimuovere il record eliminato dal database.

9. Chiudere il form.

10. Premere **F5** e verificare che il record eliminato sia stato rimosso dal database.

    > [!NOTE]
    > Se l'applicazione Usa SQL Server Express Edition, in base al valore di **copia in Directory di Output** proprietà del file di database, le modifiche potrebbero non comparire quando si preme **F5** nel passaggio 10.

## <a name="next-steps"></a>Passaggi successivi

A seconda dei requisiti dell'applicazione, esistono diverse operazioni che è possibile eseguire dopo aver creato LINQ alle classi di entità SQL. È possibile apportare alcuni miglioramenti a questa applicazione, tra cui:

- Implementazione del controllo della concorrenza durante gli aggiornamenti. Per informazioni, vedere [la concorrenza ottimistica: Panoramica](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).

- Aggiunta di query LINQ per filtrare i dati. Per informazioni, vedere [Introduzione alle query LINQ (c#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metodi DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura: assegnare stored procedure per eseguire gli aggiornamenti, inserimenti ed eliminazioni](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Query LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)